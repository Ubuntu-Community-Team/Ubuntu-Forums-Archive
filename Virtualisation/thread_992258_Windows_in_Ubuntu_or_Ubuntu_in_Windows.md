---
title: "Windows in Ubuntu or Ubuntu in Windows"
date: 2008-11-24
forum: Virtualisation
---

### Post by ctopher2391 on 2008-11-24
I installed Ubuntu for the first time Thursday because I'm sick of windows vista.  Unfortunately, I don't think I can completely get rid of it due to itunes and iphone.  I'm currently dual booting, but I'm thinking about running one of them virtually through vmware.  Are there any pros/cons to doing either configuration?  I'm considering running ubuntu virtually in windows just due to ease of use, and my ignorance.  I'm obviously new to Linux, so it would be easier (for me) to set up vmware and ubuntu in windows.  I haven't really figured out the terminal yet, but that's one of the reasons Linux interests me, because I would like to, and it will force me to.  Any suggestions?

---

### Post by HermanAB on 2008-11-24
The easiest way to get going with virtualization is to install Virtualbox and then install WinXP in that.

I use VMware Workstation, but my needs are different from the ordinary.

Cheers,

H.

---

### Post by lkness on 2008-11-24
I run a Vista host with VM Server and a Ubuntu guest. If you are planning on using VM Server, i don't know if you will be happy. I have been unable to get my network to recognize the virtual machine, so i can't FTP, ssh, or telnet to it or from it to the other device. I do have a network connection to the internet from the vm, but that's about it. I worked on it for quite a while but could not resolve the issue, and i think the issue is rooted in Vista's security. The not-for-free VM Workstation may be better; i don't know.

---

### Post by jtheriot on 2008-11-24
I would suggest using VirtualBox instead of VMware.  There are no restrictions with VBox.

I've done both WinXP host and Ubuntu guest and Ubuntu Host and XP guest.  The better setup would be Ubuntu host and XP guest, but if you are inexperienced with Linux, then I would suggest XP host, Ubuntu guest.  Then when you are versed enough in Linux, make the switch.

Two of the biggest reasons I use Linux is xkill and the terminall kill ProcessID command.  This will kill any program or services running.  With M$ products, you are limited to what the taskmanager will allow you to do and then, most of the time, the processes won't quit.

I hope you enjoy your learning experience with Linux.  It really is the best OS around.

---

### Post by ctopher2391 on 2008-11-24
> **jtheriot said:**
> I would suggest using VirtualBox instead of VMware.  There are no restrictions with VBox.

I've done both WinXP host and Ubuntu guest and Ubuntu Host and XP guest.  The better setup would be Ubuntu host and XP guest, but if you are inexperienced with Linux, then I would suggest XP host, Ubuntu guest.  Then when you are versed enough in Linux, make the switch.

Two of the biggest reasons I use Linux is xkill and the terminall kill ProcessID command.  This will kill any program or services running.  With M$ products, you are limited to what the taskmanager will allow you to do and then, most of the time, the processes won't quit.

I hope you enjoy your learning experience with Linux.  It really is the best OS around.

I appreciate the feedback..I am loving Linux so far.  No crashing, no pop-ups saying "Windows has disabled startup programs" etc.  I was ready to trash Vista.  I've never had a problem with MS until now, after several reinstalls, and several irritating things I was ready for a switch.  For some reason a terminal scares the hell out of me..I guess I started using computers around Windows 95 time, so I just never really needed to do anything with it, but we'll see how it goes.  I decided to go Linux host with XP guest, I'm about to do the VMware install- I sell it so I have to use it :-)  It will actually be my first hands-on experience with it, so should be fun.  

I will say, one of my favorite things so far about Linux is the community.  Countless times on these forums I've seen a post beginning with "I'm a noob, so I know I'll get flamed", and every time the first response is "no flames, we're here to help."

---

### Post by houbysoft.xf.cz on 2008-11-24
I also think that Linux host/Windows guest is better because Linux is more secure than windows - so you can trust it and use as the host OS.

---

### Post by benhur99ph on 2008-11-24
I recommend using Ubuntu as your host OS and Windows XP as the guest.
I also recommend using VirtualBox because its pretty easy to get up and running. The other virtualization softwares work great too, but if you will only use it for iTunes and iPhone, VirtualBox is the way to go.

---

### Post by ctopher2391 on 2008-11-25
Well, it's getting late..I installed VMware server 2.0, logged into the console and created the VM.  I guess I inserted the XP disc too late, and couldn't figure out how to get into the VM to install the OS.  I restarted, and now I can't seem to get back to the console.  This is what I'm getting: 

Firefox can't establish a connection to the server at 127.0.0.1:8333.

When I successfully logged in I went ahead and did the security certificate exception, but now I can't get in.  Any ideas?

---

### Post by stinger30au on 2008-11-25
> **ctopher2391 said:**
> I installed Ubuntu for the first time Thursday because I'm sick of windows vista.  Unfortunately, I don't think I can completely get rid of it due to itunes and iphone.


you can ditch itunes

i run my sons ipod shuffle of 8.04 with rythymbox installed and it does it nicely

read bout it here

[http://live.gnome.org/Rhythmbox](http://live.gnome.org/Rhythmbox)

install from add/remove, find it under applcations

---

### Post by ctopher2391 on 2008-11-25
> **stinger30au said:**
> you can ditch itunes

i run my sons ipod shuffle of 8.04 with rythymbox installed and it does it nicely

read bout it here

[http://live.gnome.org/Rhythmbox](http://live.gnome.org/Rhythmbox)

install from add/remove, find it under applcations

I would like to, but I don't think I can..i have to run software updates, and I manage the apps through iTunes as well- I can just drag and drop into iTunes.

---

### Post by ctopher2391 on 2008-11-25
> **ctopher2391 said:**
> Well, it's getting late..I installed VMware server 2.0, logged into the console and created the VM.  I guess I inserted the XP disc too late, and couldn't figure out how to get into the VM to install the OS.  I restarted, and now I can't seem to get back to the console.  This is what I'm getting: 

Firefox can't establish a connection to the server at 127.0.0.1:8333.

When I successfully logged in I went ahead and did the security certificate exception, but now I can't get in.  Any ideas?

I guess this proved that I'm too accustomed to Windows, ie running everything at startup.  I'm thinking vmware isn't running, and i need to add a startup script?  

System \ Preferences\ Sessions right?

---

### Post by ctopher2391 on 2008-11-25
> **ctopher2391 said:**
> I guess this proved that I'm too accustomed to Windows, ie running everything at startup.  I'm thinking vmware isn't running, and i need to add a startup script?  

System \ Preferences\ Sessions right?

Well, I guess I don't want VM to start automatically every time, since it will hog resources.  What command would I use to start/stop when I want to use it?

---

### Post by ctopher2391 on 2008-11-25
Anyone?  :(

---

