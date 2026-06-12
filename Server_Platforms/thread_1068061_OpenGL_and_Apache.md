---
title: "OpenGL and Apache"
date: 2009-02-12
forum: Server Platforms
---

### Post by bfree on 2009-02-12
I currently use lighttpd running as a standalone HTTP server to serve dynamically-generated OpenGL video streams.

OpenGL requires a display context in order to render offscreen buffers (Frame Buffer Objects) in hardware.  Using lighttpd as a standalone user-server, it's able to access the desktop display, open an OpenGL context, render an offscreen FBO, and feed it to a video codec for output - fast.

Anyone have any experience with using Apache to access displays on a console-less server?  My server has a high-end GPU on it, and I'd prefer using Apache as a network service, rather than lighttpd as a user app.

Using Mesa is not an option, as it is primarily a software implementation, and doesn't provide full access to GPU extensions (eg: geometry shaders).

---

### Post by digitalbenji on 2009-02-12
if you provide some information on your configuration, and more details on how you do this, I'd love to try to help.  This is really interesting, could you give some configs and such?

---

### Post by bfree on 2009-02-12
> **digitalbenji said:**
> if you provide some information on your configuration, and more details on how you do this, I'd love to try to help.  This is really interesting, could you give some configs and such?

I maintain POGL, an open source Portable OpenGL framework.  It's written/optimized in C, with a Perl binding that runs on Linux, MacOS and Windows.  It benchmarks much faster than the Python and Ruby bindings, and in some cases as fast as C.  I added some APIs to ImageMagick last year to provide optimized buffer-sharing between IM and POGL's FBOs/VBOs/textures.

POGL runs great on Ubuntu via command line using FreeGLUT; it also works via lighttpd and IIS on Windows - I just haven't been able to get a display context on Apache.

---

