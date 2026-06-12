---
title: "XP on ubuntu"
date: 2007-12-28
forum: Virtualisation
---

### Post by ronb94 on 2007-12-28
hello
 i want to try xp in ubuntu instead of dualbooting.
i have some questions:
1.I saw that there are many virualization programs,what is the best?
2.what i'll able to do with the xp(play?,adobe cs3?,ather programs?).
3.i need to install windows on ubuntu?there will be a folder in my ubuntu that will emulate partition?
4.i'll need to install drivers?
 Thank you and sorry for the bad english:)

---

### Post by theZoid on 2007-12-28
I'm running XP Pro in Ubuntu 7.10 using VMware Server.  You can install it through the synaptic package manager, just make sure you have 3rd party programs enabled.  The install is pretty brainless.  I've never used Virtual Box.  Install it to anwer many of your questions.  I run XP because of a couple of business programs I need (work out of my house).

---

### Post by bernied on 2007-12-28
1 - I've used vmware-server and virtualbox-ose. Each has its own strengths. I would not say that either is better. Try one and see.

2 - You will not get 3D graphics acceleration - so forget about playing any graphics-intensive games. Otherwise you should be able to run anything, providing you allocate enough resources to the virtual machine

3 - The virtualisation program will create a 'virtual disk image' for you, in a location of your choosing.

4 - The host will emulate a basic PC. Both virtualbox and vmware offer guest OS tools for windows. These are drivers that will improve on the basic PC setup, especially for screen resolution and mouse behaviour. Networking should be straightforward.

You will notice a reduction in speed while running inside a virtual machine, and it will impact on the host as well - you will be giving memory and cpu time to the guest operating system.

Your english is better than may native speakers - you don't need to apologise.

---

### Post by tajreed on 2007-12-28
VMware seems to take less processor time with XP than does VB. At least on my machine.

---

### Post by ronb94 on 2007-12-28
Thank you for answers:)
when u telling reduction in speed u mean just in the virtual OS? or my ubuntu will be slower too?
My xp will be in virtual disk so it will not taking disk space?and what about programs?
And what about internet? would i connect to the internet?
Thanks again:popcorn:

---

### Post by bernied on 2007-12-28
Yes, the VM can slow down both your ubuntu (host) as well as the windows (guest). The PC resources are being shared between two different operating systems, so this is inevitable. If you have a fast machine, it might not be noticeable, but it is for me.

The virtual disk will certainly take up disk space. You will have to decide how much space to allocate when you create the virtual machine. But it will be a single file, or a group of files, on a directory in an actual partition, not an actual partition itself. That is the meaning of 'virtual' in this context.

Both vmware and virtualbox handle network and internet connections for you - providing that your host (ubuntu) machine has internet already. So yes, you will have internet access from within the virtual machine. You will have some options for how networking is done, you may need to know something about your current internet connection to get this right.

Just in case you haven't already thought of this, you need to also consider the licence needed to run Windows. Windows has various ways of ensuring that you have a 'legitimate copy' of the operating system, meaning that you hold a valid licence. Since a single licence can usually only be used on a single machine, and a virtual machine is not considered to be the same as the host, this may mean that you need two different licences for both the virtual machine, and the actual machine, if you want to retain the option of dual-booting. This might be a problem if you use your licence code from your existing windows install. The install on the hard drive might complain next time you boot it and download any updates.

There are various ways around this problem, but I don't know if any are legal. You might want to read the terms of your microsoft licence. If you can afford a second windows licence then this does not matter.

---

### Post by ronb94 on 2007-12-28
the virtual disk will take the real disk space? i mean if my xp is 10GB so the virtual disk will take 10GB?

---

### Post by theZoid on 2007-12-28
> **ronb94 said:**
> the virtual disk will take the real disk space? i mean if my xp is 10GB so the virtual disk will take 10GB?

Yes.  With VMware Server, I just set the max to allow for the diskspace, but don't preallocated so it grows as I install programs.  I don't notice performance degradation myself, laptop specs in sig.

---

### Post by dcstar on 2007-12-29
> **bernied said:**
> 
...........
3 - The virtualisation program will create a 'virtual disk image' for you, in a location of your choosing.
...........
You will notice a reduction in speed while running inside a virtual machine, and it will impact on the host as well - you will be giving memory and cpu time to the guest operating system.
...........

I have just set up vmware server and installed my XP Home system inside of it, here are some tips from my experience (that may already be known generally):

