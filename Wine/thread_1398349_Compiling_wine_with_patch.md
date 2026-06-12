---
title: "Compiling wine with patch"
date: 2010-02-04
forum: Wine
---

### Post by esauer on 2010-02-04
Hello,

I am trying to compile wine in ubuntu karmic with two patches:

```
diff --git a/dlls/wined3d/vertexshader.c b/dlls/wined3d/vertexshader.c
index 5fab988..9d6fffb 100644
--- a/dlls/wined3d/vertexshader.c
+++ b/dlls/wined3d/vertexshader.c
@@ -602,7 +602,7 @@ static HRESULT WINAPI IWineD3DVertexShaderImpl_CompileShader(IWineD3DVertexShade
              */
             if(swizzled_attribs_differ(This, vdecl)) {
                 WARN("Recompiling vertex shader %p due to D3DCOLOR input changes\n", This);
-                goto recompile;
+                //goto recompile;
             }
             WARN("Swizzled attribute validation required an expensive comparison\n");
         }
```

and

```
--- wine.old/dlls/wined3d/directx.c	2008-04-04 10:55:13.000000000 -0400
+++ wine/dlls/wined3d/directx.c	2008-04-18 13:32:44.000000000 -0400
@@ -839,7 +839,7 @@
         }
         if (gl_info->supported[ARB_MULTITEXTURE]) {
             glGetIntegerv(GL_MAX_TEXTURE_UNITS_ARB, &gl_max);
-            gl_info->max_textures = min(MAX_TEXTURES, gl_max);
+            gl_info->max_textures = 8;
             TRACE_(d3d_caps)("Max textures: %d\n", gl_info->max_textures);
 
             if (gl_info->supported[NV_REGISTER_COMBINERS]) {
@@ -2802,8 +2802,13 @@
                                      WINED3DPMISCCAPS_CLIPTLVERTS           |
                                      WINED3DPMISCCAPS_CLIPPLANESCALEDPOINTS |
                                      WINED3DPMISCCAPS_MASKZ                 |
-                                     WINED3DPMISCCAPS_BLENDOP;
-                                    /* TODO:
+				     WINED3DPMISCCAPS_TSSARGTEMP	    |
+				     WINED3DPMISCCAPS_FOGANDSPECULARALPHA   |
+				     WINED3DPMISCCAPS_SEPARATEALPHABLEND    |
+				     WINED3DPMISCCAPS_BLENDOP               |
+                                     WINED3DPMISCCAPS_FOGVERTEXCLAMPED;
+				    
+				    /* TODO:
                                         WINED3DPMISCCAPS_NULLREFERENCE
                                         WINED3DPMISCCAPS_INDEPENDENTWRITEMASKS
                                         WINED3DPMISCCAPS_FOGANDSPECULARALPHA
@@ -3067,8 +3072,8 @@
     pCaps->MaxVertexBlendMatrixIndex   = 0;
 
     pCaps->MaxAnisotropy   = GL_LIMITS(anisotropy);
-    pCaps->MaxPointSize    = GL_LIMITS(pointsize);
-
+    //pCaps->MaxPointSize    = GL_LIMITS(pointsize);
+    pCaps->MaxPointSize    = 64.0f;
 
     pCaps->VertexProcessingCaps = WINED3DVTXPCAPS_DIRECTIONALLIGHTS |
                                   WINED3DVTXPCAPS_MATERIALSOURCE7   |
@@ -3085,7 +3090,13 @@
     pCaps->MaxStreamStride     = 1024;
 
     /* d3d9.dll sets D3DDEVCAPS2_CAN_STRETCHRECT_FROM_TEXTURES here because StretchRects is implemented in d3d9 */
-    pCaps->DevCaps2                          = WINED3DDEVCAPS2_STREAMOFFSET;
+    
+    //pCaps->DevCaps2                          = WINED3DDEVCAPS2_STREAMOFFSET;
+    pCaps->DevCaps2                          = WINED3DDEVCAPS2_STREAMOFFSET |
+                                               WINED3DDEVCAPS2_CAN_STRETCHRECT_FROM_TEXTURES |
+					       WINED3DDEVCAPS2_PRESAMPLEDDMAPNPATCH |
+					       WINED3DDEVCAPS2_VERTEXELEMENTSCANSHARESTREAMOFFSET;
+    
     /* TODO: VS3.0 needs at least D3DDEVCAPS2_VERTEXELEMENTSCANSHARESTREAMOFFSET */
     pCaps->MaxNpatchTessellationLevel        = 0;
     pCaps->MasterAdapterOrdinal              = 0;
```

What I have done so far is create a file for each of these code blocks and tried to "patch" them using 

```
sudo patch -p1  < patchname
```

from inside the wine source directory I extracted. When I do this, I get similar errors:

```
Hunk #1 FAILED at 602.
1 out of 1 hunk FAILED -- saving rejects to file dlls/wined3d/vertexshader.c.rej

```

and 

```
patching file dlls/wined3d/directx.c
Hunk #1 FAILED at 839.
Hunk #2 FAILED at 2802.
Hunk #3 FAILED at 3072.
Hunk #4 FAILED at 3090.
4 out of 4 hunks FAILED -- saving rejects to file dlls/wined3d/directx.c.rej

```

Can someone tell me what I am doing wrong?

Thanks!

---

### Post by rocky5051 on 2010-02-04
That patch might only work with one (or a few) older revisions of Wine, since failed hunks usually mean the code it was mean't to move and replace wasn't where it was expected to be. Try the last known version of Wine known to work with that patch.

Just out of curiosity, what is the patch for anyway?

---

### Post by beastrace91 on 2010-02-04
> **rocky5051 said:**
> Just out of curiosity, what is the patch for anyway?

A link to the patch and then letting us know what Wine version you are trying to recompile would be very helpful :)

~Jeff

---

### Post by esauer on 2010-02-04
I found the patches in these articles:

[http://www.wine-reviews.net/benchmarks/compile-wine-with-the-3dmark-patch.html](http://www.wine-reviews.net/benchmarks/compile-wine-with-the-3dmark-patch.html)

[http://www.wine-reviews.net/games/company-of-heroes-on-linux-with-wine.html](http://www.wine-reviews.net/games/company-of-heroes-on-linux-with-wine.html)

I am attempting to get Company of Heroes running in Ubuntu.

I just downloaded the latest wine version (1.1.33)

Thanks.

---

### Post by beastrace91 on 2010-02-04
Howdy,

As I thought that patch you linked to is some year and a half old now (The Wine version it talks about is pre 1.0.0 even) - it is no longer needed. It is included in the latest Wine source. Just install Wine 1.1.33 from a .deb package

EDIT: Also latest Wine version as of today is 1.1.37 FYI

Regards,
~Jeff

---

### Post by esauer on 2010-02-05
Ok, and what about the other patch? (the smaller one) how can I find out if that is included as well?

---

### Post by beastrace91 on 2010-02-05
> **esauer said:**
> Ok, and what about the other patch? (the smaller one) how can I find out if that is included as well?

Try loading your app with default Wine. That other patch is quite old as well - odds are it is no longer needed as well.

~Jeff

---

### Post by esauer on 2010-02-05
I tried loading with default wine. I got through the intro video and then the screen just goes black. Any other suggestions on how I can troubleshoot?

---

### Post by beastrace91 on 2010-02-06
Check appdb.winehq.org for the program you are trying to run. (I'd provide a direct link but I am posting from my phone atm)

~Jeff

---

