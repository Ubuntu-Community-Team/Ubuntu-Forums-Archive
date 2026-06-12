---
title: "Segfault when trying to go to System -&gt; Details"
date: 2013-05-15
forum: Virtualisation
---

### Post by daerid on 2013-05-15
I'm running 13.04 in Virtual Box v4.2.12, and everything seems to work fine, except whenever I go to System Settings -> Settings -> Details I get a crash. Running gnome-control-center from the Terminal results in the following: 

```
(gnome-control-center:4653): info-cc-panel-WARNING **: PackageKit version 7.4.0 not supportedOpenGL Warning: glFlushVertexArrayRangeNV not found in mesa table
OpenGL Warning: glVertexArrayRangeNV not found in mesa table
OpenGL Warning: glCombinerInputNV not found in mesa table
OpenGL Warning: glCombinerOutputNV not found in mesa table
OpenGL Warning: glCombinerParameterfNV not found in mesa table
OpenGL Warning: glCombinerParameterfvNV not found in mesa table
OpenGL Warning: glCombinerParameteriNV not found in mesa table
OpenGL Warning: glCombinerParameterivNV not found in mesa table
OpenGL Warning: glFinalCombinerInputNV not found in mesa table
OpenGL Warning: glGetCombinerInputParameterfvNV not found in mesa table
OpenGL Warning: glGetCombinerInputParameterivNV not found in mesa table
OpenGL Warning: glGetCombinerOutputParameterfvNV not found in mesa table
OpenGL Warning: glGetCombinerOutputParameterivNV not found in mesa table
OpenGL Warning: glGetFinalCombinerInputParameterfvNV not found in mesa table
OpenGL Warning: glGetFinalCombinerInputParameterivNV not found in mesa table
OpenGL Warning: glDeleteFencesNV not found in mesa table
OpenGL Warning: glFinishFenceNV not found in mesa table
OpenGL Warning: glGenFencesNV not found in mesa table
OpenGL Warning: glGetFenceivNV not found in mesa table
OpenGL Warning: glIsFenceNV not found in mesa table
OpenGL Warning: glSetFenceNV not found in mesa table
OpenGL Warning: glTestFenceNV not found in mesa table
OpenGL Warning: XGetVisualInfo returned 0 visuals for 0x7f1deb88aba0
OpenGL Warning: Retry with 0x8002 returned 0 visuals
Segmentation fault (core dumped)
```

I'm not sure where to go from here to fix this. I searched Google for quite a while before giving up and coming here. Thanks in advance for any help.

---

