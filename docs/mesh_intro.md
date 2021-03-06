Brigge for Meshes lets you bring 3D mesh models from Blender directly into UE4. This approach keeps all the quality and nuance of your work while bypassing the usual complications and trial & error.

For now we'll use a file import/export workflow, similar to how you'd work with FBX, OBJ, or glTF files.

You will need:
* Blender 2.80 or later
* Unreal Engine 4.22 or later
* Brigge for Meshes

See the [install docs](install.md) to get things set up.

## Export mesh objects from Blender

1. Launch Blender and open your project's `.blend` file
2. Select which mesh objects you want to export
3. From the menu bar, choose File > Export > Brigge for Meshes
4. Choose where on disk to put the files
	> Brigge for Meshes creates one `.brigge` file, which you can name anything.
	> It also creates one `.mesh` file per mesh object. These are named based on the corresponding object names in Blender.
	> Be careful! If files with the same name already exist, Brigge export will overwrite them with the latest data.
5. Adjust export options
	> Default settings should work fine.
	>
	> ![](media/mesh_options_export.png)
	>
	> (read [this doc](mesh_options.md) for full details)
6. Export!

You now have these mesh assets on disk, separate from their source `.blend` file. The `.brigge` file describes the assets and has a link back to the `.blend` file. You can open this with any text editor and see how it works. The `.mesh` files are binary, and have all the information needed by Brigge's Unreal plugin.

## Import into Unreal Engine

1. Launch Unreal Engine and open your project
2. In the Content Browser, navigate to the folder you want the mesh assets to be in
3. Click the Import button and locate the `.brigge` file you exported from Blender
4. Import!

Each mesh in the `.brigge` file will create its own StaticMesh asset in your Unreal project, and spawn Actors into your level.


### Notes

_Brigge is designed for rapid iteration. You can make changes in the `.blend` file, export to `.brigge`, and reimport the StaticMesh at any time._

_Brigge for Meshes sets up Material slots in Unreal to match those in Blender. It looks for existing Unreal Material assets in your project and will assign them to the StaticMesh if their names match. Missing materials or empty material slots are perfectly ok! These will use the default world grid material and you can assign them once you're ready to think about materials. Brigge will never create "dummy" materials or disrupt your slot order._