[LIST=1]
[*]Set up a separate partition for your Vmware images - I set up a ReiserFS partition after I found that the FAT32 that I originally used was so slow - the new one is much (much) faster when vmware uses it!
[*]You can download a free (Windows) utility from the vmware site to fully import your existing Windows system into a vm - all your setup and installed programs will be there!
[*]Find (on the 'net) instructions on how to optimise Windows for a vm environment - this can help with performance.
[/LIST]

All in all I now have access to XP inside my Ubuntu system far more conveniently than with dual boot, and it performs well enough for my purposes.

---

### Post by theZoid on 2007-12-29
> **dcstar said:**
> I have just set up vmware server and installed my XP Home system inside of it, here are some tips from my experience (that may already be known generally):

[LIST=1]
[*]Set up a separate partition for your Vmware images - I set up a ReiserFS partition after I found that the FAT32 that I originally used was so slow - the new one is much (much) faster when vmware uses it!
[*]You can download a free (Windows) utility from the vmware site to fully import your existing Windows system into a vm - all your setup and installed programs will be there!
[*]Find (on the 'net) instructions on how to optimise Windows for a vm environment - this can help with performance.
[/LIST]

All in all I now have access to XP inside my Ubuntu system far more conveniently than with dual boot, and it performs well enough for my purposes.

VMware Server is slick.  Thanks for the tips...didn't know about that windows utility.  I've never used VirtualBox.

---

### Post by ronb94 on 2007-12-29
Thanks for tips i'll try them later.
i download the  vmware version 2 beta and i had much problem in installation so i download the normal version(not beta) 1.04.
my question is there a lot of differance between the beta and 1.04 versions? what should i use?

---

### Post by ronb94 on 2007-12-29
I installed the 1.04 version and configured a virtual machine but when i press power on i am getting this messege:
[IMG]http://img338.imageshack.us/img338/4352/screenshotwindowsxpprofse0.png[/IMG]

---

### Post by fjgaude on 2007-12-30
When you installed the WindowsXP did it install as it would when doing it to a regular hard drive?

---

### Post by ronb94 on 2007-12-30
i didnt installed windows xp i just configured the virtual machine but it wont start for installing xp

---

### Post by fjgaude on 2007-12-30
Strange, it seems the configuration file is in your /home directory. Did you move it there?

---

### Post by ronb94 on 2007-12-30
in the install i in mistake chosed to install the binary files(i am not sure its the binary files) in my /home directory.
how can i uninstall the program and install with default setting ?

---

### Post by fjgaude on 2007-12-30
Okay, the only way I've seen an uninstall work, at least for me, was to use Synaptic.

In Synaptic do a Search for vmware. Then click the Status bar near the bottom, left of the windows. When vmware-server shows from the search, click on it and go down and click on Mark for Complete Removal. After that happens, reinstall by clicking to install vmware-server.

---

### Post by ronb94 on 2007-12-30
ok synaptic even showing that vmware is not installed:confused::confused::confused:

---

### Post by fjgaude on 2007-12-30
All right, you installed using the package from the vmware web site.

Go ahead and use apt-get

```
sudo apt-get uninstall vmware
```

and see it that works. You might have to use vmware-server as a program name. Then install using Synaptic or apt-get. Use all the defaults on installing. You can use the same original license number you have.

---

### Post by ronb94 on 2007-12-30
its showing:
E: Invalid operation uninstall
i writed uninstall propaly what the problem?

---

### Post by fjgaude on 2007-12-30
I'm sorry... use "remove" for install.

---

### Post by ronb94 on 2007-12-30
:(
E: Couldn't find package vmware
:confused:

---

### Post by fjgaude on 2007-12-30
Try vmware-server.

If that doesn't work, go into your package that had VMware-server-1.0.4, in the folder vmware-server-distrib/bin you will find an uninstall script. In a terminal cd over to the folder and run the script:

```
sudo ./ vmware-uninstall.pl
```

That's about it for me... no more suggestions.

You might try reading this post:

[http://www.blog.arun-prabha.com/2007...box-in-ubuntu/](http://www.blog.arun-prabha.com/2007...box-in-ubuntu/)

---

### Post by ronb94 on 2007-12-30
sudo apt-get remove vmware-server gave me this:
Package vmware-server is not installed, so not removed
i am going to try the other ways and tell if its works

---

### Post by ronb94 on 2007-12-30
> **fjgaude said:**
> Strange, it seems the configuration file is in your /home directory. Did you move it there?

the only thing i changed is i putted the virtual OS in my /home.
i cant uninstall i cant just install from the begging but this option is coming by default(after the first time i changed) to /home/vmware.and i dont know what was the default before.
what should i do? how to uninstall this vmware?

---

### Post by fjgaude on 2007-12-30
Okay, what happened to the package you downloaded from vmware.com? Where is it?

---

### Post by ronb94 on 2007-12-30
i still have it i have the .tar.gz file and the extracted files in /tmp.

---

### Post by fjgaude on 2007-12-30
Okay, as I pointed to before. Go in and find the uninstall.pl file and run it. That will uninstall vmware. It's in the /vmware-server-distrib/bin directory.

---

### Post by cmat on 2007-12-30
I just started playing with VirtualBox today. XP ran very well and I plan on running office 2007 on it soon. OpenOffice is great but dyslexia is difficult to deal with without a built in grammar checker. VirtualBox has plenty of options and the one in the repos is open sourced.

---

### Post by dcstar on 2007-12-31
> **ronb94 said:**
> I installed the 1.04 version and configured a virtual machine but when i press power on i am getting this messege:
[IMG]http://img338.imageshack.us/img338/4352/screenshotwindowsxpprofse0.png[/IMG]

The screenshot seems to indicate that you have directly connected to your existing XP install, you must keep in mind that the VM environment is different to the physical hardware environment that the XP is configured for - this may be a big part of your problem.

I would advise booting XP and creating a new hardware profile for vm use, and then using the VMWARE convert utility to create a vm of the existing XP partition and using that.

Here are some links that may be of assistance:

[http://www.vmware.com/support/ws4/doc/disks_profiles_ws.html](http://www.vmware.com/support/ws4/doc/disks_profiles_ws.html)
[http://blogs.ipona.com/dan/archive/2007/08/22/8419.aspx](http://blogs.ipona.com/dan/archive/2007/08/22/8419.aspx)

---

### Post by ronb94 on 2007-12-31
Thank you guys i uninstalled and installed it again and its works.but now i have another question:
how can i move files from ubuntu(host) to the xp(vmware) and from xo to ubuntu?

---

### Post by fjgaude on 2007-12-31
The way I do it is through the NAT connection, and use SAMBA shares. Setup shares in Ubuntu and then use Windows Explorer to go to the shares.

---

### Post by ronb94 on 2007-12-31
ok i installed samba and configured share folder.now how i direct this folder with xp?

---

### Post by fjgaude on 2007-12-31
In Windows Explorer go to Network, then click on Entire Network, then click on Microsoft Windows Network, then click on WORKGROUP or whatever you set the share General features to. I think it might have defaulted to MSGROUP or something like that. Can't remember.

Let us know if you get to where you wish to go.

---

### Post by ronb94 on 2007-12-31
you mean My network places?

---

### Post by fjgaude on 2007-12-31
Yes.

---

### Post by ronb94 on 2007-12-31
i dont have nothing in My network places. when i  click on "view workgroup computer" i get this:
[IMG]http://img297.imageshack.us/img297/5670/screenshot1zc1.png[/IMG]

---

### Post by fjgaude on 2007-12-31
Ron, you are getting close... have you rebooted your computer since you installed the shares? If not, do so.

Can you access the Internet using Windows Explorer? Have you updated Windows since you installed it in VMware?

---

### Post by fjgaude on 2007-12-31
One more thing: I forgot to tell you to set the password for SAMBA like so:

```
sudo smbpasswd -a ron
```

This adds your name to smb and permits Windows to see the shares you setup in Ubuntu.

---

### Post by ronb94 on 2007-12-31
Thank you for your help:)
i did everything you told me (i rebooted nad updated windows) and i can acees internet with the windows explorer but still there is nothing in My Network Places.

---

### Post by fjgaude on 2007-12-31
Did you:

```
sudo smbpasswd -a ron
```

yet?

---

### Post by bharadwaj on 2007-12-31
how abt trying emulation software like codeweavers crossoverX play windows apps like you do normally

---

### Post by fjgaude on 2007-12-31
For one, Codeweaver doesn't run the software I use for graphic design. Note my signature.

---

### Post by ronb94 on 2007-12-31
i found the anser here:
[http://2tap.com/2007/04/22/sharing-files-between-a-windows-guest-and-ubuntu-host-using-vmware-and-samba](http://2tap.com/2007/04/22/sharing-files-between-a-windows-guest-and-ubuntu-host-using-vmware-and-samba)
thank you for helping!!:)

---

### Post by fjgaude on 2007-12-31
Very good, glad you got it. I'll read the how-to and use it to help others.

Thanks for hanging in there with us.

Happy New year!

---

