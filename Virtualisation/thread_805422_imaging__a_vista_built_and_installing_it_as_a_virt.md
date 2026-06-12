---
title: "imaging  a vista built and installing it as a virtual machine ?"
date: 2008-05-23
forum: Virtualisation
---

### Post by donavan on 2008-05-23
Can you use *something like* a norton ghost image to install Vista as a guest OS. I have a ton of software and it will take me a  month to get everything setup the way I like/need it if I have to reinstall from scratch.  I am not familiar with the limitations or features of virtualization in linux I haven't made it that far yet. Still working on some of the more basic linux skills.

Also if this isn't a possibility can a VM be set up in such a way that I don't really ever see the OS desktop just the program in Linux window. I know I would be probably looking at just as much work as a reinstall, but I think it would be worth it.

---

### Post by dcstar on 2008-05-24
> **donavan said:**
> Can you use *something like* a norton ghost image to install Vista as a guest OS. I have a ton of software and it will take me a  month to get everything setup the way I like/need it if I have to reinstall from scratch.  I am not familiar with the limitations or features of virtualization in linux I haven't made it that far yet. Still working on some of the more basic linux skills.

Also if this isn't a possibility can a VM be set up in such a way that I don't really ever see the OS desktop just the program in Linux window. I know I would be probably looking at just as much work as a reinstall, but I think it would be worth it.

VMWare has a free utility to convert an existing installation into a VM.

---

### Post by Jose Catre-Vandis on 2008-05-24
I doubt whether Vista would like this very much, given all the "hardware" changes that would be made as it moved into a Virtual environment. However, it might work if you use VMware to do the conversion. You would be better off with a fresh install so that Vista optimises itself for the virtual environment. Then customise only for the things you really need :)

I would recommend VirtualBox as your VM program

You can set up your VM to run in the background and call applications from launchers. many threads on this on the forum. I prefer to run my vms in a seperate desktop.

---

### Post by zekopeko on 2008-05-24
> **Jose Catre-Vandis said:**
> 

You can set up your VM to run in the background and call applications from launchers. many threads on this on the forum. I prefer to run my vms in a seperate desktop.

could you point to one of this threads? thanks.

---

### Post by Jose Catre-Vandis on 2008-05-24
Here's one
[http://ubuntuforums.org/showthread.php?t=577897](http://ubuntuforums.org/showthread.php?t=577897)

VirtualBox and Vmware both offer seamless options, VBox by default, not sure about VMware

---

### Post by bradmkjr on 2008-05-24
Have you thought about using Wine?

You could mount the Vista partition in Ubuntu, then set it as the root for your wine configuration, and maybe able to run most of your applications with little difficulty. This isn't the prefered method, but I recomend looking into it before trying to virtualize Vista. 

If you do use a converter, or just mount the Vista as a drive in the virtual machine you will have to reauthorize it with Microsoft, and that means if you are trying to use a dual boot, it won't boot on the natural hardware again without reauthorizing that. If you duplicate it into a virtual machine, and use both the virtual machine and the normal hardware then you are violating the EULA, which is not legal.

Hope that makes sense,
Bradford Knowlton
[http://x86V.com](http://x86V.com)

---

### Post by donavan on 2008-05-24
First off thanks for all the tips.  I have looked into Vbox a little and I like the sound of it but I still don't know if I want to go that route yet, but it looks promising.  As I indicated before I was trying to get Wine working but I seem to be stuck.  I have tried installing office several times now and it just hangs on the install screen.  I checked for files to see if it was actually installing but not telling me, but its not.  I found somewhere that I need to install crossover games 7 (or something close to that)to get rpcrt4.dll however I have a copy of that on vista and copied it over because I couldn't get the crossover games to compile. That being said, will the idea of mounting the vista partition work? And the next question, is there a way to mount the vista partition inside of VMware...Remember the host is currently Vista and Ubuntu is running as the guest.  I want to test all this out virtually before I commit my computer to linux 100%.

---

