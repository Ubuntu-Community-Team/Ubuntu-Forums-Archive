---
title: "help with xp partition permissions and virtualbox"
date: 2009-07-12
forum: Virtualisation
---

### Post by jcm1107 on 2009-07-12
I want to mount my windows xp partition with virtualbox. I have tried to follow tutorials on here and I am very close. I also created a windows xp install inside of ubuntu it worked but now stoped working. I think I am having permission issues. I used to be able to open my storage partition inside of ubuntu and also my xp partition to view files. I used to be able to do anything with the storage partition and now I can't even open it. I don't know what caused this but it may have been when I was doing the virtualbox permissions. I just am not sure. Could someone please help me with this. I know you may want more info, so just let me know and I will give you what I know. I attached a screen shot of what the virtual machine is doing now when I try to boot it. It tries to boot and shows the windows logo and then I get the blue screen of death as it is so famously called. The actual partition acts like it wants to boot and then it stops short of the windows logo.

---

### Post by jcm1107 on 2009-07-14
bump

---

### Post by aesis05401 on 2009-07-14
> **jcm1107 said:**
> I want to mount my windows xp partition with virtualbox. *snip*

I have not done this personally, but there used to be a utility that could add the necessary .vdi file information to an existing disk image so it could be mounted in VBox. 

A little searching should turn that tool up, but I am not sure if it has been kept current.

---

### Post by jcm1107 on 2009-07-14
> **aesis05401 said:**
> I have not done this personally, but there used to be a utility that could add the necessary .vdi file information to an existing disk image so it could be mounted in VBox. 

A little searching should turn that tool up, but I am not sure if it has been kept current.

I think I have the .vdi file right I just no longer have permissions to anything!! I don't know why but I cant even play a cd because I don't have permissions to mount it!! I used to be able to view files on disks play music and open my storage partition and even open my windows xp partition I just couldn't run anything on the xp partition. I had games on the storage partition I could play in ubuntu with dosbox, but now I cant open that storage partition. I could also play games on the xp partition with dosbox and listen to music from that partition but I cant open it now. I know it is permission issue but I don't know how to fix it!! Thanks for any advice you can give on this!!

---

### Post by aesis05401 on 2009-07-14
Windows is finicky about upgrades to the underlying hardware - so any upgrade or other change that causes the VM hardware layer to appear to change can cause that particular blue screen message.

First thing to try is locating settings for your IDE controller type.  Should be under the Machine/Settings/Advanced/'IDE Controller Type' setting (without machine running).  Try the 'PIIX3' setting if you are currently set to PIIX4.  



Post back if this does not help.

---

### Post by jcm1107 on 2009-07-15
> **aesis05401 said:**
> Windows is finicky about upgrades to the underlying hardware - so any upgrade or other change that causes the VM hardware layer to appear to change can cause that particular blue screen message.

First thing to try is locating settings for your IDE controller type.  Should be under the Machine/Settings/Advanced/'IDE Controller Type' setting (without machine running).  Try the 'PIIX3' setting if you are currently set to PIIX4.  



Post back if this does not help.

THANKS!!! This got my virtualbox install of windows xp to work with virtualbox!! Now I just need to know what to do to get my physical windows xp partition to work with it. It tries to boot but then when it should have the windows xp logo it just has a gray bar and never goes any farther. The attached pic is as far as it will go, it asks if I want to start in safe mode and then it asks for my hardware profile( a thread on here said to make a virtual and physical hardware profile) and then I select that and boot and it does not go any farther.
 I still can not mount any other partitions on my hard drive and I still can not use the CD drive. I also saw when I booted my computer that force mount of a device failed I think it was my storage partition but I only saw it real quick. I would really appreciate any help on this I need my cd burner!! and also other partitions!! Thanks.

---

### Post by jcm1107 on 2009-07-16
OK I fixed my permission issues. I had to run chkdsk /f in a command prompt in windows xp to schedule chkdsk /f for the next reboot and then I had to do it again once was not enuff and rebooted several times after that. 
I found something interesting about my physcal windows partition that I am trying to boot in virtualbox, for some reason when I made the .vdi file for it, it used the whole hard drive instead of just the windows partition. I think trying to boot this is what caused me to loose acess to everything that I lost ( and then regained with the chkdsk /f). How can I make the vdi file with only the windows partition?

---

### Post by jcm1107 on 2009-07-16
I got my existing windows partition to boot by checking the Enable IO APIC.

---

