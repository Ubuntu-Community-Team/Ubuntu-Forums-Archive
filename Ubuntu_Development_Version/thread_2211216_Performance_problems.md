---
title: "Performance problems"
date: 2014-03-14
forum: Ubuntu Development Version
---

### Post by DisappearingOak on 2014-03-14
I'm noticing that some animations like min/max are distractingly laggy. Not always, but a lot of the time. And this has been the case for at least past two releases. I hope someone can file a proper useful bug to fix this. That is, if anyone has experienced the same. 

The dash blur is slightly screechy during preview animation also, but in 14.04 it has been speeded up so that I don't experience the issue on my system where it is horridly laggy like it is for some others. 

I think if anyone wants to use this thread to discuss performance problems and any way to get it fixed, please feel free to. I hope devs at least make this LTS free of performance problems.

---

### Post by ventrical on 2014-03-14
With the exception of ccsm not being totally up to par, I am having a very snappy response time here with those anims that you have mentioned across several different form factors. Also , the trusty cycle had included older ATi graphics hardware to fit in with mir/x and not rollover to llvmpipe but this is not to say that any given system may  one day seem to be running smooth and fast and then , after an  update (assuming it has rolled to llvmpipe) then there will defintely be a performance problem with many form factors circa 2005 and downward ; perhaps even on newer trades as well. My observations of course.

---

### Post by xc3RnbFO8P on 2014-03-15
I can see  improvement in performance.
I have been testing performance with GLmark2.

5.november 2013

> rig@rig-Aspire-R3600:~$ glmark2
=======================================================
    glmark2 2012.08
=======================================================
    OpenGL Information
    GL_VENDOR:     NVIDIA Corporation
    GL_RENDERER:   ION/integrated/SSE2
    GL_VERSION:    3.3.0 NVIDIA 331.17
=======================================================
[build] use-vbo=false: FPS: 306 FrameTime: 3.268 ms
[build] use-vbo=true: FPS: 341 FrameTime: 2.933 ms
[texture] texture-filter=nearest: FPS: 301 FrameTime: 3.322 ms
[texture] texture-filter=linear: FPS: 299 FrameTime: 3.344 ms
[texture] texture-filter=mipmap: FPS: 289 FrameTime: 3.460 ms
[shading] shading=gouraud: FPS: 293 FrameTime: 3.413 ms
[shading] shading=blinn-phong-inf: FPS: 292 FrameTime: 3.425 ms
[shading] shading=phong: FPS: 290 FrameTime: 3.448 ms
[bump] bump-render=high-poly: FPS: 265 FrameTime: 3.774 ms
[bump] bump-render=normals: FPS: 328 FrameTime: 3.049 ms
[bump] bump-render=height: FPS: 326 FrameTime: 3.067 ms
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 228 FrameTime: 4.386 ms
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 143 FrameTime: 6.993 ms
[pulsar] light=false:quads=5:texture=false: FPS: 255 FrameTime: 3.922 ms
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4: FPS: 123 FrameTime: 8.130 ms
[desktop] effect=shadow:windows=4: FPS: 196 FrameTime: 5.102 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 91 FrameTime: 10.989 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 106 FrameTime: 9.434 ms
[buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 102 FrameTime: 9.804 ms
[ideas] speed=duration: FPS: 252 FrameTime: 3.968 ms
[jellyfish] <default>: FPS: 186 FrameTime: 5.376 ms
[terrain] <default>: FPS: 26 FrameTime: 38.462 ms
[conditionals] fragment-steps=0:vertex-steps=0: FPS: 265 FrameTime: 3.774 ms
[conditionals] fragment-steps=5:vertex-steps=0: FPS: 285 FrameTime: 3.509 ms
[conditionals] fragment-steps=0:vertex-steps=5: FPS: 295 FrameTime: 3.390 ms
[function] fragment-complexity=low:fragment-steps=5: FPS: 291 FrameTime: 3.436 ms
[function] fragment-complexity=medium:fragment-steps=5: FPS: 273 FrameTime: 3.663 ms
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 288 FrameTime: 3.472 ms
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5: FPS: 286 FrameTime: 3.497 ms
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5: FPS: 293 FrameTime: 3.413 ms
=======================================================
                                  glmark2 Score: 243 
=======================================================
rig@rig-Aspire-R3600:~$ 

Today

> rig@rig-Aspire-R3600:~$ glmark2
=======================================================
    glmark2 2012.08
=======================================================
    OpenGL Information
    GL_VENDOR:     NVIDIA Corporation
    GL_RENDERER:   ION/integrated/SSE2
    GL_VERSION:    3.3.0 NVIDIA 331.49
=======================================================
[build] use-vbo=false: FPS: 379 FrameTime: 2.639 ms
[build] use-vbo=true: FPS: 416 FrameTime: 2.404 ms
[texture] texture-filter=nearest: FPS: 367 FrameTime: 2.725 ms
[texture] texture-filter=linear: FPS: 363 FrameTime: 2.755 ms
[texture] texture-filter=mipmap: FPS: 376 FrameTime: 2.660 ms
[shading] shading=gouraud: FPS: 367 FrameTime: 2.725 ms
[shading] shading=blinn-phong-inf: FPS: 367 FrameTime: 2.725 ms
[shading] shading=phong: FPS: 352 FrameTime: 2.841 ms
[bump] bump-render=high-poly: FPS: 315 FrameTime: 3.175 ms
[bump] bump-render=normals: FPS: 409 FrameTime: 2.445 ms
[bump] bump-render=height: FPS: 406 FrameTime: 2.463 ms
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 277 FrameTime: 3.610 ms
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 154 FrameTime: 6.494 ms
[pulsar] light=false:quads=5:texture=false: FPS: 313 FrameTime: 3.195 ms
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4: FPS: 148 FrameTime: 6.757 ms
[desktop] effect=shadow:windows=4: FPS: 242 FrameTime: 4.132 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 92 FrameTime: 10.870 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 111 FrameTime: 9.009 ms
[buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 107 FrameTime: 9.346 ms
[ideas] speed=duration: FPS: 306 FrameTime: 3.268 ms
[jellyfish] <default>: FPS: 230 FrameTime: 4.348 ms
[terrain] <default>: FPS: 31 FrameTime: 32.258 ms
[conditionals] fragment-steps=0:vertex-steps=0: FPS: 360 FrameTime: 2.778 ms
[conditionals] fragment-steps=5:vertex-steps=0: FPS: 349 FrameTime: 2.865 ms
[conditionals] fragment-steps=0:vertex-steps=5: FPS: 360 FrameTime: 2.778 ms
[function] fragment-complexity=low:fragment-steps=5: FPS: 361 FrameTime: 2.770 ms
[function] fragment-complexity=medium:fragment-steps=5: FPS: 334 FrameTime: 2.994 ms
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 357 FrameTime: 2.801 ms
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5: FPS: 356 FrameTime: 2.809 ms
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5: FPS: 357 FrameTime: 2.801 ms
=======================================================
                                  glmark2 Score: 298 
=======================================================
rig@rig-Aspire-R3600:~$ 


---

### Post by DisappearingOak on 2014-03-16
Oibaf's PPA successfully made Gnome Shell silky smooth on Saucy (I'm on RS880, radeon hd 4250 desktop igpu). I've yet to test trusty or the other DEs. If anyone's having animation lag, I guess they could try this ppa.

---

