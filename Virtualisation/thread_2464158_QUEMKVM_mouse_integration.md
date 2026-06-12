---
title: "QUEM/KVM mouse integration"
date: 2021-06-25
forum: Virtualisation
---

### Post by monkeybrain20122 on 2021-06-25
So I installed Fedora 34 in KVM (ubuntu 20.04 host) to check out gnome-4.0. It works well except the hot corner and edges don't work ( because they are in conflict with those effects of the host?, say you go the hot corner, it activates it in the host, host DE is unity but it has similar hot corners and edge effects) I tried to uninstall spice-vdagent in guest to disable mouse integration but then the screen resolution become vastly reduced (I guess, spice-vdagent is kind of like guest additions in VirtualBox) and the corner still doesn't work.

In the guest

```
[monkeybrain@fedora ~]$ glxinfo | grep OpenGL
OpenGL vendor string: Mesa/X.org
OpenGL renderer string: llvmpipe (LLVM 12.0.0, 256 bits)
OpenGL core profile version string: 4.5 (Core Profile) Mesa 21.1.3
OpenGL core profile shading language version string: 4.50
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
OpenGL version string: 3.1 Mesa 21.1.3
OpenGL shading language version string: 1.40
OpenGL context flags: (none)
OpenGL extensions:
OpenGL ES profile version string: OpenGL ES 3.2 Mesa 21.1.3
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.20
OpenGL ES profile extensions:




```
```

[monkeybrain@fedora ~]$ glxinfo | grep render
direct rendering: Yes
    GLX_MESA_query_renderer, GLX_MESA_swap_control, GLX_OML_swap_method, 
    GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, GLX_MESA_query_renderer, 
Extended renderer info (GLX_MESA_query_renderer):
OpenGL renderer string: llvmpipe (LLVM 12.0.0, 256 bits)
    GL_ARB_compute_shader, GL_ARB_conditional_render_inverted, 
    GL_NV_conditional_render, GL_NV_copy_image, GL_NV_depth_clamp, 
    GL_ARB_conditional_render_inverted, GL_ARB_conservative_depth, 
    GL_NV_conditional_render, GL_NV_copy_depth_to_color, GL_NV_copy_image, 
    GL_EXT_render_snorm, GL_EXT_robustness, GL_EXT_sRGB_write_control, 
    GL_MESA_shader_integer_functions, GL_NV_conditional_render, 
    GL_OES_element_index_uint, GL_OES_fbo_render_mipmap, 




```

And by way of testing the graphics in the guest, I installed the gnome-shell compiz extension and 'wobbly windows' does work (actually that is the only compiz effect in the extension out of the box), the blur background extension also works (strangely that doesn't work in the host with gnome-shell 3 since it doesn't play well with the Nvidia card)

Is there a way to configure the VM so that the corners work in the guest?
Thanks.

Edited: I mistakenly chose the wrong tag, host OS is Ubuntu, not Lubuntu, don't know how to change that.

---

### Post by Dennis N on 2021-06-25
> Is there a way to configure the VM so that the corners work in the guest?
You can install the "hot edge" gnome-shell extension in Fedora 34 - then the bottom edge works like a hot corner.

---

### Post by monkeybrain20122 on 2021-06-25
> **Dennis N said:**
> You can install the "hot edge" gnome-shell extension in Fedora 34 - then the bottom edge works like a hot corner.

No, doesn't work. The edge and corners just don't work. I think it has something to do with mouse integration. When the mouse reaches the edge or corner it leaves the VM, and if full screen it basically triggers the corners and edges of the host.

---

### Post by Dennis N on 2021-06-25
> **monkeybrain20122 said:**
> No, doesn't work. The edge and corners just don't work. I think it has something to do with mouse integration. When the mouse reaches the edge or corner it leaves the VM, and if full screen it basically triggers the corners and edges of the host.
Yes, I have seen similar effects. With Ubuntu Gnome as guest OS fullscreen, the hot corners do nothing. I just use the activities button in upper left, or the super key. Also I have to set the guest dash-to-dock to not autohide or I activate the host's dock instead of the guest dock.

---

### Post by MAFoElffen on 2021-06-26
> **monkeybrain20122 said:**
> So I installed Fedora 34 in KVM (ubuntu 20.04 host) to check out gnome-4.0. It works well except the hot corner and edges don't work ( because they are in conflict with those effects of the host?, say you go the hot corner, it activates it in the host, host DE is unity but it has similar hot corners and edge effects) I tried to uninstall spice-vdagent in guest to disable mouse integration but then the screen resolution become vastly reduced (I guess, spice-vdagent is kind of like guest additions in VirtualBox) and the corner still doesn't work.

Is there a way to configure the VM so that the corners work in the guest?
Wait a minute... LOL

I have 20.04 with NVidia on my host... Just to test what you said, I spun up a Fedora 34 guest in KVM... Spice/QRT and virtio drivers... 

True, the hot corners don't work in the Virt Manager if it is "windowed." That's because when Virt Manager is windowed, the mouse is not lock insided the window. It can go outside the window to the rest of the host desktop. That's how it should work, so it doen't sense that it hits an edge or corner in the VM. 

But in full screen mode, it works as it should on-metal. It then hits edge and corner limits and generates those screen events just fine. Just like it does with a recent Windows Guest on hot edges and corners...

---

### Post by monkeybrain20122 on 2021-06-26
> **MAFoElffen said:**
> Wait a minute... LOL

I have 20.04 with NVidia on my host... Just to test what you said, I spun up a Fedora 34 guest in KVM... Spice/QRT and virtio drivers... 

True, the hot corners don't work in the Virt Manager if it is "windowed." That's because when Virt Manager is windowed, the mouse is not lock insided the window. It can go outside the window to the rest of the host desktop. That's how it should work, so it doen't sense that it hits an edge or corner in the VM. 

But in full screen mode, it works as it should on-metal. It then hits edge and corner limits and generates those screen events just fine. Just like it does with a recent Windows Guest on hot edges and corners...

No, it doesn't work in full screen either because the host is unity and when it hits the edges it triggers effects on the host and I go to a different desktop (the top and bottom edges can be arranged to not trigger that if the VM is opened in the right virtual desktops but GS has no special effects on these edges to test as far as I know)  I guess it is the way it is unless I disable the effects on the host.  I just want to see what the buzz is all about for gnome-shell 4 anyway so never mind. Thanks for the input. :) The host here is also 20.04 with Nvidia.

Edited: yeah so if I disable workspaces and the scale addon in unity the corner and edges work. :) But I was reluctant to change the settings on the host.

---

### Post by MAFoElffen on 2021-06-26
Dang. Duplicate post.

---

### Post by MAFoElffen on 2021-06-26
> **monkeybrain20122 said:**
> No, it doesn't work in full screen either because the host is unity...
On my host I use gnome-session, not unity... I wonder if that is the difference?

---

### Post by monkeybrain20122 on 2021-08-07
I just found out the activity hot corner and hide top bar intelhide work in wayland but not in xorg, using gnome-shell 40 for Archlinux guest here. For Ubuntu 21.04 guest (gnome-shell) hide top bar intelhide works in Wayland but not in xorg and the hot corner doesn't work in either. Host is the same, Ubuntu 20.04 on xorg and with Unity.

But I started the VM with the qemu commandline instead of virt-manager so when go fullscreen the mouse doesn't venture out of the VM.

---

