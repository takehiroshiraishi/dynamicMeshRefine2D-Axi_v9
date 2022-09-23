# dynamicMeshRefine2D+Axi_v9
2D and Axisymmetric Dynamic Mesh Refinement Libraries.  
Allows dynamic meshing in 2D planar and axisymmetric geometries.  
Based on the OpenFOAM 3D dynamic meshing.

Author:        Takehiro Shiraishi (Original code: Ahmad Baniabedalruhman)  
Version:       Adapted to OpenFOAM v9

## Installation/Compiling
   Copy the entire directory to:  $WM_PROJECT_USER_DIR/src/.  
   Then compile as follows.
   ```
   $ cd $WM_PROJECT_USER_DIR/src/dynamicMeshRefine_2D+Axi_v9/dynamicMesh
   $ wclean
   $ wmake libso
   $ cd $WM_PROJECT_USER_DIR/src/dynamicMeshRefine_2D+Axi_v9/dynamicFvMesh
   $ wclean
   $ wmake libso
   ```

## Running the Tutorial:   2d-dropInShearFlowCa0.3

1) Changes to <caseDir>/constant/dynamicMeshDict:
   a) 2D planar geometry:  
   
      dynamicRefineFvMesh       ---> dynamicRefineFvMesh2D   
      dynamicRefineFvMeshCoeffs ---> dynamicRefineFvMesh2DCoeffs  
      Parameter values:
      
        "axis" = 0: x-axis is normal to "empty" faces and min(x)<"axisVal"<max(x)
        "axis" = 1: y-axis is normal to "empty" faces and min(y)<"axisVal"<max(y)
        "axis" = 2: z-axis is normal to "empty" faces and min(z)<"axisVal"<max(z)

   b) Axisymmetric geometry:
   
      dynamicRefineFvMesh       ---> dynamicRefineFvMeshAxi  
      dynamicRefineFvMeshCoeffs ---> dynamicRefineFvMeshAxiCoeffs  
      Parameter values: 
   
        "axis" = 0: x-axis is normal to "wedge" faces and "axisVal" = centerLine x-value
        "axis" = 1: y-axis is normal to "wedge" faces and "axisVal" = centerLine y-value
        "axis" = 2: z-axis is normal to "wedge" faces and "axisVal" = centerLine z-value


2) Run the case:
   a) run "blockMesh"
   b) run "setFields"
   c) run "interFoam"

