---
title: "Emerald running under VMware"
date: 2008-10-10
forum: Virtualisation
---

### Post by whythankyou on 2008-10-10
Okay there doesn't seem to be any posts about this and I'm pretty sure this is the best place to ask.

I know Compiz-fusion is out of the question.  However, I'd like a few things answered if possible.

Question 1: Why does running the command gtk-window-decorator or emerald --replace crash the xserver in the VM, yet running metacity --replace does not?

Question 2: (The money question) Is it possible to have emerald themer run to apply a basic theme?

Since there isn't anything 3d going on, I'd imagine this would be a fairly simple task.  I mean transparency is already support (tested via change the opacity in the panels), this would seem to be something simple... no?

Thanks in advance for any feedback!

*If it helps, I'm running Windows 2008 Server Standard edition x64, running VMware workstation 6.5 with ubuntu hardy heron 8.04 x64 running as the guest os*

---

### Post by ooobuntooo on 2008-10-10
I thought VMware supported 3D.

---

### Post by whythankyou on 2008-10-10
Supports directx 9c :-/

Any ideas on how to debug the issue?

Heres the shared library output, looks good...

```

desktop:~$ ldd /usr/bin/emerald
	linux-gate.so.1 =>  (0xb7faf000)
	libemeraldengine.so.0 => /usr/lib/libemeraldengine.so.0 (0xb7f97000)
	libwnck-1.so.22 => /usr/lib/libwnck-1.so.22 (0xb7f61000)
	libgtk-x11-2.0.so.0 => /usr/lib/libgtk-x11-2.0.so.0 (0xb7be9000)
	libgdk-x11-2.0.so.0 => /usr/lib/libgdk-x11-2.0.so.0 (0xb7b65000)
	libatk-1.0.so.0 => /usr/lib/libatk-1.0.so.0 (0xb7b4b000)
	libgdk_pixbuf-2.0.so.0 => /usr/lib/libgdk_pixbuf-2.0.so.0 (0xb7b33000)
	libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7b0e000)
	libdecoration.so.0 => /usr/lib/libdecoration.so.0 (0xb7b06000)
	libXrender.so.1 => /usr/lib/libXrender.so.1 (0xb7afd000)
	libX11.so.6 => /usr/lib/libX11.so.6 (0xb7a16000)
	libpangocairo-1.0.so.0 => /usr/lib/libpangocairo-1.0.so.0 (0xb7a0d000)
	libpango-1.0.so.0 => /usr/lib/libpango-1.0.so.0 (0xb79d0000)
	libcairo.so.2 => /usr/lib/libcairo.so.2 (0xb796e000)
	libgobject-2.0.so.0 => /usr/lib/libgobject-2.0.so.0 (0xb7932000)
	libgmodule-2.0.so.0 => /usr/lib/libgmodule-2.0.so.0 (0xb792d000)
	libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7929000)
	libglib-2.0.so.0 => /usr/lib/libglib-2.0.so.0 (0xb7878000)
	libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7729000)
	libstartup-notification-1.so.0 => /usr/lib/libstartup-notification-1.so.0 (0xb7720000)
	libXRes.so.1 => /usr/lib/libXRes.so.1 (0xb771d000)
	libXcomposite.so.1 => /usr/lib/libXcomposite.so.1 (0xb771a000)
	libXdamage.so.1 => /usr/lib/libXdamage.so.1 (0xb7717000)
	libXfixes.so.3 => /usr/lib/libXfixes.so.3 (0xb7712000)
	libfontconfig.so.1 => /usr/lib/libfontconfig.so.1 (0xb76e8000)
	libXext.so.6 => /usr/lib/libXext.so.6 (0xb76d9000)
	libXinerama.so.1 => /usr/lib/libXinerama.so.1 (0xb76d6000)
	libXi.so.6 => /usr/lib/libXi.so.6 (0xb76ce000)
	libXrandr.so.2 => /usr/lib/libXrandr.so.2 (0xb76c8000)
	libXcursor.so.1 => /usr/lib/libXcursor.so.1 (0xb76bf000)
	/lib/ld-linux.so.2 (0xb7fb0000)
	libxcb-xlib.so.0 => /usr/lib/libxcb-xlib.so.0 (0xb76bc000)
	libxcb.so.1 => /usr/lib/libxcb.so.1 (0xb76a4000)
	libpangoft2-1.0.so.0 => /usr/lib/libpangoft2-1.0.so.0 (0xb767d000)
	libfreetype.so.6 => /usr/lib/libfreetype.so.6 (0xb7610000)
	libz.so.1 => /usr/lib/libz.so.1 (0xb75fb000)
	libpng12.so.0 => /usr/lib/libpng12.so.0 (0xb75d7000)
	libpixman-1.so.0 => /usr/lib/libpixman-1.so.0 (0xb75ae000)
	libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0xb74bb000)
	libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb74b0000)
	libselinux.so.1 => /lib/libselinux.so.1 (0xb7497000)
	libpcre.so.3 => /usr/lib/libpcre.so.3 (0xb746f000)
	libSM.so.6 => /usr/lib/libSM.so.6 (0xb7467000)
	libICE.so.6 => /usr/lib/libICE.so.6 (0xb744f000)
	libexpat.so.1 => /usr/lib/libexpat.so.1 (0xb742e000)
	libXau.so.6 => /usr/lib/libXau.so.6 (0xb742b000)
	libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0xb7425000)
	libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb740d000)

```

---

