---
title: "Ubuntu Server won't find any partition."
date: 2019-01-03
forum: Virtualisation
---

### Post by alangme on 2019-01-03
I wanted to run Ubuntu Server in a virtual machine along Windows Server just to test whether it'd be possible with the purpose of doing it later in a notebook. I had made dual boot installs previously with normal versions of both softwares... but Ubuntu Server is giving me a serious headache! No matter whether I have more than one NTFS partition free, a single partition and some free space, or a NTFS partition and an EXT4 one (made with [COLOR=#373737][FONT=&amp]Eassos PartitionGuru), the installer will only give me the option to erase the entire disk (scrapping all my Windows data) and format the disk as EXT4!

I even tried to make a Live USB to avoid having to erase my data, but it seems impossible cause all i can get with tools like UnetBootin is a normal USB installer. Even if I try to use a disk with Ubuntu Server and try to see whether I can install it on the pendrive, the only drive available is the HDD! At this time I'm starting to feel as if this OS'd have been designed by some sort of egocentric sadist (I know it's an exaggeration but I'm getting on my nerves). 

I had even seen some posts talking about using the Terminal but they were all for normal Ubuntu. I can't get any idea if it's even possible to install it along Windows now (not even another Linux distro taking into account it didn't detect an EXT4 partition) and I get it's meant to be installed in a server and all... but Windows Server can be installed in a normal partition as nothing!

EDIT: Solved, see last answer.[/FONT][/COLOR]

---

### Post by wildmanne39 on 2019-01-03
Hello, a virtual machine will run inside windows and not along side windows, for example I use virtualbox to run vm's and inside virtualbox the option is always to erase the whole disk if I have other virtual OS's in my virtualbox but it is a virtual disk in the virtual environment so it does not actually touch your physical hard drive, I suggest you post what virtualisation software you are trying to use like virtualbox for example, it does not sound like you are doing a virtual install and I am not sure about running a virtual OS inside a server, I am going to give you a link to virtualbox so you can get a better idea of virtualisation.

You can install a dual boot along side windows if that is what you mean? I have a suspicion that you are not actually doing a virtual install.

[https://www.virtualbox.org/](https://www.virtualbox.org/)

Thread moved to virtualization!

---

### Post by alangme on 2019-01-03
Hello, some clarifications before I continue:

1: I'm not running Ubuntu Server as a standalone OS inside a VM, I was trying to run it along Windows Server 2016 inside a VM running on VMware on Windows 10.
2: The reason for such thing is that I want to be able to bring both OS inside a notebook to be able to give classes about OSs (I'm a teacher in a high school) and since no computer there's powerful enough to run Windows Server 2016 and I want to introduce my students to both NOS that is practically the only option I have to be able to show them both NOS without having to use videos or another non interactive way by bringing my own note that can withstand both OS.
3: And since that computer already has Windows I was trying it on a VM to avoid anything that could end up breaking that notebook.
4: Thus as I already have Windows installed there, I can't alter the install order. I can only install Ubuntu after Windows.

---

### Post by wildmanne39 on 2019-01-03
Okay that makes more sense, it is getting very late here and I am going offline soon so hopefully someone will jump in here and help you get this issue sorted.

---

### Post by spjackson on 2019-01-03
I exclusively use Virtual Box for all my VM needs these days: it is many  years since I used VMware and I doubt that I can help. However, I would  like to point out that it seems to me that installing 2 OS inside one  VM is an atypical use case. The normal thing to do would be to create a  separate VM for each OS that you want to teach about. The only reason I  could think of for dual-booting a VM would be specifically for teaching  about dual-booting. That being said, I can't think why installing Linux  as a 2nd OS inside a dual-booting VM would not work... providing there's  room for it.

---

### Post by alangme on 2019-01-03
Hello spjackson, the issue is that I'm doing that in a VM only for testing purposes. I'm planning to install Ubuntu Server in a notebook of mine that already has Windows installed.

---

### Post by alangme on 2019-01-03
I finally found a solution! It did require to think outside of the box a little but managed to solve the issue. What I actually did was installing Ubuntu Desktop and then "upgrade" it to Ubuntu Server.

1: First I opened Windows and reduced the size of the main partition (removed approximately 30Gbs).
2: Then I installed Ubuntu Desktop as normal (Didn't create a new partition at all, just followed the normal step-by-step)
3: When I turned on the VM again, I had Ubuntu along Windows Server.
4: Then I opened the Terminal and run the updating process (sudo apt-get update), had to restart the VM to continue with the following steps.
6: I opened a new terminal and installed tasksel (sudo apt-get tasksel).
7: Then I executed it (sudo tasksel) and scrolled down to Basic Ubuntu Server, selected it with Space, pressed Tab and confirmed with Enter (was a simple thing but I was so sure I'd have to check with Enter instead of Space it took me some time to continue).

And now I've got the server functions along Windows... jeez it was complicated, guess there's no actually a way to install it along Windows... (at least installing Windows first). But upgrading Desktop to have the same functions is a totally acceptable alternative (that took some extra time than expected, several things were rather anti-intuitive, at least for a most-of-the-time Windows user). 

Can't yet understand why Ubuntu Server wont detect no partitions be them NTFS or EXT4. Were you to want to save data putting them in partitions you'd have to move it elsewhere... quite unpractical to say the least.

---

