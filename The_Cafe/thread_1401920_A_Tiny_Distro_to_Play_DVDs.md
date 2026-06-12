---
title: "A Tiny Distro to Play DVDs"
date: 2010-02-08
forum: The Cafe
---

### Post by neu5eeCh on 2010-02-08
On the laptop I presently own (on which I now run Ubuntu) there used to be a DVD Quickplay option. One could play a video without powering up Windows. Well... that's all gone now, but I thought it might be fun to recreate it on the Linux side.

So... here's my question: Is there a super small distro of Linux that I could run off a flash drive, that would load into RAM (like Puppy Linux) , and play DVDs? I know I don't have to do this, but Linux is putting the fun back into computers (for me). My thinking is that if the Distro runs off a Flash Drive, this leaves the DVD drive free for the movie.

I could also install the Distro on a super small partition (just for the fun of it) and show it off. Any ideas. (I could have sworn there was an off-shoot of tiny core or puppy that did something like this.)

---

### Post by chriswyatt on 2010-02-08
That's a neat idea.  I used to have HP Quickplay on this laptop until I wiped Windows off completely.  It was a neat feature and was good for showing off to people.

---

### Post by Warpnow on 2010-02-08
GeeXboX is EXACTLY what you describe.

[http://geexbox.org/en/index.html](http://geexbox.org/en/index.html)

---

### Post by neu5eeCh on 2010-02-08
> **Warpnow said:**
> GeeXboX is EXACTLY what you describe.

[http://geexbox.org/en/index.html](http://geexbox.org/en/index.html)

I'm going to look at it right now. :-)

---

### Post by Jose Catre-Vandis on 2010-02-08
> **Warpnow said:**
> GeeXboX is EXACTLY what you describe.

[http://geexbox.org/en/index.html](http://geexbox.org/en/index.html)

+1

And patiently waiting for GeeXboX 2 (Enna) :)

Also can be easily booted from HDD using grub2

---

### Post by Dragonbite on 2010-02-09
> **Jose Catre-Vandis said:**
> +1

And patiently waiting for GeeXboX 2 (Enna) :)

Also can be easily booted from HDD using grub2

So do you set it up as a dual-boot and choose geeXboX if you want a quick-run DVD player, or Ubuntu if you want the full-blown desktop?

---

### Post by markp1989 on 2010-02-09
> **Warpnow said:**
> GeeXboX is EXACTLY what you describe.

[http://geexbox.org/en/index.html](http://geexbox.org/en/index.html)

+1 geexbox rocks

---

### Post by CJ Master on 2010-02-09
Is GeeXboX quick to boot?

---

### Post by Jose Catre-Vandis on 2010-02-09
Yes as an alternate to booting into my main desktop, can just boot GeexBox up, for media playback.

Once you have the Geexbox iso to your liking (if you use the generator), mount the iso so you can get at the files within, and copy the entire GEEXBOX directory to your hard drive (I put mine in /boot/isos/)

You will now need to create a custom entry in grub2 I use 40_custom in the /etc/grub.d directory. Read the howto by dr305 to see how to use this.

Add an entry something like this:
```
menuentry "Geexbox HDD" {
        set root=(hd0,8)
        linux /boot/isos/GEEXBOX/boot/vmlinuz root=/dev/ram0 rw rdinit=linuxrc boot=UUID=1d2b639a-b83f-46f3-8a04-3f647fcce2af lang=en remote=atiusb receiver=atiusb keymap=qwerty splash=silent video=vesafb:ywrap,mtrr quiet
        initrd /boot/isos/GEEXBOX/boot/initrd.gz
}
```

Make sure you edit the root= and the boot=UUID= entries to match your system

---

### Post by Jose Catre-Vandis on 2010-02-09
> **CJ Master said:**
> Is GeeXboX quick to boot?

30 seconds or so - depending on your hardware / setup (networking etc) and whether you boot from CD or HDD

---

### Post by Lightstar on 2010-02-09
That's not the best looking OS :P  but it's cute, looks like an old video game menu.

What I would do though, is get a very small linux, like puppylinux that boots in a few seconds, and install a pretty application like [Moovida]("http://www.moovida.com/") as autorun.

there's a few other applications similar to moovida if that one doesn't float your boat.  But it can play youtube and ted.com and other streams as well as music, .avi, etc.

I actually never did try it for DVDs, since I use my dvd player.

---

### Post by Warpnow on 2010-02-09
I'd try boxee. I prefer it to moovida. 

And you should look into slitaz. It lets you remaster it using taz (its package manager) at any point.

---

### Post by Jose Catre-Vandis on 2010-02-09
Good alternatives from Lightstar and Warpnow, but the beauty of GeexBox is it just does what it says on the tin, plays media. Do one thing and do it well (K.Mandla!)

---

### Post by neu5eeCh on 2010-02-09
Well... I've tried GeexBox but it's been a flop on my system. I've asked for help over at the Geexbox forum but the silence is deafening (and here too). Unfortunately, their instructions are for legacy grub and incomplete at that. On the **upside**, I've learned a hell of a lot about GRUB2. I can now confidently edit the menu. So it's not a complete loss. Here's my Grub Script:

#!/bin/sh
exec tail -n +3 $0

menuentry "GeeXboX 1.2.4 for x86_32 (PC, MacIntel)"  {
    set root=(hd0,5)
    linux    /GEEXBOX/boot/vmlinuz root=/dev/ram0 rw rdinit=linuxrc boot=UUID=d46e2773-aba9-41b3-a36b-fc3a6710a474 lang=en remote=atiusb receiver=atiusb keymap=qwerty splash=silent video=vesafb:ywrap,mtrr quiet
    initrd    /GEEXBOX/boot/initrd.gz
}

When I try to boot to Geexbox I get some "hail marry" message that maybe my UUID is wrong (it's not).

So... besides Geexbox, what else is there?

---

### Post by Jose Catre-Vandis on 2010-02-09
> **VTPoet said:**
> Well... I've tried GeexBox but it's been a flop on my system. I've asked for help over at the Geexbox forum but the silence is deafening (and here too). Unfortunately, their instructions are for legacy grub and incomplete at that. On the **upside**, I've learned a hell of a lot about GRUB2. I can now confidently edit the menu. So it's not a complete loss. Here's my Grub Script:

#!/bin/sh
exec tail -n +3 $0

menuentry "GeeXboX 1.2.4 for x86_32 (PC, MacIntel)"  {
    set root=(hd0,5)
    linux    /GEEXBOX/boot/vmlinuz root=/dev/ram0 rw rdinit=linuxrc boot=UUID=d46e2773-aba9-41b3-a36b-fc3a6710a474 lang=en remote=atiusb receiver=atiusb keymap=qwerty splash=silent video=vesafb:ywrap,mtrr quiet
    initrd    /GEEXBOX/boot/initrd.gz
}

When I try to boot to Geexbox I get some "hail marry" message that maybe my UUID is wrong (it's not).

So... besides Geexbox, what else is there?

Just for sanity's sake run:
```
sudo blkid
``` and report back

and have you got the GEEXBOX directory in the root of the partition you are booting from, if not make sure you have the full path (but sounds more like partition problems)

Also, it won't like booting off an ext4 partition

---

### Post by neu5eeCh on 2010-02-09
> **Jose Catre-Vandis said:**
> Also, it won't like booting off an ext4 partition

Ah.

I see.

Maybe that's the problem. My partition is, indeed, an ext4 partition. Did I miss that little nugget of information somewhere?

I thought I read somewhere that one can boot it off a windows partition using grub?

---

### Post by neu5eeCh on 2010-02-09
So... what if I created an ext2 or ext3 partition just for Geexbox? 

Could I just plop the Geexbox folder onto the partition and point Grub to the folder? I wonder...

---

### Post by Kenny_Strawn on 2010-02-09
> **VTPoet said:**
> So... what if I created an ext2 or ext3 partition just for Geexbox? 

Could I just plop the Geexbox folder onto the partition and point Grub to the folder? I wonder...

I think probably Ext**_4_** will do. It will require some work, though.

---

### Post by neu5eeCh on 2010-02-09
> **Kenny_Strawn said:**
> I think probably Ext**_4_** will do. It will require some work, though.

Yes, but will it require *more* or *less* work than creating a new partition? **That** is the question. ;)

---

### Post by Jose Catre-Vandis on 2010-02-10
I have not had any luck booting GEEXBOX off an ext4 partition, and I have tried and tried! Easier just to create a small ext2/3 or fat32 partition. If you have a multiboot environment (inc Windows) then why not set up a "data" partition to easily share data (Ext2fsd etc can't read ext4 either for Windows, unless you start by formatting the ext4 partition with some special flags).

---

### Post by markp1989 on 2010-02-10
> **VTPoet said:**
> So... what if I created an ext2 or ext3 partition just for Geexbox? 

Could I just plop the Geexbox folder onto the partition and point Grub to the folder? I wonder...

on my desktop i had to make a small ext2 partition at the end for geexbox because ot wont work with ext4

---

### Post by neu5eeCh on 2010-02-10
> **markp1989 said:**
> on my desktop i had to make a small ext2 partition at the end for geexbox because ot wont work with ext4

And if I do that (I'll make a small EXT2 partition this morning), I wonder if Puppy, with a good player (above) would load and be faster?

---

### Post by neu5eeCh on 2010-02-10
OK. I created a small 8g ext2 partition. Now I need to change permissions (ownership) of the partition. I've been looking elsewhere on the [forum for guidance]("http://ubuntuforums.org/showthread.php?t=171735") and will search the net. I'm worried that some of the info might be out of date. Here's the goods on the new partition:

/dev/sda7: UUID="fc10669d-9c82-47e8-840a-7ac7119336a4" TYPE="ext2" 

I need to familiarize myself with the necessary commands. I welcome any guidance. In the meantime, I'll see what I can find out.

---

### Post by neu5eeCh on 2010-02-10
> **Jose Catre-Vandis said:**
> I have not had any luck booting GEEXBOX off an ext4 partition, and I have tried and tried! Easier just to create a small ext2/3 or fat32 partition. If you have a multiboot environment (inc Windows) then why not set up a "data" partition to easily share data (Ext2fsd etc can't read ext4 either for Windows, unless you start by formatting the ext4 partition with some special flags).

**Got it!** It's working now. I installed it on an ext2 partition and it works beautifully. Loads _fast_(!) and faster than the old QuickPlay on the windows side. Very impressive.

I haven't figured out how to successfully select aspect ratios but, at this point, that's the least of it.

---

### Post by Jose Catre-Vandis on 2010-02-10
:)

Using just the keyboard, aspect ratios can be changed by following the menu:

Preferences > Video > Aspect Ratio

You can also fiddle about with mplayer.conf (/GEEXBOX/etc/mplayer/) on the HDD to set the default ratio and display

---

### Post by markp1989 on 2010-02-11
> **VTPoet said:**
> **Got it!** It's working now. I installed it on an ext2 partition and it works beautifully. Loads _fast_(!) and faster than the old QuickPlay on the windows side. Very impressive.

I haven't figured out how to successfully select aspect ratios but, at this point, that's the least of it.



good to hear :) 8gb is alot bigger then geexbox needs, i have a 1gb (still abit over sized) partition for mine :)

---

### Post by neu5eeCh on 2010-02-11
> **markp1989 said:**
> good to hear :) 8gb is alot bigger then geexbox needs, i have a 1gb (still abit over sized) partition for mine :)

Yeah... I figured 8g was **way** more than I needed. On the other hand, if I decided I didn't like GeexBox, I thought I'd have enough room to install something else - play around with the space.

---

### Post by markp1989 on 2010-02-12
> **VTPoet said:**
> Yeah... I figured 8g was **way** more than I needed. On the other hand, if I decided I didn't like GeexBox, I thought I'd have enough room to install something else - play around with the space.

makes sence :) hope you like you geexbox :)

