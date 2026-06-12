---
title: "Anything to consider for installing Feisty parallel to VISTA?"
date: 2007-05-17
forum: Windows
---

### Post by AGS on 2007-05-17
[LEFT]Hej,

I just bought a Vista-preinstalled notebook (Toshiba Satellite A100-0something...) and would like to install Kubuntu 7.04 parallel to M$. Is there anyone out there with experience in this matter? I think I heard rumors that Vistas MBR is somewhat  different from prevous versions and installing Linux might render Vista unloadable.

So, is there anything special to consider when installing the Feisty Fawn side-by-side to WinVISTA?

[/LEFT]

---

### Post by rsambuca on 2007-05-18
It is pretty easy, just make sure that you use the Vista disk partitioner to free up space for Kubuntu.  If you use the Kubuntu partitioner Vista will not be able to boot afterwords.  Other than that, just follow the prompts on the install CD and you will be fine.

---

### Post by theicyj on 2007-05-18
I've been running Vista Business Ed and Ubuntu 7.04 in dual-boot configuration since Vista's launch.  It was very easy to set up, from what I've heard, it is recommended to install Vista first, then install Ubuntu.  Also, Vista comes with a disk resizer that I would use to make some free space before installing Ubuntu.

---

### Post by snowbalrog on 2007-05-18
The main ones have been hit.. just make sure Vista's disc partitioner is used. I didn't have any trouble setting up a dual-boot (Vista Premium and Ubuntu Feisty) on my acer, and I'm rather new to Linux. 

The thing about Vista's MBR being whack is that Vista's boot thingy nerfs GRUB (or whatever else is used) when Linux is there first, and won't allow the option to boot to it (I think that's what you're referring to?).

---

### Post by AGS on 2007-05-20
Thanks a lot so far, guys! I'll give it a try.
 
If I hadn't asked, I would have used QtPartEd of Kubuntu. If this had kicked Vista, my wife would have kicked me ;) (She doesn't like Linux at all).

---

### Post by Pistolla on 2007-05-20
One of the things i am having issues with is, when i gets to the partition spot, i used the manual (found elsewhere on these forums in regards to dual-bootin') the issue at hand is after i make the prequisite linux swap partition and then i guess leave the rest (of the free space) for linux and when i try to go further it says i need to have root what do i do about that?

---

### Post by rsambuca on 2007-05-20
If you choose manual partitioning, then you have to designate a swap partition and a root partition.  The root partition is also referred to as the '/' partition.

---

### Post by Pistolla on 2007-05-20
Where do i find that option? When i make the 256MB linux swap, i still have a lot of free space and nowhere do i see the option for the "/" (root). How do i go about settin' one up?

---

### Post by Pistolla on 2007-05-20
Or should i dare to use the guided option and, instead of using the remaining free space, decrease it to, say, 30 gigs or so. I haven't tried it yet because it says "changes made cannot be undone" (paraphrased). And will that also present a similar problem that i seem to be having under the manual option?

---

### Post by rsambuca on 2007-05-20
If you have already used the Vista disk partitioner to create free space for ubuntu, then you can just tell the installer to use the free space (I can't remember the exact words).  As long as you know which partition Vista is on (you should be able to tell by the size), then you should be OK.

If you don't feel comfortable doing this, then list your exact hard drive info here and we can guide you through it in more detail.  ie. total size of hard drive, how big your vista partition is, etc.

---

### Post by Pistolla on 2007-05-20
OK here goes:
/dev/sda
  /dev/sda1 NTFS media/sda1 210461 MB 14000 (used)
  free space 31458
  /dev/sda3 NTFS /media/sda3 8136 MB 7200 (used)

the option of free space has a drop down menu with the swap included but not the '/' part

---

### Post by Pistolla on 2007-05-20
OK here goes:
/dev/sda
/dev/sda1 NTFS media/sda1 210461 MB 14000 (used)
free space 31458
/dev/sda3 NTFS /media/sda3 8136 MB 7200 (used)

the option of free space has a drop down menu with the swap included but not the '/' part

---

### Post by AGS on 2007-05-22
> **Pistolla said:**
> 
the option of free space has a drop down menu with the swap included but not the '/' part
Hej,

same was here for me. I allready installed Feisty to my old desktop machine so I thougt I wa prepared, but when I first opened the installer on my 6 week old Notebook I too didn't get the option for "/" in the dropdown menu for the mount points. I restarted the installer three times but nothing changed, so the installer in itself didn't offer an answer.

I updated the packages with Adept Manager (luckily my notebooks WLAN works, contrary to my desktop's USB-powered WLAN from DLINK :-k :frown: ) after I chose ALL sources - and then this part of the installation worked. So maybe there's some kind of error in the installer as I didn't get this error during desktop installation :-k

Unfortunately half an hour later the installer aborted with a GRUB error... :(

---

### Post by Pistolla on 2007-05-22
I would go back to Dapper Drake (still have the CD) however, vista doesn't want to recognize it or play nicely. So i am stuck just dealin with vista until i get my old 'puter up and runnin' (lack of space on the desk and only one connection-so i need a router)

---

