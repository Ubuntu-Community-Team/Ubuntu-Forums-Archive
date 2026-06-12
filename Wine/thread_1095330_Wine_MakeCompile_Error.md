---
title: "Wine Make/Compile Error"
date: 2009-03-13
forum: Wine
---

### Post by 133794m3r on 2009-03-13
> **Meow27 said:**
> ok you are going to have to do this

open up a terminal and type ```
sudo apt-get build-dep wine
```

while you are downloading these dependencies, you will need to download the source code for wine [http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=77449&release_id=664595](http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=77449&release_id=664595)

after you are done with installing the dependencies in the terminal, open up a new one (you should extract the wine source in as the folder in your home folder)

in the terminal type ```
cd wine1.1.6
``` or whatever the folder is

then type /.configure

this will take ~3 minutes

after that you will need to do ```
make
```
which can take 1-3 hours, depending on you cpu

after that is completed, do ```
sudo make install
```


just make sure you uninstalled your older version of wine just in case
was doing that but then on the make command i get this output. I'm trying to build wine 1.1.16 with the Perfect World Fix.
```
/usr/include/bits/stdlib.h:78: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/stdlib.h: In function ‘wctomb’:
/usr/include/bits/stdlib.h:93: error: ‘size_t’ undeclared (first use in this function)
/usr/include/bits/stdlib.h:94: error: too many arguments to function ‘__wctomb_chk’
/usr/include/bits/stdlib.h: At top level:
/usr/include/bits/stdlib.h:99: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__mbstowcs_chk’
/usr/include/bits/stdlib.h:102: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__mbstowcs_alias’
/usr/include/bits/stdlib.h:106: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__mbstowcs_chk_warn’
/usr/include/bits/stdlib.h:114: error: expected ‘,’ or ‘;’ before ‘mbstowcs’
/usr/include/bits/stdlib.h:131: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__wcstombs_chk’
/usr/include/bits/stdlib.h:134: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__wcstombs_alias’
/usr/include/bits/stdlib.h:138: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__wcstombs_chk_warn’
/usr/include/bits/stdlib.h:145: error: expected ‘,’ or ‘;’ before ‘wcstombs’
In file included from device.c:32:
wined3d_private.h: In function ‘is_identity_fixup’:
wined3d_private.h:112: error: too many arguments to function ‘memcmp’
device.c: In function ‘IWineD3DDeviceImpl_QueryInterface’:
device.c:70: error: too many arguments to function ‘memcmp’
device.c:71: error: too many arguments to function ‘memcmp’
device.c:72: error: too many arguments to function ‘memcmp’
device.c: In function ‘IWineD3DDeviceImpl_CreateStateBlock’:
device.c:397: error: too many arguments to function ‘memset’
device.c: In function ‘IWineD3DDeviceImpl_CreateVolume’:
device.c:1171: error: too many arguments to function ‘memset’
device.c: In function ‘IWineD3DDeviceImpl_CreateSwapChain’:
device.c:1803: error: too many arguments to function ‘memset’
device.c: In function ‘IWineD3DDeviceImpl_LoadLogo’:
device.c:2187: error: too many arguments to function ‘memset’
device.c: In function ‘IWineD3DDeviceImpl_SetDisplayMode’:
device.c:2677: error: too many arguments to function ‘memset’
device.c: In function ‘IWineD3DDeviceImpl_SetTransform’:
device.c:2889: error: too many arguments to function ‘memcmp’
device.c:2893: error: too many arguments to function ‘memcpy’
device.c:2906: error: too many arguments to function ‘memcmp’
device.c: In function ‘IWineD3DDeviceImpl_SetVertexShaderConstantB’:
device.c:3686: error: too many arguments to function ‘memcpy’
device.c: In function ‘IWineD3DDeviceImpl_GetVertexShaderConstantB’:
device.c:3714: error: too many arguments to function ‘memcpy’
device.c: In function ‘IWineD3DDeviceImpl_SetVertexShaderConstantI’:
device.c:3733: error: too many arguments to function ‘memcpy’
device.c: In function ‘IWineD3DDeviceImpl_GetVertexShaderConstantI’:
device.c:3762: error: too many arguments to function ‘memcpy’
device.c: In function ‘IWineD3DDeviceImpl_SetVertexShaderConstantF’:
device.c:3782: error: too many arguments to function ‘memcpy’
device.c:3796: error: too many arguments to function ‘memset’
device.c: In function ‘IWineD3DDeviceImpl_GetVertexShaderConstantF’:
device.c:3816: error: too many arguments to function ‘memcpy’
device.c: In function ‘IWineD3DDeviceImpl_SetPixelShaderConstantB’:
device.c:4079: error: too many arguments to function ‘memcpy’
device.c: In function ‘IWineD3DDeviceImpl_GetPixelShaderConstantB’:
device.c:4107: error: too many arguments to function ‘memcpy’
device.c: In function ‘IWineD3DDeviceImpl_SetPixelShaderConstantI’:
device.c:4126: error: too many arguments to function ‘memcpy’
device.c: In function ‘IWineD3DDeviceImpl_GetPixelShaderConstantI’:
device.c:4155: error: too many arguments to function ‘memcpy’
device.c: In function ‘IWineD3DDeviceImpl_SetPixelShaderConstantF’:
device.c:4175: error: too many arguments to function ‘memcpy’
device.c:4189: error: too many arguments to function ‘memset’
device.c: In function ‘IWineD3DDeviceImpl_GetPixelShaderConstantF’:
device.c:4209: error: too many arguments to function ‘memcpy’
device.c: In function ‘process_vertices_strided’:
device.c:4253: error: too many arguments to function ‘memcpy’
device.c:4469: error: too many arguments to function ‘memcpy’
device.c:4471: error: too many arguments to function ‘memcpy’
device.c:4495: error: too many arguments to function ‘memcpy’
device.c:4526: error: too many arguments to function ‘memcpy’
device.c:4546: error: too many arguments to function ‘memcpy’
device.c:4548: error: too many arguments to function ‘memcpy’
device.c: In function ‘IWineD3DDeviceImpl_ProcessVertices’:
device.c:4587: error: too many arguments to function ‘memset’
device.c: In function ‘IWineD3DDeviceImpl_UpdateVolume’:
device.c:5547: error: too many arguments to function ‘memcpy’
device.c: In function ‘IWineD3DDeviceImpl_UpdateSurface’:
device.c:5942: error: too many arguments to function ‘memset’
device.c: In function ‘IWineD3DDeviceImpl_DrawRectPatch’:
device.c:6140: error: too many arguments to function ‘memcmp’
device.c: In function ‘IWineD3DDeviceImpl_ColorFill’:
device.c:6414: error: too many arguments to function ‘memset’
device.c: In function ‘IWineD3DDeviceImpl_ClearRendertargetView’:
device.c:6462: error: too many arguments to function ‘memset’
device.c: In function ‘IWineD3DDeviceImpl_SetCursorProperties’:
device.c:6904: error: too many arguments to function ‘memcpy’
device.c: In function ‘is_display_mode_supported’:
device.c:7142: error: too many arguments to function ‘memset’
make[2]: *** [device.o] Error 1
make[2]: Leaving directory `/home/mac/wine-1.1.16/dlls/wined3d'
make[1]: *** [wined3d] Error 2
make[1]: Leaving directory `/home/mac/wine-1.1.16/dlls'
make: *** [dlls] Error 2

```

