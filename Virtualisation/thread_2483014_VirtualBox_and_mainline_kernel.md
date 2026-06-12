---
title: "VirtualBox and mainline kernel"
date: 2023-01-17
forum: Virtualisation
---

### Post by Eldar_Insafutdinov on 2023-01-17
Hi all,

I'm on Ubuntu 22.10 and I recently switched to a kernel 6.1 from mainline ppa because of its better support for AMD CPUs. However it doesn't seem to have built a right module for this kernel - when I reinstall VirtualBox .deb package downloaded from Oracle website nala output contains this:

[FONT=monospace][COLOR=#54ff54]**&#9474;Unpacking:**[/COLOR][COLOR=#000000]  linux-headers-generic [/COLOR][COLOR=#000000]**(**[/COLOR][COLOR=#5454ff]**5.19.0.29.26**[/COLOR][COLOR=#000000]**)**[/COLOR]
[COLOR=#54ff54]**&#9474;Setting up:**[/COLOR][COLOR=#000000] linux-headers-generic [/COLOR][COLOR=#000000]**(**[/COLOR][COLOR=#5454ff]**5.19.0.29.26**[/COLOR][COLOR=#000000]**)**[/COLOR]

As far as I can tell it builds a module for the original kernel in the main repositories. Is there any way to tell it to build a module for the mainline kernel?

Cheers.
[/FONT]

---

### Post by lammert-nijhof on 2023-01-17
Download Virtualbox from its official site 'virtualbox.org' and download the newest version 7.06. That one has initial support for kernel 6.1 since Virtualbox 7.02 and 6.2 since 7.06.

---

### Post by Eldar_Insafutdinov on 2023-01-18
Yes, I am using 7.06 from their website. I think the issue is that it uses linux-headers-generic package to build the module and those point to the old kernel.

---

