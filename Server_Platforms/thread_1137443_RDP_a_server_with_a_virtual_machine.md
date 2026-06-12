---
title: "RDP a server with a virtual machine"
date: 2009-04-25
forum: Server Platforms
---

### Post by fenixbtc on 2009-04-25
hi,
so, i'm looking to set up a server with 9.04. i'm planning on possibly hosting a site on it and i want to also have the ability to do a RDP to access virtual machines on it.

my question is, in order to have either virtual machine or vmware server running and hosting other os', do i have to have the desktop installed on the actual server installation, or can i run it via command line and when i connect externally i can view a desktop on the virtual os'? being as this is a personal computer of mine at home, i thought i would try to keep it fairly secure by not installing the desktop package on the server, but i will if i need to. also, what are your preferences between virtualbox or vmware server?

thanks
david

---

### Post by Cheesemill on 2009-04-25
On my machines at work I run a base install of Ubuntu Server 8.04 and just install VMware on top, no need for a GUI.

VMware 2.0 has a web front end to manage it, all you need to do is point a browser at [https://machine_ip:8333/](https://machine_ip:8333/) and you can create and administrate VM's as well as firing up a remote connection to the machine's desktop.

Cheesemill

---

### Post by HermanAB on 2009-04-25
Howdy,

You can do everything over SSH, including running GUI based programs.

```
$ ssh -X -C -c blowfish user@server "vmware"
```

VMware is better with Windows Active X programs and Virtualbox is better with OpenGL based programs.  Otherwise they are pretty much the same.

---

### Post by fenixbtc on 2009-04-26
Cheesemill: when you administer a VM through the browser, does everything come across fairly static like a webpage, or will i get a fully functional desktop if i'm running a VM of windows or a desktop version of another os? or are you saying that you can fire up a RDP of a VM through the browser and it would run outside of the browser as a regular RDP?

HermanAB: if i'm accessing the server to do a RDP from a windows machine using SSH, does putty have the capabilities i need, or what would i use? having both VMWare and virtualbox installed and possibly running at the same time *shouldn't* cause any problems, right?

thanks for answering all the questions and sorry if i'm asking a lot. i'm fairly new to this and am trying to make a project for myself that is hopefully going to motivate me to learn a lot and get away from being so dependent on windows.

---

