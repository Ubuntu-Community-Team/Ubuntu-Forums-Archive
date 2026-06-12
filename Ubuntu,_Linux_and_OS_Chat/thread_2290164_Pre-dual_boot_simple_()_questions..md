---
title: "Pre-dual boot simple (?) questions."
date: 2015-08-10
forum: Ubuntu, Linux and OS Chat
---

### Post by MachFront on 2015-08-10
Greetings all! :)

After years of hemming and hawing and half-starts and "maybes" and "I'm gonna"'s, etc. I'm finally set to dive full-on into Linux via Lubuntu*.

I'll be dual-booting a Win 7 laptop (HP 2000).

What I'd like to know is....

1. Would the Lubuntu partition be able to easily access the files on the Windows partition? What I mean is.. can I keep my pics, docs, music, etc. on the existing W7 partition and utilize Linux softs (such as media players) to make use of the files?
If no (i likely will not), or if...yeah but PITA, etc... then....

2. If I slap those things over to an external (formatted for Windows stuffs)... once I have slimmed down my W7 side and have installed Lubuntu 'pon the rest... when I plug in, while in Lubuntu, to the external...will I experience some sort of pain of simply bringing in my files (music, docs, pics, movies, etc.) from that external to the Linux partition?

3. Is there something that jumps out at you folks that makes you go: "Whoa. You dummy. You'll really, really need to do/consider/etc. this or that." ?


The only reason I remain on Windows nowadays is because, though Linux music production stuff is very nice and still moving forward, to be frank it's simply not as easy and reliable and straightforward or with as many solid options as on Windows. But I saw that that was the ONLY reason...so why waste time on Windows otherwise I said. Right? So, here I am...there ya go...
My win partition will be small and only contain the operating system and my music production stuffs. My (hopefully) forthcoming Lubuntu partition will be everything else. Here's to it.



*I actually did dual-boot my XP desktop with Mint years ago and while it worked well, since Gnome 3 was relatively new at the time, I experience weird graphic gliches (something to do with, at the time, Gnome 3 and AMD processors or something if I recall...), so ...since that machine, though it worked well and I took care of it and it was and still is excellent and responsive despite never being re-installed...I had no way at the time of saving anything so I treated the machine like a house of cards. I just didn't want to touch it(update Mint or what-have-you) lest something be lost and so on... yeah, yeah, I KNOW. lol Plus, grub has acted kinda weird over the years. First it was as advertised, nowadays it simply sits there (there is no 'count down' or whatever) It would sit there for hours it I let it and didn't select either XP or Mint. Odd. So...yeah...

---

### Post by nerdtron on 2015-08-10
> 1. Would the Lubuntu partition be able to easily access the files on the Windows partition? What I mean is.. can I keep my pics, docs, music, etc. on the existing W7 partition and utilize Linux softs (such as media players) to make use of the files?
If no (i likely will not), or if...yeah but PITA, etc... then....
Yes, Lubuntu can read/write windows partition just fine. But from windows, you can't access your linux partitions.

> 2. If I slap those things over to an external (formatted for Windows stuffs)... once I have slimmed down my W7 side and have installed Lubuntu 'pon the rest... when I plug in, while in Lubuntu, to the external...will I experience some sort of pain of simply bringing in my files (music, docs, pics, movies, etc.) from that external to the Linux partition?
An external drive formatted in FAT32 or NTFS will just be the same as an external hard drive or USB. you'll be able to read/write on that device just fine while inside Lubuntu.

> 
3. Is there something that jumps out at you folks that makes you go: "Whoa. You dummy. You'll really, really need to do/consider/etc. this or that." ?
Yup. You can have two options on dual booting:
a. Boot into the Lubuntu live CD and choose "Install side-by-side". You'll be able to adjust hard drive partition allocation on that screen via a nice GUI slider. Don't do this method twice. If you are already dual-booting, and you want to reinstall Ubuntu, then you should choose the second option.
b. This options takes a little hard work but provides you with better partition control. You shrink your windows 7 partition while you are in windows. Then boot into the lubuntu installer and choose "Something Else" to enter the manual partitioning screen. This is where you will need to assign in which partition you are going to install Lubuntu. If you choose this option, seek the help of the forums so you don't mess up.


