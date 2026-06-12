---
title: "Can someone proof my theory and code sample please?"
date: 2011-06-25
forum: Virtualisation
---

### Post by ClientAlive on 2011-06-25
Recently I went through a lot of trouble to learn to p2v my o/s into Virtual Box. Eventually I was successful but I'm not sure I went about it in the best or most efficient way. This experience has still got me thinking about possibly better ways to do that. I realize there are probably many options (both tried and untried) but there is one in particular I would like to focus on. What I'm wondering is if (1) my theory holds any water; and (2) whether the code sample I'm about to give for it is on track, needs something added, something removed, something changed, etc.

Thanks in advance for taking the time to look at this and share your knowledge with me.


So the idea is to:

1> Make a virtual machine with disk size slightly larger than the used space I would end up with (perhaps 25% -33% larger).

2> Do a standard installation of the same distro and release as the o/s I want to clone.

3> use rsync to difference the entire root partition between the two (assuming a default partition scheme where the home directory does not have it's own partition)


So here comes my code sample. It is based on the vdi file being located in the default Virtual Box location - a directory named "VirtualBos VMs" in the main user's directory.


```

rsync -av / /home/uname/"VirtualBox VMs"/NameOfGuest.vdi/.

```

I'm not sure if VBox doesn't create another folder inside VirtualBox VMs when the machine is created though. So maybe it would be:

```

rsync -av / /home/uname/"VirtualBox VMs"/NameOfGuest/NameOfGuest.vdi/.

```


What do you guys think? Would it work without breaking anything important? Any improvements or changes?

Thanks.
------------------

Edit:

What may be an important consideration just came to mind. What about the location of either the source and/ or the destination - with regard to the disk being mounted or not? I don't gather rsync cares but I'm not really sure.

---

### Post by ClientAlive on 2011-06-26
bump

---

### Post by drdos2006 on 2011-06-26
Virtual Box sets up two folders when you install a VM. One is Virtual VMs and the other is a hidden folder .VirtualBox where the .vdi file is stored.

On my machine I choose to store the .vdi file on a partition of my HDD that I can back up so that if the need arises, I can restore from the backed up .vdi file.

I use rsync to backup that .vdi and I also back the Virtual VMs folder from my home folder.

regards

---

### Post by ClientAlive on 2011-06-26
> **drdos2006 said:**
> Virtual Box sets up two folders when you install a VM. One is Virtual VMs and the other is a hidden folder .VirtualBox where the .vdi file is stored.

On my machine I choose to store the .vdi file on a partition of my HDD that I can back up so that if the need arises, I can restore from the backed up .vdi file.

I use rsync to backup that .vdi and I also back the Virtual VMs folder from my home folder.

regards


Right on. I'll have to look into that. Thanks.

---

### Post by ClientAlive on 2011-07-08
Cool.

Well, I was basically trying to figure out if there's a simple way to transform a regular/ base installation into the identical system you are actually using (your host) with all its additions, tweaks, etc, etc. The first thing that came to mind was rsync but I'm not sure if it would work for a couple different reasons:

1) Whether it would mess up any internal links in the system or not that the system needs to function properly. And . . .

2) Whether a *.vdi file can even be accessed/ modified in the way any other disk would be (as far as even being able to copy stuff into it with rsync). So, whether a guy could just find out the right abs path to use and simply make that path the destination of rsync's output.

If it did work it seems like a remarkably simple way of going about p2v'ing your system.

---

### Post by donpaterson on 2011-12-09
Hello,
I just P2V converted an Ubuntu 10.10 Desktop 64-bit install that was running on a physical PC.
I am using VMware workstation to host it but I guess any vm software would be the same.

This is how I P2V converted the box.

1. Build a VM with Ubuntu 10.10 64bit ISO (not worried about drive size matching). No updates done. Leave it booted up.
2. On the physical box run the tar command to back it up to a file (FullBackupDec2011.tgz), like this (ignored last error message):
```

```
cd/
sudo su
tar cvpzf FullBackupDec2011.tgz --exclude=/proc --exclude=/lost+found --exclude=/FullBackup*.tgz --exclude=/mnt --exclude=/sys --exclude=/home/don/notforbackup
```

```
3. Copy (ftp) the file onto the new VM (root / ) and then run (ignored last error message):
```

```
cd/
sudo su
tar xvpfz FullBackupDec2011.tgz 
```

```
4. Try to boot the VM
5. If it wont boot, to fix grub do this:
Boot the VM from Ubuntu CD in Try It mode.
Run (it is one line):
```

```
sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update && sudo apt-get install -y --force-yes boot-repair && boot-repair
```

```
6. Follow instruction and then reboot.

