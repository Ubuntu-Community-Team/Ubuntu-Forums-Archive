---
title: "Issues with Pixel Unpack Buffer Object on VirtualBox 4.10 OpenGL"
date: 2013-07-16
forum: Virtualisation
---

### Post by arthurp on 2013-07-16
[B][EDIT: I experimented some more and discovered that this was a bug in the old Slick2D or LWJGL. I thought I was using the newest versions I was not. Upgrading fixed the problem. Sorry about that. The lesson is that some OpenGL drivers and much more permissive than others, so success on one implementation does not mean the client is correct.]
[/B]
I am getting an error from an OpenGL app running inside VirtualBox. The program is a Java app based on Slick2D. It is called semanav-ui (just to have a name for it). The error message I am getting is:

```
Exception in thread "main" org.lwjgl.opengl.OpenGLException: Cannot use Buffers when Pixel Unpack Buffer Object is enabled
   at org.lwjgl.opengl.GLChecks.ensureUnpackPBOdisabled(GLChecks.java:120)
   at org.lwjgl.opengl.GL11.glTexImage2D(GL11.java:2701)
   at org.newdawn.slick.opengl.InternalTextureLoader.getTexture(InternalTextureLoader.java:306)
[cut] (The rest of the trace is in the attached file LWJGLError.txt)

```

Does anyone have any idea what could cause this? Are there any other debugging techniques I should try? Could this be a bug in the VirtualBox guest OpenGL driver? (this last is my current best guess)

Both the host and guest are Ubuntu 13.04 and everything is installed using the Ubuntu packages (both VirtualBox VM and the guest additions). Other 3D applications do work in the guest. vminfo and vm logs are in the attached zip file if you want to look at them.

I know this issue could be a bug in LWJGL or Slick2D, however semanav-ui DOES work when running on my system natively.

Thanks a lot!
-Arthur

---