---

### Post by neu5eeCh on 2010-02-15
Just noticed that **GeexBox 2.0 Alpha1** was released. I downloaded it,  burned it, & copied it  to my EXT2 partition. I tried to boot the new release using the same script in GRUB2 (crossing my fingers) but it didn't work.

Have any of you tried booting the new GeexBox from a partition? I couldn't find any instructions for the new version?

---

### Post by markp1989 on 2010-02-15
> **VTPoet said:**
> Just noticed that **GeexBox 2.0 Alpha1** was released. I downloaded it,  burned it, & copied it  to my EXT2 partition. I tried to boot the new release using the same script in GRUB2 (crossing my fingers) but it didn't work.

Have any of you tried booting the new GeexBox from a partition? I couldn't find any instructions for the new version?

i not tried it, but the kernel nameand initrd might be named different, so you might need to change grub to match

---

### Post by neu5eeCh on 2010-02-15
> **markp1989 said:**
> i not tried it, but the kernel nameand initrd might be named different, so you might need to change grub to match

Based on my uninformed observations, everything is in the same place. But I'm wondering if the new Geexbox doesn't like booting from EXT2?

The old Geexbox works just fine, so there's no urgency. I'll be interested to see if someone else (with more experience) can take it for a spin.

---

### Post by Jose Catre-Vandis on 2010-02-15
> **VTPoet said:**
> Based on my uninformed observations, everything is in the same place. But I'm wondering if the new Geexbox doesn't like booting from EXT2?

