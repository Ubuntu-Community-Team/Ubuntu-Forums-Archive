---
title: "VMWare Player GUI lost after logout"
date: 2008-09-23
forum: Virtualisation
---

### Post by kpictjl on 2008-09-23
I'm running VMWare player on top of Ubuntu 8.04.  I configured a mediawiki server inside a VM and all was well.  I logged out of my Ubuntu gnome host desktop and then logged back in.  Now I can't get back into the VMWare player GUI for console access to the virtual machine.

The vm is still running fine.  I proved this by hitting the mediawiki web page from another machine.  Also, top shows the vm chugging away.

How do I get the VMware player GUI back?

Call me the vmware noob.

---

### Post by Scunizi on 2008-09-23
If you're running the 2.0 Beta version of VmWare then you use Firefox to access the gui at http://localhost:<insert port #>  .. I've got mine set for 8080.

If you're running an earlier version of Server then there should be a menu item for it off of Applications someplace.

---

### Post by kpictjl on 2008-09-24
I can open vmware player from the gnome applications menu. That allows me to start new vms.   But what I can't do is make that instance of vmware player connect to the running virtual machine.

---

### Post by dodle on 2008-09-24
I'm not sure if this is something you want to do, but I like VirtualBox a lot better than VMWare.  If you haven't you might want to give that a try.

---

### Post by Scunizi on 2008-09-24
All I can say is if you loaded VMWare Player and not server (both of which are out of date in the repos) then I'm not sure how to fix what you've got going on.  You could do a couple of things, download and install either player or server directly from vmware or before doing that get on IRC using xChat or Pidgin (xChat is better) and then log on to irc.freenode.net and channel #vmware.  But I have to warn you that, that particular channel has some helpful people but most of them are data center types that have a hard time answering the basic questions and typically point you to the manual.

Vbox or virtual box also works quite well.  However to get it's new functionality, get it directly from the vbox site.  It won't be able to load vmware's appliances though from what I understand..

---

