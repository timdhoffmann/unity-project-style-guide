# Unity Project Style Guide
A style guide for keeping your Unity projects tidy and organized. Compiled from several best practices resources (see the resources section at the end of the document).

## Files, Folders and Project Structure

### Naming 

#### General Principles

- *Never use Spaces* in names.
- Use **PascalCase** for *custom file- and folder names*, like this: *ComplicatedVerySpecificObject*. Do not use spaces, underscores, or hyphens, with one exception (see Naming Different Aspects of the Same Thing).
- Keep the **most specific** descriptor on the **left**: *DarkVampire*, not *VampireDark*; *PauseButton*, not *ButtonPaused*. 
- Some names form a **sequence**. Use *numbers in these names*, for example, *PathNode0*, *PathNode1*. Always start with *0*, not *1*.
- Do *not use numbers* for things that *don’t form a sequence*. For example, Bird0, Bird1,Bird2 should be Flamingo, Eagle, Swallow.
- Prefix temporary objects with a double underscore __Player_Backup.

#### Naming Different Aspects of the Same Thing

Use *underscores* between the *core name*, and the thing that describes the *“aspect”*. For instance:
- GUI buttons states *EnterButton_Active*, *EnterButton_Inactive*
- Textures *DarkVampire_Diffuse*, *DarkVampire_Normalmap*
- Skybox *JungleSky_Top*, *JungleSky_North*
- LOD Groups *DarkVampire_LOD0*, *DarkVampire_LOD1*

Do *not use* this convention just to *distinguish* between *different types* of items, for instance Rock_Small, Rock_Large should be SmallRock, LargeRock.


### Structure

#### General Principles

- **Prefab everything**.
    - To modify an asset from the store, drag it into the hierarchy and create a prefab inside _Project.
- **Use the Project tab's *search* functionality**:
  - *Search by Type* in the *upper right*.
  - *Restrict results to selected folder only* (recursively): Click on *Search* and selecting the desired folder from the drop-down (operation mode will be remembered). 
- **Save searches as *context sensitive filters*** (two colum layout): 
  - Click on the *star* in the top right to save a search. The *filter will apply to any selected folder*, for example: 
     - *Only scripts in selected* (and sub-folders)
     - *Only prefabs in selected* (and sub-folders)
     - *Only animations in selected* (and sub-folders)
- *Pin* folders by dragging them to *Favorites*.
- *Don’t* disassemble *context-specific assets*. For instance, leave the folder structure of downloaded assets intact.
- **Use Tags to mark imported 3rdParty assets:**
  - Select an item in the project browser and assign a tag in the bottom right of the inspector.
    - For entire packs, mark the top folder of the asset pack.
    - Assets that come as individual files can be marked directly.

#### Project directory structure (strictly functionality/entity-based):

```
Assets
    __NoVersionControl      // Container for temporary stuff, not under version control. More clear???
    _Project                // All custom files.               
        Characters
            Enemy           // Can have sub-folders or not (see "Save searches as context sensitive filters).       
            Player
            ...
        Environment
            Trees
            ...
        Props
            Weapons
            ...
        Managers
        Scenes
        TestScripts
        UI
        Vehicles
    Plugins                 // Reserved folder.
    Standard Assets         // Reserved folder for Unity standard assets.
```

#### Scene hierarchy structure

Prefab everything!

```
Main
Debug
Managers 
Cameras
Lights
UI
   Canvas
      HUD
      PauseMenu
      ...
World
   Terrain
   Props
   Structures
   ...
Gameplay
   Actors
   Items
   ...
_DynamicObjects     // Parent for all objects instantiated at runtime.
```


## Coding Standard (C#)

- Use camelCase for fields and variables. 

  Example: 
  ```CSharp
  private RigidBody rigidBody;

  private int length; 
  ```

---

References: 
- https://www.gamasutra.com/blogs/HermanTulleken/20160812/279100/50_Tips_and_Best_Practices_for_Unity_2016_Edition.php

- http://developers.nravo.com/mastering-unity-project-folder-structure-level-2-assets-organization/

- https://docs.microsoft.com/en-us/dotnet/standard/design-guidelines/naming-guidelines

- https://docs.microsoft.com/en-us/dotnet/csharp/tour-of-csharp/
