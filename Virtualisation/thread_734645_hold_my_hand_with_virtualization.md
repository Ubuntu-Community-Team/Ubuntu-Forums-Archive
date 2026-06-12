---
title: "hold my hand with virtualization"
date: 2008-03-24
forum: Virtualisation
---

### Post by zorkerz on 2008-03-24
Ive been trying wrap my head around virtualized environments but have not found the sources for me to fully grasp it yet. 

I want to run xp from within ubuntu primarily for excel and a few other programs. I would love to be able test/run some games (warcraft 3, civ 4), i understand there are performance hits to this.

Im running hardy 64 bit. 

I don't know where to start. What virtualization to use? Ive searched around and found alot of information but no direction. Im sure there are links around i just have not found them. 

What advice can you all give?

---

### Post by shad0w_walker on 2008-03-24
My recommendation would be for Virtualbox, it has brilliant performance and if you don't mind the lack of a direct USB access (Not especially useful for most things) then the opensourced version is in the repos. There is also a .deb file on their official website so it's nice and easy to get setup.

Excel and the like shouldn't be a problem to run, but games are pretty much a no go. Aside from the large performance hit you would get they require 3d acceleration, which is still highly experimental in the virtualisation world, even the commercial programs still haven't got it going to a decent level.

---

### Post by diegosouza on 2008-03-24
Take a look: [https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

Don't mind about networking and wireless networking sections, I think you wouldn't need it.

Try to install the Guest Additions, it makes difference, but don't think you have good 3D video processing.

---

### Post by zorkerz on 2008-03-24
thanks alot ill give virtualbox a try

---

### Post by evilc on 2008-03-25
I am new to virtualization, but installed vmware to try, been using it for a week and have found it easy to use. Haven't had any problems with usb, sounds or video. I have even networked between xp (vm) and ubuntu, if I can do it then anyone can.:lolflag:

---

### Post by diegosouza on 2008-03-25
It's very easy to use both (vmware and virtualbox).
When I installed vmware inside the ubuntu 7.04 (feisty), there was a boring thing, I had to recompile something I don't remember (I think it was vmware module) when kernel update was released.

I don't know how it is nowadays, if somebody knows, please tell me   :-)

---

### Post by fjgaude on 2008-03-25
Well, nothing has changed when a kernel update occurs: you have to run vmware-config.pl again... no big deal when you consider just what features you have and the power of VM.

---

### Post by zorkerz on 2008-03-25
so how do vmware and virtualbox differ?

---

### Post by fjgaude on 2008-03-25
The only real significant difference for me is the ability to copy, cut, paste from Ubuntu to WinXP and back again, without issue. This VMware can do, and from last I saw, VBox cannot.

Speed, quickness is about the same. VBox does have an open source edition. VMware Player and Server are free, but not open.

I feel VMware Server is more mature, but this is my opinion, after using both on the same computer for about two months. Notice my signature.

---

### Post by zorkerz on 2008-03-25
well unless someone strongly argues otherwise i think i will give virtualbox a try first. I must admit i have heard more about vmware overall and it does sound like it might have advantages. vmware not being opensource seriously detracts from its long term value for me. 

Face value they can both be used for free but the level of community involvement is usually very restricted when not open source. Plus anything could happen to the code base in the future.

Id love to keep hearing peoples input. Ill also post about how thing go for me (though its not too high on my list of things to do yet).

---

### Post by kellemes on 2008-03-25
I have very good experiences with Virtualbox, very easy to setup and performance close to native.
Don't forget the virtualbox guest additions.

---

### Post by zorkerz on 2008-03-25
There are many instructions for installing virtualbox, however, none seem to be hardy specific. Ive been reading through the instructions at [https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox) for feisty. Should I do anything differently? This is a 64 bit computer and hardy installation if that makes a difference.

---

### Post by kellemes on 2008-03-25
> **zorkerz said:**
> There are many instructions for installing virtualbox, however, none seem to be hardy specific. Ive been reading through the instructions at [https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox) for feisty. Should I do anything differently? This is a 64 bit computer and hardy installation if that makes a difference.

I'm on Debian myself so I simply added the virtualbox repository..
I use the binary (non open source) version since it ads a couple of features I want.
For Ubuntu you can simply download the binary-version from here.. [http://www.virtualbox.org/wiki/Downloads]("http://www.virtualbox.org/wiki/Downloads")
and install using your preferred package-management tool.

---

### Post by fjgaude on 2008-03-25
I have vmware server installed in hardy beta, but it wasn't simple. So, I can't say what it might take for VBox.

---

### Post by kellemes on 2008-03-25
> **zorkerz said:**
> There are many instructions for installing virtualbox, however, none seem to be hardy specific. Ive been reading through the instructions at [https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox) for feisty. Should I do anything differently? This is a 64 bit computer and hardy installation if that makes a difference.

It seems you can use the Debian repository..
[http://ubuntuforums.org/showthread.php?t=598414]("http://ubuntuforums.org/showthread.php?t=598414")

---

### Post by zorkerz on 2008-03-25
virtualbox-ose is in the hardy repos also. It looks like it is the newest version 1.5.6 with some ubuntu customizations (full version 1.5.6-dfsg-2ubuntu2).

I think i will start there im just not sure what other packages I will need yet.

Update: here is what i did
```
sudo apt-get install virtualbox-ose virtualbox-ose-modules-2.6.24-12-generic
```
Then I added myself to the group vboxusers and followed the normal instructions from the link above and was able to setup xp. All took less than 30 minutes. This is awsome.

Thanks all.

---

### Post by zorkerz on 2008-03-25
[LEFT]So i have discovered one problem with my second step to instalation(although i edited it out above already so as not to confuse others). Every time I reboot or login (not sure which) ubuntu the /dev/vboxdrv owner gets set back to root. When this file is not owned by the current user I get the following error whenever trying to enter a virtual os.
> VirtualBox - Error
Failed to start the virtual machine
The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).

Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}any ideas how to avoid changing the owner of /dev/vboxdrv all the time?

Update Solved: check out [here.]("http://ubuntuforums.org/showthread.php?t=486355") I needed to simply add myself to the group **vboxusers** (system->administration->users/groups->managegroups->properties of group vboxusers and check my username)
[/LEFT]

---

### Post by trnt94 on 2008-03-25
Go system-admin-users and groups-manage groups- vboxusers-properties and add your name.

---