> The only reason I remain on Windows nowadays is because, though Linux music production stuff is very nice and still moving forward, to be frank it's simply not as easy and reliable and straightforward or with as many solid options as on Windows. But I saw that that was the ONLY reason...so why waste time on Windows otherwise I said. Right? So, here I am...there ya go...
My win partition will be small and only contain the operating system and my music production stuffs. My (hopefully) forthcoming Lubuntu partition will be everything else. Here's to it.
Linux is a good platform to migrate to. Especially when the software that you are using are already available in Ubuntu. Maybe you can tell us more about your software needs because "Linux is NOT a drop in replacement for Windows"

---

### Post by oldfred on 2015-08-10
If you have a standard Windows 7 install, you may have used all 4 primary partitions. Vendors seem to do that just to make it difficult to install Linux.

Most with HP backup the HP tools partition. It also can be re- downloaded from HP. And of course good backups of your Windows install & all data. If your Music is at all valuable even if time to recreate, then good backups are vital. Even hard drives fail after a few years.

 My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor utility partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. - gordintoronto
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)

---

### Post by MachFront on 2015-08-16
I thank you all!
The HP issue may or may not be a 'thing'. I've a main Windows partition (though I assume there may be another partition taken up by Windows system (that little few megs for whatever), as well as having a recovery partition and an "HP Tools" partition. Viewing my drive one only sees the three but...yeah...doesn't Windows take up yet another partition for the system that's a handful of megs?... Hmm..

So.
Here's my plan. Lemme know if it obviously appears I would stub my toe or am/would be going full dunce withing these steps...

1. Grab my 'stuff' and plop it onto an external.
2. Reset Windows back to factory settings (as I cannot do a fresh re-install, not having a Win disc).
3. Within Win, set the Win partition to about 40GB (it's 300GB drive).
4. Tweak Win for my music production needs (turning off many visual effects, turning off a bunch of unneeded services, etc.)
5. Install my music programs, Firefox (only for updating my music stuff,etc.), a cleaner or two, a third-party defragger, and so on. Plus add my software synths, samples and soundfonts.
6. Run the Lubuntu live CD and install on the 'remainder' or the drive (around about 250GB).
7. Remove media. Turn off.
8. Power on laptop...I'll assume grub will show up and boot into Lubuntu.
9. In Lubuntu, plug into external and put all my 'stuff' in the various Lubuntu folders (music, docs, vids,etc.).
10. Enjoy life again.

The ONLY reason I'm tied to Windows is because, though music production stuff on Linux is more than simply do-able, to be brutally honest it's much more easy and solid via Windows. I'll likely be futzing about with some Linux music production stuff too (the old Seq24 looks fun and QTractor looks really cool and my style), but often I'm sitting here browsing whilst watching 70s and 80s b and z-grade sci-fi and horror movies and inspiration strikes and in Win I can just slam into my chosen DAW (Reaper) and not worry about Wine or Jack or if a given synth will work. I can just do it. But while I'm going about my daily whatsits in Lubuntu in the future I'll need at least some stuff to at least act as a 'sketchpad' for when I absolutely need to put down something NOW. So I'm not going to want to save everything, log out, log back in, boot to Win and THEN...FINALLY get to my music creation stuff, ya know?
ANYWAY!

Ya know... one always hears about such-n-such niche group having forums full of elitists and so on... I've never experienced that. Certainly not in the Linux community. Even though my questions could evoke "OMG! RTFM for eff's sake! Really!" and it may very well be justified, I've never had that happen. Folks are patient and helpful and positive. It's awesome. I've seen it here yet again. Thanks so much for that. Really. :) Cheers an' stuff!

---

### Post by Bucky Ball on 2015-08-16
*Thread moved to **Ubuntu, Linux and OS Chat**.*

And cheers right back at ya. :)

---