---

### Post by Meow27 on 2009-03-13
does it compile with the normal source?

is this in /home/username/wine1.1.6 ?

---

### Post by 133794m3r on 2009-03-13
yes it's there and i'm unsure if it'll compile with normal source i'll check it right after i get done with this current round of it since if it'll not work this way :/ there's no reason to just not do the normal install correct? Basically i'm trying to do this current build of it if it fails then i'll redo it with the base socurce.

here's the source changes that i was using
```

--- wine-1.1.14/dlls/wined3d/device.c	2009-01-30 18:54:01.000000000 +0200
+++ wine/dlls/wined3d/device.c	2009-02-02 16:34:31.000000000 +0200
@@ -5997,8 +5997,7 @@
                 } if (destFormat != srcFormat) {
                     FIXME("Updating mixed format compressed texture is not curretly support\n");
                 } else {
-                    GL_EXTCALL(glCompressedTexImage2DARB(glDescription->target, glDescription->level,
-                            glDescription->glFormatInternal, srcWidth, srcHeight, 0, destSize, data));
+                    FIXME("PW no S3TC support");
                 }
             } else {
                 FIXME("Attempting to update a DXT compressed texture without hardware support\n");
--- wine-1.1.14/dlls/wined3d/directx.c	2009-01-30 18:54:01.000000000 +0200
+++ wine/dlls/wined3d/directx.c	2009-02-02 16:38:22.000000000 +0200
@@ -2303,7 +2303,7 @@
         case WINED3DFMT_DXT5:
             if (GL_SUPPORT(EXT_TEXTURE_COMPRESSION_S3TC)) {
                 TRACE_(d3d_caps)("[OK]\n");
-                return TRUE;
+                return FALSE;
             }
             TRACE_(d3d_caps)("[FAILED]\n");
             return FALSE;
```

---

