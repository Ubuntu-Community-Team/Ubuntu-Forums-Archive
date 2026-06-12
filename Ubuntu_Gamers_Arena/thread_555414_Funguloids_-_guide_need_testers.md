---
title: "Funguloids - guide need testers"
date: 2007-09-20
forum: Ubuntu Gamers Arena
---

### Post by Perfect Storm on 2007-09-20
At last I've been able to compile that game :guitar:

about: funguloids; [http://funguloids.sourceforge.net/screenshots.html](http://funguloids.sourceforge.net/screenshots.html)


If anyone dare;


sudo aptitude update && sudo aptitude upgrade
sudo aptitude install build-essential checkinstall automake libtool
sudo aptitude install zlib1g-dev libgtk2.0-dev libdevil-dev libcegui-mk2-dev libfreetype6-dev libtiff4-dev libgl1-mesa-dev bison flex libzzip-dev libxt-dev libxaw7-dev libxxf86vm-dev libxrandr-dev xlibs-dev libopenexr-dev liblua5.1-0-dev libopenal-dev libalut-dev libvorbis-dev libmad0-dev


CG Toolkit
----------

cd ~/Desktop
wget [http://developer.download.nvidia.com/cg/Cg_1.5/1.5.0/0022/Cg-1.5_Aug2007_x86.tar.gz](http://developer.download.nvidia.com/cg/Cg_1.5/1.5.0/0022/Cg-1.5_Aug2007_x86.tar.gz)
tar zxfv Cg-1.5_Aug2007_x86.tar.gz
cd usr
sudo cp -r * /usr


Object Oriented Input System
----------
cd ~/Desktop
wget [http://downloads.sourceforge.net/wgois/ois-1.0.tar.gz?modtime=1182593947&big_mirror=0](http://downloads.sourceforge.net/wgois/ois-1.0.tar.gz?modtime=1182593947&big_mirror=0)
tar zxfv ois-1.0.tar.gz
cd ois
./bootstrap
./configure --prefix=/usr
make
sudo make install


OGRE
----------
cd ~/Desktop
wget [http://downloads.sourceforge.net/ogre/ogre-linux_osx-v1-4-4.tar.bz2](http://downloads.sourceforge.net/ogre/ogre-linux_osx-v1-4-4.tar.bz2)
tar jxfv ogre-linux_osx-v1-4-4.tar.bz2
cd ogrenew
./configure --prefix=/usr --disable-freeimage --enable-openexr
make
sudo make install


fungul
-------------
cd ~/Desktop
wget [http://downloads.sourceforge.net/funguloids/funguloids-linux-1.06-4.tar.bz2?download](http://downloads.sourceforge.net/funguloids/funguloids-linux-1.06-4.tar.bz2?download)
tar jxfv funguloids-linux-1.06-4.tar.bz2
cd funguloids
./configure
make
sudo make install
cd bin
sudo mv funguloids /usr/local/bin



launching;
**funguloids**


By the way what's the latest OGRE in Gutsy? Funguloids needs atleast version 1.4 and in Feisty it's 1.2.5

---

### Post by hikaricore on 2007-09-20
I'll try it out when I get home.

Also I'll check the OGRE version on the system my girl and I have named "fluffy".  ^_^
As it is running gutsy.

---

### Post by cogadh on 2007-09-20
"fluffy" #-o 

Geez, and I thought it was bad when I named one of my systems "optimus_prime" (looong before the movie).

I'll also give this a shot later. It should be a great test of my hopefully working (again) 'buntu box.

---

### Post by cogadh on 2007-09-20
Hmmm, I seem to be having a problem with the OGRE compile. It finishes with this:
```
/usr/bin/ld: cannot find -lmng
collect2: ld returned 1 exit status
make[2]: *** [libOgreMain.la] Error 1
make[2]: Leaving directory `/home/cogadh/Desktop/ogrenew/OgreMain/src'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/cogadh/Desktop/ogrenew/OgreMain'
make: *** [install-recursive] Error 1

```
Then when I try to run the fungul ./configure I get this:
```
checking for OGRE... configure: error: Package requirements (OGRE >= 1.4) were not met:

No package 'OGRE' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables OGRE_CFLAGS
and OGRE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```
I'll keep working on it, but I can't see what I might have done wrong.

EDIT - Okay, I'm certain the problem has something to do with the "/usr/bin/ld: cannot find -lmng" error (everything seems to trace back to that). Any ideas what "lmng" is?

---

### Post by Perfect Storm on 2007-09-20
can I get more of the make of Ogre and the configure output also.

---

### Post by cogadh on 2007-09-21
Here you go, complete output from both the configure and make.

---

### Post by compiledkernel on 2007-09-21
Hrmmm. Ill try it. 

to Cogadh: I name all my systems after dragons, so dont feel bad.

---

### Post by Perfect Storm on 2007-09-21
I was wondering if you had any other compiling tools other than gcc4.1 installed, cogadh. If so try uninstall those (except those you applications are depended on ofcause).

---

### Post by Perfect Storm on 2007-09-21
download again, so far the configure is the exact same as yours.

Another option I read;

```
sudo ldconfig
```
first

then;

```
make clean
```

then try again;

---

### Post by cogadh on 2007-09-21
Nope, I only have gcc and whatever else might be installed with the build-essentials package (g++, g++-4.1).

EDIT - Man I'm typing slow today. I produced that output with a brand new download, but I'll give it another shot.

---

### Post by Perfect Storm on 2007-09-21
I just edit my post above, try see if it helps.

---

### Post by Vadi on 2007-09-21
The forums cut down on the size of the wget commands, and they don't work... you have to manually right click, copy link location. Can this be fixed somehow? Maybe put code tags around it?

---

### Post by cogadh on 2007-09-21
> **Artificial Intelligence said:**
> I just edit my post above, try see if it helps.

No go, still produced the same problem. Any other ideas?

---

### Post by Vadi on 2007-09-21
Well, I didn't get a recursive error, but my orgre installation is looping too. It's just going in circles executing the huge command over and over.

Here's the output: [http://pastebin.ca/706079](http://pastebin.ca/706079)

---

### Post by Vadi on 2007-09-21
Oops, I saw it was making different things... So I guess it wasn't looping after all. I'll try it again then.

---

### Post by Perfect Storm on 2007-09-21
Strange...wonder what's diffrent from our systems.


I just hope, Ogre 1.4.4 will be available in Gutsy, then the guide will be cut down considerable.

If people a burning for using this game I guess they can use this; [http://www.ogre3d.org/wiki/index.php/Building_From_Source#Using_the_source_package](http://www.ogre3d.org/wiki/index.php/Building_From_Source#Using_the_source_package)

but I really hoped for an "clean" ubuntu version.

---

### Post by Vadi on 2007-09-21
I used the clean command, and am right right on the "make" command of the ogre. It's at uhh... OgreParticleSystem right now.

---

### Post by Perfect Storm on 2007-09-21
Some more helps: [http://www.ogre3d.org/wiki/index.php/Building_From_Source#GCC_.26_Make](http://www.ogre3d.org/wiki/index.php/Building_From_Source#GCC_.26_Make)

When I think of it I have freeimage installed, but I disabled it via /configure to use libdevil instead. It shouldn't make a diffrence....

---

### Post by Vadi on 2007-09-21
No go, it needed with this:

```
        then mv -f ".deps/libSSEsupport_la-OgreOptimisedUtilSSE.Tpo" ".deps/libSSEsupport_la-OgreOptimisedUtilSSE.Plo"; else rm -f ".deps/libSSEsupport_la-OgreOptimisedUtilSSE.Tpo"; exit 1; fi
 g++ -DHAVE_CONFIG_H -I. -I. -I../../OgreMain/include -I/usr/include/freetype2 -I../../OgreMain/include -DOGRE_NONCLIENT_BUILD -DOGRE_GUI_gtk -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -fvisibility=hidden -fvisibility-inlines-hidden -DOGRE_GCC_VISIBILITY -msse -g -O2 -MT libSSEsupport_la-OgreOptimisedUtilSSE.lo -MD -MP -MF .deps/libSSEsupport_la-OgreOptimisedUtilSSE.Tpo -c OgreOptimisedUtilSSE.cpp  -fPIC -DPIC -o .libs/libSSEsupport_la-OgreOptimisedUtilSSE.o
OgreSIMDHelper.h:107: warning: specifying vector types with __attribute__ ((mode)) is deprecated
OgreSIMDHelper.h:107: warning: use __attribute__ ((vector_size)) instead
OgreSIMDHelper.h:108: warning: specifying vector types with __attribute__ ((mode)) is deprecated
OgreSIMDHelper.h:108: warning: use __attribute__ ((vector_size)) instead
/bin/bash ../../libtool --tag=CXX --mode=link g++  -g -O2   -o libSSEsupport.la   libSSEsupport_la-OgreOptimisedUtilSSE.lo  -lCg -lILU -lIL -lpthread -lz -lm -ldl 
ar cru .libs/libSSEsupport.a .libs/libSSEsupport_la-OgreOptimisedUtilSSE.o
ranlib .libs/libSSEsupport.a
creating libSSEsupport.la
(cd .libs && rm -f libSSEsupport.la && ln -s ../libSSEsupport.la libSSEsupport.la)
/bin/bash ../../libtool --tag=CXX --mode=link g++  -g -O2   -o libOgreMain.la -rpath /usr/lib -shared -release 1.4.4 -Wl,-rpath,/usr/lib OgreAlignedAllocator.lo OgreAnimation.lo OgreAnimable.lo OgreAnimationState.lo OgreAnimationTrack.lo OgreArchiveManager.lo OgreAutoParamDataSource.lo OgreBillboard.lo OgreBillboardChain.lo OgreBillboardParticleRenderer.lo OgreBillboardSet.lo OgreBone.lo OgreBorderPanelOverlayElement.lo OgreCamera.lo OgreCodec.lo OgreColourValue.lo OgreCommon.lo OgreConfigFile.lo OgreControllerManager.lo OgreConvexBody.lo OgreDataStream.lo OgreDDSCodec.lo OgreDefaultHardwareBufferManager.lo OgreDefaultSceneQueries.lo OgreDynLib.lo OgreDynLibManager.lo OgreEdgeListBuilder.lo OgreEntity.lo OgreException.lo OgreExternalTextureSource.lo OgreExternalTextureSourceManager.lo OgreFileSystem.lo OgreFont.lo OgreFontManager.lo OgreFrustum.lo OgreGpuProgram.lo OgreGpuProgramManager.lo OgreGpuProgramUsage.lo OgreHardwareBufferManager.lo OgreHardwareIndexBuffer.lo OgreHardwareOcclusionQuery.lo OgreHardwareVertexBuffer.lo OgreHardwarePixelBuffer.lo OgreHighLevelGpuProgram.lo OgreHighLevelGpuProgramManager.lo OgreImage.lo OgreInstancedGeometry.lo OgreKeyFrame.lo OgreLight.lo OgreLog.lo OgreLogManager.lo OgreManualObject.lo OgreMaterial.lo OgreMaterialManager.lo OgreMaterialSerializer.lo OgreMaterialScriptCompiler.lo OgreMath.lo OgreMatrix3.lo OgreMatrix4.lo OgreMemoryManager.lo OgreMesh.lo OgreMeshManager.lo OgreMeshSerializer.lo OgreMeshSerializerImpl.lo OgreMovableObject.lo OgreMovablePlane.lo OgreNode.lo OgreNumerics.lo OgreOptimisedUtil.lo OgreOptimisedUtilGeneral.lo OgreOverlay.lo OgreOverlayContainer.lo OgreOverlayElement.lo OgreOverlayElementCommands.lo OgreOverlayManager.lo OgrePixelFormat.lo OgrePanelOverlayElement.lo OgreParticle.lo OgreParticleEmitter.lo OgreParticleEmitterCommands.lo OgreParticleIterator.lo OgreParticleSystem.lo OgreParticleSystemManager.lo OgrePass.lo OgrePatchMesh.lo OgrePatchSurface.lo OgrePlane.lo OgrePlatformInformation.lo OgrePolygon.lo OgrePose.lo OgrePredefinedControllers.lo OgrePrefabFactory.lo OgreProfiler.lo OgreProgressiveMesh.lo OgreQuaternion.lo OgreRectangle2D.lo OgreRenderQueue.lo OgreRenderQueueInvocation.lo OgreRenderQueueSortingGrouping.lo OgreRenderSystem.lo OgreRenderSystemCapabilities.lo OgreRenderTarget.lo OgreRenderTexture.lo OgreRenderWindow.lo OgreResource.lo OgreResourceBackgroundQueue.lo OgreResourceGroupManager.lo OgreResourceManager.lo OgreRibbonTrail.lo OgreRoot.lo OgreRotationSpline.lo OgreSceneManager.lo OgreSceneManagerEnumerator.lo OgreSceneNode.lo OgreSceneQuery.lo OgreSearchOps.lo OgreSerializer.lo OgreShadowCameraSetup.lo OgreShadowCameraSetupFocused.lo OgreShadowCameraSetupLiSPSM.lo OgreShadowCameraSetupPlaneOptimal.lo OgreShadowCaster.lo OgreShadowTextureManager.lo OgreShadowVolumeExtrudeProgram.lo OgreSimpleRenderable.lo OgreSimpleSpline.lo OgreSkeleton.lo OgreSkeletonInstance.lo OgreSkeletonManager.lo OgreSkeletonSerializer.lo OgreStaticGeometry.lo OgreString.lo OgreStringConverter.lo OgreStringInterface.lo OgreSubEntity.lo OgreSubMesh.lo OgreTagPoint.lo OgreTechnique.lo OgreTextAreaOverlayElement.lo OgreTexture.lo OgreTextureManager.lo OgreTextureUnitState.lo OgreUnifiedHighLevelGpuProgram.lo OgreUserDefinedObject.lo OgreVector2.lo OgreVector3.lo OgreVector4.lo OgreVertexIndexData.lo OgreViewport.lo OgreWireBoundingBox.lo OgreZip.lo OgreCompositionPass.lo OgreCompositionTargetPass.lo OgreCompositionTechnique.lo OgreCompositor.lo OgreCompositorChain.lo OgreCompositorInstance.lo OgreCompositorManager.lo OgreCompositorSerializer.lo OgreCompositorScriptCompiler.lo OgreCompiler2Pass.lo OgreTimer.lo OgreConfigDialog.lo OgreErrorDialog.lo OgreWindowEventUtilities.lo  OgreILImageCodec.lo OgreILCodecs.lo OgreILUtil.lo  -lfreetype -lz -lzzip -lz   -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes -lpango-1.0 -lcairo -lX11 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0    -lX11 -lXaw libSSEsupport.la -lCg -lILU -lIL -lpthread -lz -lm -ldl 
g++ -shared -nostdlib /usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/crti.o /usr/lib/gcc/i486-linux-gnu/4.1.2/crtbeginS.o  .libs/OgreAlignedAllocator.o .libs/OgreAnimation.o .libs/OgreAnimable.o .libs/OgreAnimationState.o .libs/OgreAnimationTrack.o .libs/OgreArchiveManager.o .libs/OgreAutoParamDataSource.o .libs/OgreBillboard.o .libs/OgreBillboardChain.o .libs/OgreBillboardParticleRenderer.o .libs/OgreBillboardSet.o .libs/OgreBone.o .libs/OgreBorderPanelOverlayElement.o .libs/OgreCamera.o .libs/OgreCodec.o .libs/OgreColourValue.o .libs/OgreCommon.o .libs/OgreConfigFile.o .libs/OgreControllerManager.o .libs/OgreConvexBody.o .libs/OgreDataStream.o .libs/OgreDDSCodec.o .libs/OgreDefaultHardwareBufferManager.o .libs/OgreDefaultSceneQueries.o .libs/OgreDynLib.o .libs/OgreDynLibManager.o .libs/OgreEdgeListBuilder.o .libs/OgreEntity.o .libs/OgreException.o .libs/OgreExternalTextureSource.o .libs/OgreExternalTextureSourceManager.o .libs/OgreFileSystem.o .libs/OgreFont.o .libs/OgreFontManager.o .libs/OgreFrustum.o .libs/OgreGpuProgram.o .libs/OgreGpuProgramManager.o .libs/OgreGpuProgramUsage.o .libs/OgreHardwareBufferManager.o .libs/OgreHardwareIndexBuffer.o .libs/OgreHardwareOcclusionQuery.o .libs/OgreHardwareVertexBuffer.o .libs/OgreHardwarePixelBuffer.o .libs/OgreHighLevelGpuProgram.o .libs/OgreHighLevelGpuProgramManager.o .libs/OgreImage.o .libs/OgreInstancedGeometry.o .libs/OgreKeyFrame.o .libs/OgreLight.o .libs/OgreLog.o .libs/OgreLogManager.o .libs/OgreManualObject.o .libs/OgreMaterial.o .libs/OgreMaterialManager.o .libs/OgreMaterialSerializer.o .libs/OgreMaterialScriptCompiler.o .libs/OgreMath.o .libs/OgreMatrix3.o .libs/OgreMatrix4.o .libs/OgreMemoryManager.o .libs/OgreMesh.o .libs/OgreMeshManager.o .libs/OgreMeshSerializer.o .libs/OgreMeshSerializerImpl.o .libs/OgreMovableObject.o .libs/OgreMovablePlane.o .libs/OgreNode.o .libs/OgreNumerics.o .libs/OgreOptimisedUtil.o .libs/OgreOptimisedUtilGeneral.o .libs/OgreOverlay.o .libs/OgreOverlayContainer.o .libs/OgreOverlayElement.o .libs/OgreOverlayElementCommands.o .libs/OgreOverlayManager.o .libs/OgrePixelFormat.o .libs/OgrePanelOverlayElement.o .libs/OgreParticle.o .libs/OgreParticleEmitter.o .libs/OgreParticleEmitterCommands.o .libs/OgreParticleIterator.o .libs/OgreParticleSystem.o .libs/OgreParticleSystemManager.o .libs/OgrePass.o .libs/OgrePatchMesh.o .libs/OgrePatchSurface.o .libs/OgrePlane.o .libs/OgrePlatformInformation.o .libs/OgrePolygon.o .libs/OgrePose.o .libs/OgrePredefinedControllers.o .libs/OgrePrefabFactory.o .libs/OgreProfiler.o .libs/OgreProgressiveMesh.o .libs/OgreQuaternion.o .libs/OgreRectangle2D.o .libs/OgreRenderQueue.o .libs/OgreRenderQueueInvocation.o .libs/OgreRenderQueueSortingGrouping.o .libs/OgreRenderSystem.o .libs/OgreRenderSystemCapabilities.o .libs/OgreRenderTarget.o .libs/OgreRenderTexture.o .libs/OgreRenderWindow.o .libs/OgreResource.o .libs/OgreResourceBackgroundQueue.o .libs/OgreResourceGroupManager.o .libs/OgreResourceManager.o .libs/OgreRibbonTrail.o .libs/OgreRoot.o .libs/OgreRotationSpline.o .libs/OgreSceneManager.o .libs/OgreSceneManagerEnumerator.o .libs/OgreSceneNode.o .libs/OgreSceneQuery.o .libs/OgreSearchOps.o .libs/OgreSerializer.o .libs/OgreShadowCameraSetup.o .libs/OgreShadowCameraSetupFocused.o .libs/OgreShadowCameraSetupLiSPSM.o .libs/OgreShadowCameraSetupPlaneOptimal.o .libs/OgreShadowCaster.o .libs/OgreShadowTextureManager.o .libs/OgreShadowVolumeExtrudeProgram.o .libs/OgreSimpleRenderable.o .libs/OgreSimpleSpline.o .libs/OgreSkeleton.o .libs/OgreSkeletonInstance.o .libs/OgreSkeletonManager.o .libs/OgreSkeletonSerializer.o .libs/OgreStaticGeometry.o .libs/OgreString.o .libs/OgreStringConverter.o .libs/OgreStringInterface.o .libs/OgreSubEntity.o .libs/OgreSubMesh.o .libs/OgreTagPoint.o .libs/OgreTechnique.o .libs/OgreTextAreaOverlayElement.o .libs/OgreTexture.o .libs/OgreTextureManager.o .libs/OgreTextureUnitState.o .libs/OgreUnifiedHighLevelGpuProgram.o .libs/OgreUserDefinedObject.o .libs/OgreVector2.o .libs/OgreVector3.o .libs/OgreVector4.o .libs/OgreVertexIndexData.o .libs/OgreViewport.o .libs/OgreWireBoundingBox.o .libs/OgreZip.o .libs/OgreCompositionPass.o .libs/OgreCompositionTargetPass.o .libs/OgreCompositionTechnique.o .libs/OgreCompositor.o .libs/OgreCompositorChain.o .libs/OgreCompositorInstance.o .libs/OgreCompositorManager.o .libs/OgreCompositorSerializer.o .libs/OgreCompositorScriptCompiler.o .libs/OgreCompiler2Pass.o .libs/OgreTimer.o .libs/OgreConfigDialog.o .libs/OgreErrorDialog.o .libs/OgreWindowEventUtilities.o .libs/OgreILImageCodec.o .libs/OgreILCodecs.o .libs/OgreILUtil.o -Wl,--whole-archive ./.libs/libSSEsupport.a -Wl,--no-whole-archive  /usr/lib/libfreetype.so /usr/lib/libzzip.so /usr/lib/libgtk-x11-2.0.so /usr/lib/libgdk-x11-2.0.so /usr/lib/libatk-1.0.so /usr/lib/libgdk_pixbuf-2.0.so /usr/lib/libpangocairo-1.0.so -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes /usr/lib/libpango-1.0.so /usr/lib/libcairo.so /usr/lib/libgobject-2.0.so /usr/lib/libgmodule-2.0.so /usr/lib/libglib-2.0.so -lX11 -lXaw -lpng /usr/lib/libtiff.so /usr/lib/libjpeg.so -lmng -lCg /usr/lib/libILU.so /usr/lib/libIL.so -lpthread -lz -ldl -L/usr/lib/gcc/i486-linux-gnu/4.1.2 -L/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib -L/lib/../lib -L/usr/lib/../lib -lstdc++ -lm -lc -lgcc_s /usr/lib/gcc/i486-linux-gnu/4.1.2/crtendS.o /usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/crtn.o  -Wl,-rpath -Wl,/usr/lib -Wl,-soname -Wl,libOgreMain-1.4.4.so -o .libs/libOgreMain-1.4.4.so
/usr/bin/ld: cannot find -lmng
collect2: ld returned 1 exit status
make[2]: *** [libOgreMain.la] Error 1
make[2]: Leaving directory `/home/vadi/Desktop/ogrenew/OgreMain/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/vadi/Desktop/ogrenew/OgreMain'
make: *** [all-recursive] Error 1
vadi@vadi-laptop:~/Desktop/ogrenew$ 

```

I'll try that ogre wiki way

---

### Post by Vadi on 2007-09-21
Wiki didn't help either,

```
vadi@vadi-laptop:~/Desktop/ogrenew$ sudo apt-get source --compile ogre
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Need to get 14.9MB of source archives.
Get:1 http://ftp.debian.org unstable/main ogre 1.4.4-2 (dsc) [1135B]
Get:2 http://ftp.debian.org unstable/main ogre 1.4.4-2 (tar) [14.5MB]
Get:3 http://ftp.debian.org unstable/main ogre 1.4.4-2 (diff) [387kB]          
Fetched 14.9MB in 2m20s (107kB/s)                                              
gpg: can't open `/gnupg/options.skel': No such file or directory
gpg: Signature made Wed 05 Sep 2007 05:18:41 AM EDT using DSA key ID 06468DEB
gpg: Can't check signature: public key not found
dpkg-source: extracting ogre in ogre-1.4.4
dpkg-source: unpacking ogre_1.4.4.orig.tar.gz
dpkg-source: applying ./ogre_1.4.4-2.diff.gz
dpkg-buildpackage: source package is ogre
dpkg-buildpackage: source version is 1.4.4-2
dpkg-buildpackage: source changed by Andres Mejia <mcitadel@gmail.com>
dpkg-buildpackage: host architecture i386
dpkg-buildpackage: source version without epoch 1.4.4-2
dpkg-checkbuilddeps: Unmet build dependencies: quilt libfreeimage-dev
dpkg-buildpackage: Build dependencies/conflicts unsatisfied; aborting.
dpkg-buildpackage: (Use -d flag to override.)
Build command 'cd ogre-1.4.4 && dpkg-buildpackage -b -uc' failed.
E: Child process failed
vadi@vadi-laptop:~/Desktop/ogrenew$ 

```.

Why isn't there a .deb that you can easily install about! Meh

---

### Post by Perfect Storm on 2007-09-21
You need then to complile FreeImage first then.

It's quite easy.

---

### Post by Perfect Storm on 2007-09-21
DOH! I think I got it. Free Image is needed though even if it disable in ogre, dunno why.

---

### Post by Perfect Storm on 2007-09-21
Here's the freeimage guide;

```
sudo aptitude update && sudo aptitude upgrade
sudo aptitude install build-essential checkinstall
sudo aptitude install libjpeg62-dev libpng12-dev libtiff4-dev libmng-dev zlib1g-dev

cd ~/Desktop
wget http://prdownloads.sourceforge.net/freeimage/FreeImage393.zip?download
unzip FreeImage393.zip
cd FreeImage
make
sudo checkinstall
```

This should make you able to use the guide I wrote (hopefully).

---

### Post by Vadi on 2007-09-21
Okay, did that, running make now. I got past the point of the "/usr/bin/ld: cannot find -lmng", but right now it's making .Tpo's now. Whatever those are.

"Instancing.cpp: In member function &#8216;void InstancingListener::_burnCPU_()&#8217;:"

...!

---

### Post by Vadi on 2007-09-21
It worked!

So yeah, just add the freeimage guide, and it'll work.

Fun game :)

---

### Post by Perfect Storm on 2007-09-21
Great!!!! :guitar:

---

### Post by Vadi on 2007-09-21
One little thing - can you make it so it adds an entry in applications - games too?

---

### Post by Perfect Storm on 2007-09-21
Sure

---

### Post by cogadh on 2007-09-21
Just to add my confirmation, installing freeimage did it, game works great now.

---

### Post by Perfect Storm on 2007-09-23
Guide now added; [http://gaming.gwos.org/doku.php/guides:funguloids](http://gaming.gwos.org/doku.php/guides:funguloids)

---

### Post by Vadi on 2007-09-23
Ahh cool.

Though, "Check if your sourcelist is fully enable (universe, multiverse and mediabuntu)." should say enable**d**!

---

### Post by Perfect Storm on 2007-09-23
ah! I properly made the mistake throughout my guides LOL

---

### Post by Vadi on 2007-09-23
Hehe.

Just a tip though, you say "Make sure that the driver to your 3D graphic card is proper installed and working.". It should be proper**ly**, and also, nowhere do you say *how* to check! What if I don't know? (which I really don't, except some grep direct rendering command). Could you make a separate page that explains how to check?

---

### Post by Perfect Storm on 2007-09-23
Geeeeeez....! You're annoying! LOL :lolflag:

fixed!

I'll see what I can do about the "checking" thing.

---

### Post by Vadi on 2007-09-23
Just making stuff more newbie-friendly :)

---

### Post by Perfect Storm on 2007-09-24
What do you say if you become a team member of UGA, I could use one to correct my/the spellings?

---

### Post by Vadi on 2007-09-24
> **Artificial Intelligence said:**
> What do you say if you become a team member of UGA, I could use one **personal minion **to correct my/the spellings?

Eh, okay. I'm in.

---

### Post by Perfect Storm on 2007-09-24
> **Vadi said:**
> Eh, okay. I'm in.

Great!
PM CK (compiledkernel) and he can set it up for you.

---

### Post by cogadh on 2007-09-24
Yes! I'm not the new guy anymore!

---

### Post by JurB on 2007-10-16
You could have just waited for [a .deb]("http://www.getdeb.net/app.php?name=Those+Funny+Funguloids") to pop up at GetDeb ;)


I'm getting some weird white squares ingame sometimes... anyone with the same problem?

---

### Post by Perfect Storm on 2007-10-16
> **JurB said:**
> You could have just waited for [a .deb]("http://www.getdeb.net/app.php?name=Those+Funny+Funguloids") to pop up at GetDeb ;)


I'm getting some weird white squares ingame sometimes... anyone with the same problem?

What's the fun in that :)
I guess the Ogre is version 1.4 in Gutsy then.

---

