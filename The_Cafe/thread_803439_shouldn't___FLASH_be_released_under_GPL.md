---
title: "shouldn't   FLASH be released under GPL ?"
date: 2008-05-22
forum: The Cafe
---

### Post by arkangel on 2008-05-22
Hi  

I did  a ldd to the flash plug-in  and this library is linked with the following lib:
       linux-gate.so.1 =>  (0xb7ef6000)
	libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0xb739d000)
	libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7385000)
	libX11.so.6 => /usr/lib/libX11.so.6 (0xb729d000)
	libXext.so.6 => /usr/lib/libXext.so.6 (0xb728f000)
	libXt.so.6 => /usr/lib/libXt.so.6 (0xb723e000)
	libfreetype.so.6 => /usr/lib/libfreetype.so.6 (0xb71ce000)
	libfontconfig.so.1 => /usr/lib/libfontconfig.so.1 (0xb71a4000)
	libgtk-x11-2.0.so.0 => /usr/lib/libgtk-x11-2.0.so.0 (0xb6e2d000)
	libgdk-x11-2.0.so.0 => /usr/lib/libgdk-x11-2.0.so.0 (0xb6da8000)
	libatk-1.0.so.0 => /usr/lib/libatk-1.0.so.0 (0xb6d8e000)
	libgdk_pixbuf-2.0.so.0 => /usr/lib/libgdk_pixbuf-2.0.so.0 (0xb6d76000)
	libpangoxft-1.0.so.0 => /usr/lib/libpangoxft-1.0.so.0 (0xb6d6f000)
	libpangox-1.0.so.0 => /usr/lib/libpangox-1.0.so.0 (0xb6d64000)
	libpango-1.0.so.0 => /usr/lib/libpango-1.0.so.0 (0xb6d26000)
	libgobject-2.0.so.0 => /usr/lib/libgobject-2.0.so.0 (0xb6cea000)
	libgmodule-2.0.so.0 => /usr/lib/libgmodule-2.0.so.0 (0xb6ce6000)
	libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb6ce2000)
	libglib-2.0.so.0 => /usr/lib/libglib-2.0.so.0 (0xb6c31000)
	libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb6c0c000)
	libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb6c00000)
	libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb6ab1000)
	/lib/ld-linux.so.2 (0xb7ef7000)
	libxcb-xlib.so.0 => /usr/lib/libxcb-xlib.so.0 (0xb6aaf000)
	libxcb.so.1 => /usr/lib/libxcb.so.1 (0xb6a97000)
	libXau.so.6 => /usr/lib/libXau.so.6 (0xb6a94000)
	libSM.so.6 => /usr/lib/libSM.so.6 (0xb6a8b000)
	libICE.so.6 => /usr/lib/libICE.so.6 (0xb6a73000)
	libz.so.1 => /usr/lib/libz.so.1 (0xb6a5e000)
	libexpat.so.1 => /usr/lib/libexpat.so.1 (0xb6a3d000)
	libpangocairo-1.0.so.0 => /usr/lib/libpangocairo-1.0.so.0 (0xb6a34000)
	libXcomposite.so.1 => /usr/lib/libXcomposite.so.1 (0xb6a30000)
	libXdamage.so.1 => /usr/lib/libXdamage.so.1 (0xb6a2d000)
	libXfixes.so.3 => /usr/lib/libXfixes.so.3 (0xb6a28000)
	libcairo.so.2 => /usr/lib/libcairo.so.2 (0xb69c6000)
	libXrender.so.1 => /usr/lib/libXrender.so.1 (0xb69be000)
	libXinerama.so.1 => /usr/lib/libXinerama.so.1 (0xb69ba000)
	libXi.so.6 => /usr/lib/libXi.so.6 (0xb69b2000)
	libXrandr.so.2 => /usr/lib/libXrandr.so.2 (0xb69ac000)
	libXcursor.so.1 => /usr/lib/libXcursor.so.1 (0xb69a3000)
	libpangoft2-1.0.so.0 => /usr/lib/libpangoft2-1.0.so.0 (0xb697c000)
	libXft.so.2 => /usr/lib/libXft.so.2 (0xb6969000)
	libselinux.so.1 => /lib/libselinux.so.1 (0xb6950000)
	libpcre.so.3 => /usr/lib/libpcre.so.3 (0xb6929000)
	libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0xb6924000)
	libpng12.so.0 => /usr/lib/libpng12.so.0 (0xb6900000)
	libpixman-1.so.0 => /usr/lib/libpixman-1.so.0 (0xb68d7000)
 
One of these had to be released under GPL and GPL only   , if that is the case ,  the plugin is derived work and should be released with a GPL , or am I wrong ?

---

### Post by geoken on 2008-05-22
I think you need to redifine your definition of derived. Making an app that takes advantage of a library is not a derivitive. Taking that library, slightly modyfing it, then redistributing it or compiling it into your app would constitute a derivitive.

---

### Post by wdaniels on 2008-05-22
As far as I know it's still a matter of contention. The FSF seems to use a much stronger interpretation than is generally accepted. As I understand it, the debate comes down to dynamic linking, or specifically, who is legally considered to be doing the linking in that case, the end-user (who has the right to under the GPL) or the developer (who does not). The FSF says [the developer is doing the linking]("http://www.fsf.org/licensing/licenses/gpl-faq.html#IfLibraryIsGPL") "because the program as it is actually run includes the library".

But in any case, the GPL cannot claim copyright over or impose licenses on non-GPL'd code (this is explicitly stated in the license) so if somebody wanted to make a legal challenge, all that could happen is that Adobe could be prevented from distributing a version of Flash which dynamically links to GPL'd libraries. Only the copyright holders of the GPL'd libraries have the power to do that, and I don't see anyone having a reason to want to.

It all gets very messy very quickly, with the question about linking, the definition of derived works, system library exceptions, modules & plugins etc...I am not a lawyer, but I'm not sure it would help if I were! Without legal precedent, it's anyone's guess. Plenty of people will tell you, often with some legal credibility, definitely one way or the other on this, but I always take it with a pinch of salt. I'm probably mistaken myself on some point or another since I lost interest in the matter years ago, but this is what I remember for whatever it's worth.

---

### Post by saulgoode on 2008-05-22
I don't believe any of those libraries are licensed under the GPL.

---

### Post by swoll1980 on 2008-05-22
Only if adobe decides it's the right thing for them to do

---

### Post by wdaniels on 2008-05-22
> **saulgoode said:**
> I don't believe any of those libraries are licensed under the GPL.

Yes, I think you're right - mostly LGPL and BSD. I thought libcairo at least was GPL, but it's not. No doubt someone will check for sure, but seems like Adobe weren't taking any chances after all :)

---

