---
title: "Very big flames in Torchlight"
date: 2009-12-01
forum: Wine
---

### Post by purity89 on 2009-12-01
I think I've tried almost everything I've found about running this game with Wine, but I still can't get rid of one big problem: The flames are way too large, because of some graphical error.

I've got fullscreen, all resolutions and OpenGL working, but I don't want this thread to be about that. To do this I just followed lgtspecb's instructions in [this](http://forum.winehq.org/viewtopic.php?t=6581) thread.

I've tried:
 - Direct3D9/OpenGL
 - Disabling "HWSKINNING"
 - Setting "MAX_PARTICLES" to 500
 - Fullscreen/windowed

Have anyone had any luck getting rid of the very annoying flame "effect"? Check the attachment to see what it looks like.

---

### Post by Azuu on 2009-12-01
Setting max particles to 0?

---

### Post by purity89 on 2009-12-02
> **Azuu said:**
> Setting max particles to 0?

That just gave me Runtime errors. But when I set it to 50 it looked like it made some difference, because the big fire around my characters weapons disappeared on the title screen. But when I loaded the game the flame in the town center was still too big.

But now I tried setting it to 10, and the flames appeared in the title screen again, but they are displayed correctly in the town centre. I'll run around in the dungeon and see what it looks like there.

EDIT: After getting into the dungeon the flames around my weapons appeared again. Check the screenshots...

EDIT2: Hmm, after fishing in a fishing pond the flames suddenly disappeared around my weapons. Guess there's something strange going on because of my settings (particles :10).

---

### Post by Azuu on 2009-12-02
> **purity89 said:**
> That just gave me Runtime errors. But when I set it to 50 it looked like it made some difference, because the big fire around my characters weapons disappeared on the title screen. But when I loaded the game the flame in the town center was still too big.

But now I tried setting it to 10, and the flames appeared in the title screen again, but they are displayed correctly in the town centre. I'll run around in the dungeon and see what it looks like there.

EDIT: After getting into the dungeon the flames around my weapons appeared again. Check the screenshots...

EDIT2: Hmm, after fishing in a fishing pond the flames suddenly disappeared around my weapons. Guess there's something strange going on because of my settings (particles :10).

alrighty, recreate the circumstances after starting the game with terminal. then post it here. The repeated errors are likely the issue as far as particles go.

---

### Post by purity89 on 2009-12-04
These were the only errors I could find when running the game through terminal:

```
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
```

```
err:ole:CoGetClassObject class {bcde0395-e52f-467c-8e3d-c4579291692e} not registered
err:ole:CoGetClassObject class {bcde0395-e52f-467c-8e3d-c4579291692e} not registered
err:ole:create_server class {bcde0395-e52f-467c-8e3d-c4579291692e} not registered
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x7
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x17df10,0x17de98): stub
```

Here's the everything that happened if you need it:

