---
title: "Enlarging a Disk in VirtualBox - gparted isn't working"
date: 2015-06-28
forum: Virtualisation
---

### Post by Lappert on 2015-06-28
I'm running Kubuntu 14.04 with VirtualBox 4.3.10. I have a Win7-32 VM that seems to run OK. I set it up with 40GB drive on a SSD. For a number of reasons - mostly to run windows programs - I want to expand the size of the disk to 50GB.

I used [FONT=monospace]VBoxManage modifyhd “/path/to/Win7-32.vdi” –resize 51200
and this seemed to work OK.

I booted into Win7 disk management and I had a 10GB unallocated partition. I then used Extend Volume to combine the original 40GB partition with the unallocated 10GB, resulting in a 50GB partition. Seemed to be working. Now Win7 reports 49.9 Healthy primary C: partition.

I power down and VirtualBox Manager reports SATA Port O: Win7-32.vdi (Normal, 50.00 GB)

Everything seems OK, but in Krusader, I still get the 39GB file size for Win7-32.vdi.

So I'm thinking I might have missed something. I looked at a different how-to page, download gparted, In VirtualBox Manager > Settings > Storage I add the gparted .iso to the IDE controller, mark it as "Live" and proceed to boot the Win7 machine.

I get the gparted splash screen, pick the defaults, keyboard, language etc. and hoit enter. I get some txt about it being Debian, and then it just stops. No graphical gparted page. Nothing. I power down again and try the option to force the video. Again, nothing. It is just hanging.

So that's where I am and I'm at a loss what to do next.

Thanks and Help![/FONT]

---

### Post by gedakc on 2015-06-29
Please try the latest GParted Live version 0.22.0-3 which is currently contained in the testing directory.

The 0.22.0-3 version resolved the problem for some others using Virtual Box.  See [gparted-live 0.22.0-2.iso: X does not start]("http://gparted-forum.surf4.info/viewtopic.php?id=17361").

---

### Post by Lappert on 2015-06-29
Thanks for the reply. I have now DLed gparted.0.22.0-3.iso and will give it a try.

However, I did make some progress as I describe below, so the new version might, or might not help.

After a bit of research, I made two modifications to the steps I outlined above.

First, I had put the gparted.iso on the IDE controller of Virtualbox Manager > Storage. In that case I had to delete the physical CD/DVD Rom Drive in order to get gparted to even attempt to book. So instead I restored the CD/DVD drive to the IDE controller and then added gparted to the SATA controller.

Second, under VirtualBox > Settings > System, I checked Enable EFI. I don't know why, but this was mentioned in some posts.

With all that done, I booted again. This time gparted loaded. (this is still with gparted 0.22.0-2.iso)

However, I only geet so far.

Once loaded, I right-click on the existing active partition and click on "Resize/Move." I slide the bar to 51099 MB, and click Resize/Move. Then I clikc "Apply."

That is when the error occurs, every time. I try to save the details as instructed, but it tries to save them on another file system, not the one on my hard drive. So I am unable to save the details, at least on my drives.

And the unallocated partition remains just that.

If I get any further with the 22.0-3 version, I'll update this thread.

Than
ks.

---

### Post by Lappert on 2015-06-29
OK, I DLed the newer version of gparted and installed it on VirtualBox as described above. It booted fine. I resized/moved the allocated partition to the full 50 GB. Then I hit "apply."

As before, it stopped with an error.

I was unable to save the details, but I was able to take two screen grabs of the errors. Perhaps this will gove you some insight as why this is happening. Thank you.

[ATTACH=CONFIG]262925[/ATTACH][ATTACH=CONFIG]262926[/ATTACH]

---

