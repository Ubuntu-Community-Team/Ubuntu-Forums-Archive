---
title: "Manually apply wine patch"
date: 2011-02-28
forum: Wine
---

### Post by sokekoke on 2011-02-28
When i try to apply a patch to wine i get "mamalformed patch at line 4" .. the author of the patch suggest that i add the line manually. How can i do this?

here is the entire patch:

```
--- a/dlls/wined3d/directx.c 
+++ b/dlls/wined3d/directx.c 
@@ -1347,6 +1347,7 @@ static BOOL IWineD3DImpl_FillGLCaps(WineD3D_GL_Info *gl_info) { 
gl_info->max_blends = gl_max;
TRACE_(d3d_caps)("Max blends: %u.\n", gl_info->max_blends); 
} 
+ gl_info->max_blends = 4; 
if (gl_info->supported[EXT_TEXTURE3D]) 
{ 
glGetIntegerv(GL_MAX_3D_TEXTURE_SIZE_EXT, &gl_max); 

```

when i try to gedit /dlls/wined3d/directx.c the file is empty.

Thanks

---

### Post by cogadh on 2011-02-28
That's because you are opening a file that doesn't exist. The file path you are using there is either not complete or is inaccurate. There should be no "/dll" directory off the root of your file system, but there may be one within the directory where you have the Wine source code stored. Assuming that you have it somewhere in your home directory and that it is simply called "winesource", the correct path would be something like /home/<your username>/winesource/dlls/wined3d/directx.c. Obviously I don't know how or where you have the Wine sources stored, so you'll have to modify that path accurately yourself.

---