The old Geexbox works just fine, so there's no urgency. I'll be interested to see if someone else (with more experience) can take it for a spin.

I'll have a play this evening. FWIW the 2.0 alpha has a long way to go before its "really" ready, but it looks fantastic.

---

### Post by Jose Catre-Vandis on 2010-02-15
> **Jose Catre-Vandis said:**
> I'll have a play this evening. FWIW the 2.0 alpha has a long way to go before its "really" ready, but it looks fantastic.

Nope can't get it to boot. Seems to be looking for an NTFS signature, then goes into kernel panic. Might be best to try an install to a separate partition?

---

### Post by neu5eeCh on 2010-02-15
> **Jose Catre-Vandis said:**
> Nope can't get it to boot. Seems to be looking for an NTFS signature, then goes into kernel panic. Might be best to try an install to a separate partition?

Same here. Don't know whether that means it wants an NTFS partition? I might try creating an NTFS partition just to see. If I do that, I'll let you know how it goes. (*It's already on a separate EXT2 partition.*)

---

### Post by neu5eeCh on 2010-03-13
Another GeexBox Alpha [was released today]("http://www.geexbox.org/en/index.html") (3.13.2010). I notice they haven't changed their instructions for booting Geexbox on a dual boot linux system.

I may try the new release to see if it works with the same GRUB2 script (which works for Geexbox 1.x), but I'm not holding my breath.

---