It was fast and easy.
If this didn't work I was going to replace step 2 and 3 with:
2. Boot physical with clonezilla live usb (or CD) and create a clone image file.
3. Boot 'bare metal' VM from clonezilla live iso and image blank new virtual disk from image file.
I would have used an interim VM to get the image file onto a seperate vdisk, which would have been a second disk in the new VM during the imaging process. There is a network option for clonezilla live too.
I actually have a clonezilla server so I usually save the physical image onto there and then PXE boot the vm and clonezilla server copy the image over to the VM but today I was virtualizing the clonezilla server itself (as a backup and proof of backup).
Hope this helps someone.

---

### Post by ClientAlive on 2011-12-10
Wow, this is such an old thread. I really didn't think anyone would make a response. Since then I did manage to get my system virtualized. I used the optional way that you mentioned at the end of your post. My challenge had been that I was working on the same machine I wanted to put the virtual copy on and the size issues that come along w/ clonezilla. I ended up putting the virtual disk on an external hard drive, resizing it, then moving it over to the original machine.

Thanks for sharing brother. Good stuff.


Jake

---

### Post by JKyleOKC on 2011-12-11
> **ClientAlive said:**
> 2) Whether a *.vdi file can even be accessed/ modified in the way any other disk would be (as far as even being able to copy stuff into it with rsync).Just came across this, Jake; there IS a way to access the content of a VDI file, but it's quite complex and not at all obvious. I had to dig out the details several months ago when the VDI file that had all my Email on it got corrupted, so that I could recover critical addresses and correspondence.

The VDI file has a very large header area, that contains data used by vbox to access its content. Once you get past that header area, it's identical to any other disk image. That is, it's a pure binary dump of the drive content, starting with its MBR and continuing to the final sector. You can strip off the header while making a copy, then mount the copy using the "loop" option to mount, and do anything within the mounted copy that you could to any other mounted filesystem.

I think there's a way to skip past the header while mounting, so that you do not have to use a copy, but I do not know whether you can make any changes to the content and retain the ability to use the VDI file in vbox. My need was simply recovering data, not changing a configuration.

I saved the commands I used, in ".bash_history" on another box, but don't remember all the details at this late date. I do remember that my starting point was a google search for "VDI file format" though...

---

### Post by ClientAlive on 2011-12-11
> **JKyleOKC said:**
> Just came across this, Jake; there IS a way to access the content of a VDI file, but it's quite complex and not at all obvious. I had to dig out the details several months ago when the VDI file that had all my Email on it got corrupted, so that I could recover critical addresses and correspondence.

The VDI file has a very large header area, that contains data used by vbox to access its content. Once you get past that header area, it's identical to any other disk image. That is, it's a pure binary dump of the drive content, starting with its MBR and continuing to the final sector. You can strip off the header while making a copy, then mount the copy using the "loop" option to mount, and do anything within the mounted copy that you could to any other mounted filesystem.

I think there's a way to skip past the header while mounting, so that you do not have to use a copy, but I do not know whether you can make any changes to the content and retain the ability to use the VDI file in vbox. My need was simply recovering data, not changing a configuration.

I saved the commands I used, in ".bash_history" on another box, but don't remember all the details at this late date. I do remember that my starting point was a google search for "VDI file format" though...



Right on. For a while now I've thoght it would be cool to manually create the vdi file to taste then copy over what you want so as to get as close to a manual creation as one could with the thing. Seems like this would be the way to go about it and the right kind of info go out for. Maybe one of these days I'll get back to that. I'm on to Xen at this point (or approaching it at least). We'll see how much of what goes into other virtualization programs applies to Xen. I bet I get my chance for a manual creation with it though. Seems that if a guy is going to find the need for that anywhere it's with Xen.

Nice to see you around again JKyleOKC. It's been a while.  :D

---

