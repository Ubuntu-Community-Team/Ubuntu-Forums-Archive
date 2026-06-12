---
title: "Encrypted volume - broken"
date: 2012-03-04
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by EgoGratis on 2012-03-04
I tested encrypted USB key today and it does not work for me.

-USB key does not get mounted and dialog to enter passphrase does not show.
-Disk Utility does show USB key as encrypted volume but trying to unlock volume fails.

Basically nothing works besides detection in Disk Utility.

Can somebody confirm this and suggest the package name this bug should be filed against!

---

### Post by phaed on 2012-03-05
Do you have cryptsetup installed?

---

### Post by EgoGratis on 2012-03-05
It was not installed and after installing it:

-USB key does not get mounted and dialog to enter passphrase does not show. This is still true.
-Disk Utility does show USB key as encrypted volume but trying to unlock volume fails. This does work now. 

Rant ON (not directed to you):

I hate when this sort of things happens. The moment you said if something was installed or not i remembered that back when i created encrypted USB key it took few hours to succeed. Why it took so long? 

THERE WAS NOT AND STILL IS NO VISUAL INDICATOR THAT PRESSING ON BUTTON IN DEFAULT SOFTWARE WILL NOT WORK BECAUSE PACKAGES ARE MISSING!

THIS IS JUST NOT ACCEPTABLE AND THIS IS A BUG!

It's like saying i bought a car but transmission didn't work. I could move the stick but nothing happened. Then when i DISASSEMBLED the car i noticed there where no GEARBOX IN THE CAR! Why am i ranting? For two reasons:

1.) First time this happened to me it took few hours to figure out what was going on. After finding the error and finding the solution in some bug report i managed to make it work.

IT WAS REPORTED MANY TIMES AND THIS CLEARLY IS A BUG!

Now new version of Ubuntu is just around the corner and nothing changed. Why is this happening?

THERE WAS NOT AND STILL IS NO VISUAL INDICATOR THAT PRESSING ON BUTTON IN  DEFAULT SOFTWARE WILL NOT WORK BECAUSE PACKAGES ARE MISSING!

THIS IS JUST NOT ACCEPTABLE AND THIS IS A BUG!

2.) I found similar BUG in bluetooth functionalities and report it on BUG TRACKER:

[http://ubuntuforums.org/showpost.php?p=11693532&postcount=7](http://ubuntuforums.org/showpost.php?p=11693532&postcount=7)

And what happened? Nothing. It was rejected and said this is not a BUG! Yes it is, both of this two mentioned things are BUGS! HUGE BUGS!

In the end it took 123 kB to fix the thing with apt-get, imagine only 123 kB. Or imagine there would be some visual indicator software is missing and the button in stock software will not work until it is installed!

---

### Post by EgoGratis on 2012-03-05
I forgot to say thanks for the solution. Thanks!

---

### Post by EgoGratis on 2012-03-07
I tested this again today on fully updated Ubuntu 12.04.

-USB key does not get mounted and dialog to enter passphrase does not show.** It works!**
-Disk Utility does show USB key as encrypted volume but trying to unlock volume fails. **It works!**

The only thing missing now from superb experience:

THERE WAS NOT AND STILL IS NO VISUAL INDICATOR THAT PRESSING ON BUTTON  IN  DEFAULT SOFTWARE WILL NOT WORK BECAUSE PACKAGES ARE MISSING!

Two solutions:

-Somewhere is mentioned why it doesn't work out-of-the-box!
-Package is included by default and it just works out-of-the-box!

I would open bug report but probably it will just get rejected. But form my point of view if there is a button in stock software that does not work and user does not know why it does not work it's a bug!

---

### Post by cariboo on 2012-03-07
> **EgoGratis said:**
> I tested this again today on fully updated Ubuntu 12.04.

-USB key does not get mounted and dialog to enter passphrase does not show.** It works!**
-Disk Utility does show USB key as encrypted volume but trying to unlock volume fails. **It works!**

The only thing missing now from superb experience:

THERE WAS NOT AND STILL IS NO VISUAL INDICATOR THAT PRESSING ON BUTTON  IN  DEFAULT SOFTWARE WILL NOT WORK BECAUSE PACKAGES ARE MISSING!

Two solutions:

-Somewhere is mentioned why it doesn't work out-of-the-box!
-Package is included by default and it just works out-of-the-box!

I would open bug report but probably it will just get rejected. But form my point of view if there is a button in stock software that does not work and user does not know why it does not work it's a bug!

If you report the problem without any dramatics, just the facts it shouldn't be rejected. File the bug against ubiquity.

---

### Post by EgoGratis on 2012-03-07
> If you report the problem without any dramatics, just the facts it shouldn't be rejected. File the bug against ubiquity.

I did this for the same thing in stock Bluetooth software and it was rejected.

[https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/933533](https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/933533)

Ubiquity, cryptsetup, Disk Utility... what would be the best place to report it?

---

### Post by cariboo on 2012-03-07
If you set up encryption during the install process, with either the alternate install iso or the live CD, then you'd file the bug against ubiquity, the report should be about missing  cryptsetup as a dependency when setting up encryption on a usb device. Seeing as you didn't tell us how you did it, you could also just file the bug against linux, and let launchpad sort it out.

I'd also suggest leaving out the part about being informed about needing it, as it should be included as part of the installation process.

---

### Post by EgoGratis on 2012-03-07
This problem was not part of installation process and i don't know if it's connected somehow with installation process too. It's about creating and using encrypted USB media. It probably affect creating and using all encrypted media not just USB if the same procedure is used but i use it only for USB media.

Now when this is fixed i tested it again and noticed cryptsetup does not have to be installed any more and user still is prompted to enter password when inserting encrypted USB key:

-USB key does not get mounted and dialog to enter passphrase does not show.[B] It works!

[/B]Installing cryptsetup as noticed above didn't have affect on this and i guess it was fixed separately and now it works out-of-the-box. This is what users expects when entering encrypted USB media and now it works out-of-the-box in my test as it should and it didn't a while back. This is fixed in Ubuntu 12.04!

This one:

-Disk Utility does show USB key as encrypted volume but trying to unlock volume fails. **It works!**

Still persist if cryptsetup is not installed. Disk Utility (palimpsest or gnome-disk-utility) needs cryptsetup to create and work with encrypted USB media. Right now if u open Disk Utility you will notice when formating USB media it has option Encrypt device. 

-If u select this option the process will fail. 
-If u insert encrypted USB media you and try to unlock it in Disk Utility it won't work.

User has to install cryptsetup for this to work but has no visual information this is needed. I guess this is bug against gnome-disk-utility then?

[https://bugs.launchpad.net/gnome-disk-utility](https://bugs.launchpad.net/gnome-disk-utility)

---

### Post by EgoGratis on 2012-03-07
I tested again and still both bugs  take place if cryptsetup is not installed. 

It's true password dialog is presented to the user but entering password will fail if cryptsetup is not installed.

I found this bug reported about year and half back and i input more information on the subject.

[https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/651730](https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/651730)

---

### Post by EgoGratis on 2012-03-14
Looks like the problem is solved. Fantastic!

[https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/343363](https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/343363)

It's always a shame that something that DOES work when everything is installed doesn't work because something is not installed and user just don't have the info to solve the problem.

---

