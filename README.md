JPetMC 
=============================================================================

# Software information
JPetMC is a simulation program written in a GEANT4 environment.
Details of the J-PET detector can be found on the project webpage [webpage](http://koza.if.uj.edu.pl/pet/).
Its main features:
- the J-PET detector geometry is loaded from the (CAD) technical drawings,
- user can load detector setups (identified by run numbers), which corresponds to 
one used in the experiment. Details can be found in section [How to run](#how-to-run),
- the mcGeant.root is created as an output file. It can be processed by the J-PET Framework
software

## Source code:
https://github.com/daria137/jpetmc.git

## Required packages:
- geant4.10.04
- root 6.0 
- cadmesh (https://github.com/christopherpoole/CADMesh)
- cmake 
- doxygen

## How to compile? 
mkdir build
cd build
cmake ..
make
- output file: (in build folder) bin/jpet_mc

## How to create documentation?
(in build folder) 
cmake .. && make doc
- open the doc/html/index.html in your favourite web browser 


# How to run 
The executable program is located in build/bin/jpet_mc. 
Simple execution of the program (./jpet_mc) should load the init_vis.mac script and show detector geometry.

User can adjust detector parameters and generated gamma-quanta by using macros. Exemplary  macro is given in bin folder along the executive file.

## Geometry
User can load one of the selected geometries:
 - /jpetmc/detector/loadGeomForRun runNr
   - runNr=3
    - only implemented since now 
    - loaded JPetBasicGeom
    - place inside of the detector the large annihilation chamber without porous material inside 
 - /jpetmc/detector/loadJPetBasicGeom 
   - 3 layers of scintillators (48,48,96)
   - each scintillator: 1.9x0.7x50 cm^3 wrapped in kapton foil
   - detector frame: loaded from CAD file
   - standard setup for runs 1-6
 - /jpetmc/detector/loadIdealGeom 
   - not implemented yet
   - should load n-layer fully packed with scintillators barrel
 - /jpetmc/detector/loadJPetExtendedGeom 
   - not implemented yet
   - should load JPET standard geometry with additional read-out modules
 - /jpetmc/detector/loadOnlyScintillators 
   - shows only scintillator wrapped in a kapton foil   

## Targets
If user calls run geometry for dedicated run, then target is predefined and it can not be changed. 


- materials can keep information about oPs creation and lifetime