```
purity@purity-laptop:~$ wine "D:\Torchlight\Torchlight.exe" 
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
Creating resource group General
Creating resource group Internal
Creating resource group Autodetect
SceneManagerFactory for type 'DefaultSceneManager' registered.
Registering ResourceManager for type Material
Registering ResourceManager for type Mesh
Registering ResourceManager for type Skeleton
MovableObjectFactory for type 'ParticleSystem' registered.
OverlayElementFactory for type Panel registered.
OverlayElementFactory for type BorderPanel registered.
OverlayElementFactory for type TextArea registered.
Registering ResourceManager for type Font
ArchiveFactory for archive type FileSystem registered.
ArchiveFactory for archive type Zip registered.
FreeImage version: 3.10.0
This program uses FreeImage, a free, open source image library supporting all common bitmap formats. See http://freeimage.sourceforge.net for details
Supported formats: bmp,ico,jpg,jif,jpeg,jpe,jng,koa,iff,lbm,mng,pbm,pbm,pcd,pcx,pgm,pgm,png,ppm,ppm,ras,tga,targa,tif,tiff,wap,wbmp,wbm,psd,cut,xbm,xpm,gif,hdr,g3,sgi,exr,j2k,j2c,jp2
DDS codec registering
Registering ResourceManager for type HighLevelGpuProgram
Registering ResourceManager for type Compositor
MovableObjectFactory for type 'Entity' registered.
MovableObjectFactory for type 'Light' registered.
MovableObjectFactory for type 'BillboardSet' registered.
MovableObjectFactory for type 'ManualObject' registered.
MovableObjectFactory for type 'BillboardChain' registered.
MovableObjectFactory for type 'RibbonTrail' registered.
Loading library .\RenderSystem_GL
Installing plugin: GL RenderSystem
OpenGL Rendering Subsystem created.
Plugin successfully installed
Loading library .\Plugin_ParticleFX
Installing plugin: ParticleFX
Particle Emitter Type 'Point' registered
Particle Emitter Type 'Box' registered
Particle Emitter Type 'Ellipsoid' registered
Particle Emitter Type 'Cylinder' registered
Particle Emitter Type 'Ring' registered
Particle Emitter Type 'HollowEllipsoid' registered
Particle Affector Type 'LinearForce' registered
Particle Affector Type 'ColourFader' registered
Particle Affector Type 'ColourFader2' registered
Particle Affector Type 'ColourImage' registered
Particle Affector Type 'ColourInterpolator' registered
Particle Affector Type 'Scaler' registered
Particle Affector Type 'Rotator' registered
Particle Affector Type 'DirectionRandomiser' registered
Particle Affector Type 'DeflectorPlane' registered
Plugin successfully installed
Loading library .\Plugin_CgProgramManager
Installing plugin: Cg Program Manager
Plugin successfully installed
Loading library .\Plugin_OctreeSceneManager
Installing plugin: Octree & Terrain Scene Manager
Plugin successfully installed
Loading library .\ParticleUniverse
Installing plugin: ParticleUniverse
MovableObjectFactory for type 'PUParticleSystem' registered.
MovableObjectFactory for type 'BoxSet' registered.
MovableObjectFactory for type 'SphereSet' registered.
ParticleUniverse: Particle Renderer Type 'Billboard' registered
ParticleUniverse: Particle Renderer Type 'Box' registered
ParticleUniverse: Particle Renderer Type 'Sphere' registered
ParticleUniverse: Particle Renderer Type 'Entity' registered
ParticleUniverse: Particle Renderer Type 'RibbonTrail' registered
ParticleUniverse: Particle Renderer Type 'Light' registered
ParticleUniverse: Particle Emitter Type 'Point' registered
ParticleUniverse: Particle Emitter Type 'Line' registered
ParticleUniverse: Particle Emitter Type 'Box' registered
ParticleUniverse: Particle Emitter Type 'Circle' registered
ParticleUniverse: Particle Emitter Type 'SphereSurface' registered
ParticleUniverse: Particle Emitter Type 'Vertex' registered
ParticleUniverse: Particle Emitter Type 'MeshSurface' registered
ParticleUniverse: Particle Emitter Type 'Position' registered
ParticleUniverse: Particle Emitter Type 'Slave' registered
ParticleUniverse: Particle Affector Type 'Dummy01' registered
ParticleUniverse: Particle Affector Type 'LinearForce' registered
ParticleUniverse: Particle Affector Type 'Gravity' registered
ParticleUniverse: Particle Affector Type 'ParticleFollower' registered
ParticleUniverse: Particle Affector Type 'Vortex' registered
ParticleUniverse: Particle Affector Type 'Randomiser' registered
ParticleUniverse: Particle Affector Type 'Line' registered
ParticleUniverse: Particle Affector Type 'Scale' registered
ParticleUniverse: Particle Affector Type 'GeometryRotator' registered
ParticleUniverse: Particle Affector Type 'TextureRotator' registered
ParticleUniverse: Particle Affector Type 'TextureAnimator' registered
ParticleUniverse: Particle Affector Type 'Jet' registered
ParticleUniverse: Particle Affector Type 'Align' registered
ParticleUniverse: Particle Affector Type 'FlockCentering' registered
ParticleUniverse: Particle Affector Type 'CollisionAvoidance' registered
ParticleUniverse: Particle Affector Type 'VelocityMatching' registered
ParticleUniverse: Particle Affector Type 'Colour' registered
ParticleUniverse: Particle Affector Type 'SineForce' registered
ParticleUniverse: Particle Affector Type 'Dummy02' registered
ParticleUniverse: Particle Affector Type 'SphereCollider' registered
ParticleUniverse: Particle Affector Type 'PlaneCollider' registered
ParticleUniverse: Particle Affector Type 'BoxCollider' registered
ParticleUniverse: Particle Affector Type 'InterParticleCollider' registered
ParticleUniverse: Particle Affector Type 'PathFollower' registered
ParticleUniverse: Particle Observer Type 'OnExpire' registered
ParticleUniverse: Particle Observer Type 'OnEmission' registered
ParticleUniverse: Particle Observer Type 'OnCount' registered
ParticleUniverse: Particle Observer Type 'OnEventFlag' registered
ParticleUniverse: Particle Observer Type 'OnCollision' registered
ParticleUniverse: Particle Observer Type 'OnVelocity' registered
ParticleUniverse: Particle Observer Type 'OnTime' registered
ParticleUniverse: Particle Observer Type 'OnPosition' registered
ParticleUniverse: Particle Observer Type 'OnClear' registered
ParticleUniverse: Particle Observer Type 'OnQuota' registered
ParticleUniverse: Particle Observer Type 'OnRandom' registered
ParticleUniverse: Particle EventHandler Type 'DoExpire' registered
ParticleUniverse: Particle EventHandler Type 'DoFreeze' registered
ParticleUniverse: Particle EventHandler Type 'DoPlacementParticle' registered
ParticleUniverse: Particle EventHandler Type 'DoStopSystem' registered
ParticleUniverse: Particle EventHandler Type 'DoEnableComponent' registered
ParticleUniverse: Particle EventHandler Type 'DoAffector' registered
ParticleUniverse: Particle EventHandler Type 'DoScale' registered
ParticleUniverse: Particle Extern Type 'Gravity' registered
ParticleUniverse: Particle Extern Type 'SphereCollider' registered
ParticleUniverse: Particle Extern Type 'BoxCollider' registered
ParticleUniverse: Particle Extern Type 'Vortex' registered
ParticleUniverse: Particle Behaviour Type 'Slave' registered
Plugin successfully installed
*-*-* OGRE Initialising
*-*-* Version 1.6.4 (Shoggoth)
err:ole:CoGetClassObject class {bcde0395-e52f-467c-8e3d-c4579291692e} not registered
err:ole:CoGetClassObject class {bcde0395-e52f-467c-8e3d-c4579291692e} not registered
err:ole:create_server class {bcde0395-e52f-467c-8e3d-c4579291692e} not registered
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x7
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x17dea0,0x17de28): stub
```

---

### Post by ukyo_rulz on 2009-12-12
I am getting the same error: huge flames. The funny thing is that when I try to set particles to 10, the flames are fixed only for wherever I am when I resume my game. So if I am in town the town flame will be fixed but the torches in the dungeon are huge. If I am in the dungeon the torches will be fixed but the town flame will be huge. Sometimes the problem will disappear but I dunno how to replicate it. Also fullscreen sometimes works and sometimes does not.

---

