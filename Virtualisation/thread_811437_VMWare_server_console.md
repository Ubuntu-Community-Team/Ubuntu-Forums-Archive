---
title: "VMWare server console"
date: 2008-05-29
forum: Virtualisation
---

### Post by corrosion on 2008-05-29
Hi all,

I have a Debian stable server running VMware server edition. Stable version, no beta.
I simply want to use vmware server console from my laptop using ubuntu 8.04, without having to full install vmware server or having to compile anything on it. I want CLEAN system, using everything from sources.list. I do NOT want to modidy that list, so the option is like download the binary and run it from my /home directory. Other options are welcome, but the most clean the better.

---

### Post by Lem on 2008-05-29
On the download page for VMWare Server 1.05 are links for the client software only for linux and windows.

---

### Post by bradmkjr on 2008-05-29
VMware is closed source commercial software, therefor unlikely that it will be in the repositories. I know they have released Workstation demo and the free player into the partner repositories, but you still need to goto their website to get a key to activate it. If you want the cleanest install on the workstation, then do this.. **Don't install the server console**. Use VNC or SSH to access the server. You can run VMware server console on the server, then remotely access it from your laptop. This cuts down on the resources needed on your laptop, and if you choose to reload your laptop you will not need to reinstall server console. Also this makes the server easier to secure, as you don't need to open up extra holes in a firewall for the console software.

You could also use MUI. This is a web based administration which you can use to control the virtual server. If you are only planning on using prebuilt machines or only need ssh access to the vms this may  be enough for your needs. Search the forums or google for instructions and where to dwonload mui from.

If you still decided that you need the power of VMware Server Console then read my post for some help with issues which people have encountered recently:
[http://x86virtualization.com/diy-plans/howto-run-vmware-server-console-105-in-ubuntu-hardy-804.html](http://x86virtualization.com/diy-plans/howto-run-vmware-server-console-105-in-ubuntu-hardy-804.html)

Good Luck,
Bradford Knowlton
[http://x86Virtualization.com/](http://x86Virtualization.com/)

---

