---
title: "Ubuntu Server with VMware question"
date: 2008-07-12
forum: Server Platforms
---

### Post by dbrine on 2008-07-12
Hope this is the right place to post this. I want to use my Ubuntu Server 8.04 and have virtual machines, like windows, other linux installs, etc. Is this possible in server edition with no GUI? I know I can do it with the desktop edition.

---

### Post by koenn on 2008-07-12
yes, it's possible.

---

### Post by windependence on 2008-07-12
Yes, you can either start the VMs at the command line, or access the Vmware console through another machine on port 902. The Vmware console takes care of the connection for you. You can also load the MUI and monitor your servers from a web browser on another machine. You do not have to be running a GUI on the server to do any of this.

-Tim

---

### Post by dbrine on 2008-07-12
tutorial(s) or how-to's? I'm still looking myself 2

---

### Post by Thirtysixway on 2008-07-13
I've also been looking for tutorials on this.  Everytime I've done it, the console on the 2nd machine get's a blank error when starting a virtual machine.

---

### Post by koenn on 2008-07-13
Here's a mini-howto :
[http://users.telenet.be/mydotcom/howto/linux/virtual.htm](http://users.telenet.be/mydotcom/howto/linux/virtual.htm)

Like windependence mentioned :
 you can start an ssh session on your server and start VM's from the command prompt.
You can also run the VMware console of the server and display it on a 2nd machine (ssh -X ... vmware ) : [http://users.telenet.be/mydotcom/howto/linux/xremote.htm#apps](http://users.telenet.be/mydotcom/howto/linux/xremote.htm#apps)

You can also use a browser to connect to the vmware web interface of a remote server, and 
You can install the vmware console separately and connect to remote vmware server. When I tried that, the seperate console tarbal lacked a few files, but you can work around that by installing the vmware server on a 2nd machine, and then only run the console to connect to a remote server. That was a few versions ago, it may have been fixed by now.

See also [http://ubuntuforums.org/showthread.php?t=840696](http://ubuntuforums.org/showthread.php?t=840696)

---

### Post by windependence on 2008-07-14
As of VMware 1.04, I have been able to load the console app on either a windows box or a Linux box and connect to the VMware server that way to graphically controll all the VMs. Works great.

Good tutorial from gdtaqua:

[http://ubuntuforums.org/showthread.php?t=826626](http://ubuntuforums.org/showthread.php?t=826626)

Another good one:

[http://users.piuha.net/martti/comp/ubuntu/en/server.html](http://users.piuha.net/martti/comp/ubuntu/en/server.html)

-Tim

---

### Post by sh4d0w808 on 2008-07-16
Hello Folks,

Are there any possibility to integrate vmware drivers to ubuntu server installer? Appreciate any help regarding this topic...

---

### Post by windependence on 2008-07-16
What do you mean by "drivers". There are no "drivers" to be installed using Vmware server on Linux.

-Tim

---

### Post by sh4d0w808 on 2008-07-16
:)

I told vmware drivers to ubuntu server, not vmware server in ubuntu :)

If U install an OS as guest in vmware, in most cases U have to install vmware additions - these are mostly drivers for network, for mouse and for VGA. I need the VGA driver at least to know by the guest ubuntu server. During the server installation I can select the vmware VGA but it looks doesn't work properly; i cannot change the screen resolution of the guest system, although i need this feature.

---

### Post by windependence on 2008-07-16
If you are using any operating systems except Windows as a guest you probably don't need drivers. Otherwise, just install vmware tools.

-Tim

---

### Post by sh4d0w808 on 2008-07-16
> **windependence said:**
> If you are using any operating systems except Windows as a guest you probably don't need drivers. Otherwise, just install vmware tools.

-Tim

In this case, can U pls help me, how to set up xorg? I tried 

[FONT="Lucida Console"]sudo dpkg-reconfigure xserver-xorg[/FONT]

without success; X was unable to start.

---

### Post by windependence on 2008-07-16
Is this on the host box or the guest box. On the guest box you should install Vmware tools also.

-Tim

---

### Post by sh4d0w808 on 2008-07-16
> **windependence said:**
> Is this on the host box or the guest box. On the guest box you should install Vmware tools also.

-Tim

Ooops, maybe some mismatch. So, I'd like to install Ubuntu server as guest with GUI (Gnome). I do not want to install ubuntu-desktop package, because it contains programs what I do not need. Instead of this, I installed gdm, gnome-core, xserver-xorg but the GUI is unable to start - and I think it is because of wrong X configuration.

---

### Post by windependence on 2008-07-16
Why not just use it as it was intended, without the GUI. You don't need it and it will be a bit heavy for a VM that way anyway. Learn some CLI, you'll be glad you did. Why do you think they don't install a GUI in the first place?

[http://www.ubuntu.com/products/whatisubuntu/serveredition/features/security](http://www.ubuntu.com/products/whatisubuntu/serveredition/features/security)

> **[SIZE="4"]No X server by design[/SIZE]**

By design, Ubuntu Server Edition does not include an X server. This is a deliberate choice as we believe that most servers should be serviced remotely, are safer without the addition of code that needs direct communication from user space to hardware, and should not be used as a desktop by their administrator. 

[I]"So I applaud the Ubuntu team’s common sense (and courage) in keeping the X Window System out of the default installation of Ubuntu Server."
--Mick Bauer in April 2008 Linux Journal - "Security Features in Ubuntu Server"[/I]

-Tim

---

### Post by sh4d0w808 on 2008-07-16
> **windependence said:**
> Why not just use it as it was intended, without the GUI. You don't need it and it will be a bit heavy for a VM that way anyway. Learn some CLI, you'll be glad you did. Why do you think they don't install a GUI in the first place?

[http://www.ubuntu.com/products/whatisubuntu/serveredition/features/security](http://www.ubuntu.com/products/whatisubuntu/serveredition/features/security)



-Tim

My target is to create an own Ubuntu (desktop) version; I have read an article about it, although that article describes to create customized Kubuntu. The idea behind the server installation is that it doesn't contain GUI and all of its' junk (eg. gnome-games, evolution and so on). It is strangeness: if I installed kdm and kde-core, it worked as designed. Gnome not...

---

### Post by windependence on 2008-07-16
There are numerous posts about adding a GUI to the server version. You can add the desktop with just one command, but I don't know how much junk it adds.

-Tim

---

### Post by sh4d0w808 on 2008-07-16
> **windependence said:**
> There are numerous posts about adding a GUI to the server version. You can add the desktop with just one command, but I don't know how much junk it adds.

-Tim

Then thank U very much for your time and answers, I will search rfor that topics. Have a nice day!

---

### Post by ryazkhan on 2008-07-16
> **windependence said:**
> As of VMware 1.04, I have been able to load the console app on either a windows box or a Linux box and connect to the VMware server that way to graphically controll all the VMs. Works great.

Good tutorial from gdtaqua:

[http://ubuntuforums.org/showthread.php?t=826626](http://ubuntuforums.org/showthread.php?t=826626)

Another good one:

[http://users.piuha.net/martti/comp/ubuntu/en/server.html](http://users.piuha.net/martti/comp/ubuntu/en/server.html)

-Tim

I have same setup in my home environment, I also have a quick how to about it just at [www.freetech.selfip.info/vmware.php](www.freetech.selfip.info/vmware.php)
let me know if you have any question/s

---

### Post by koenn on 2008-07-16
> **sh4d0w808 said:**
> ... I installed gdm, gnome-core, xserver-xorg but the GUI is unable to start - and I think it is because of wrong X configuration.

> **sh4d0w808 said:**
> ...  if I installed kdm and kde-core, it worked as designed. Gnome not...

If you got KDE working, your X configuration is probably ok. You probably missed some gnome components (gnome-panel, gnome-menus, ....) or something wjet wrong while setting up gnome.
Search for GUI + server threads, there's hundreds of them on these forums.

---

### Post by sh4d0w808 on 2008-07-26
> **koenn said:**
> If you got KDE working, your X configuration is probably ok. You probably missed some gnome components (gnome-panel, gnome-menus, ....) or something wjet wrong while setting up gnome.
Search for GUI + server threads, there's hundreds of them on these forums.

Thanks, the problem was that I had to install xfonts-base package separately.

---

