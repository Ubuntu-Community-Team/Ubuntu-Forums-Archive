---
title: "Ubuntu rescues Windows (again)"
date: 2008-02-23
forum: Testimonials &amp; Experiences
---

### Post by freebeer on 2008-02-23
So I'm at a client's site who just recently bought a new computer.  They're running Win2k and have asked me to re-install it on the new box, add in the various bits of software they need, connect it to the network, yada yada yada.

Ok.  So I install Win2k on the new machine.  It's a painfully slow process, but it proceeds along at the expected pace.  When it comes to adding the drivers, nightmare ensues.  The drivers disk that came with the motherboard runs just fine but the software simply won't install properly.  No network card, no sound, improper video.  I play around with it for a while to no avail.  Frustrating, because I need, at the very least a working LAN card so I can get all the updates, etc. I move on.

I drop the old hard drive in the machine to get the old data off (yeah I have alternative backups just in case).  Windows recognizes the drive after a BIOS confirmation and reboot.  However Win2k will **not read the drive**!  It's claiming that the old drive is unformatted and very dangerously offers to format it for me.  WTF?  The old drive is an older Win2k installation with NTFS... the exact same OS and file format that's installed on the new hard drive!  Screw you Windows!  

I pull out my Ubuntu 7.10 disk and install it onto a new partition on the new hard drive.  Ubuntu installs in less than 1/4 of the time it took me to get Win2k to its present and incomplete state.  It recognizes the LAN card, gets an IP addy and I'm on the 'net.  It automatically uses the sound card and sees all of the hard drives and partitions. It even recognized the Nvidia on-board video and asked me if I wanted to use the restricted drivers.  Too easy.  Doing this also confirms that my problems with the various hardware bits isn't a hardware issue, as they all work perfectly fine with Ubuntu.  It's a Windows issue.

I look at the old hard drive and Ubuntu happily gives me a directory listing of the old Win2k install that the new install claims is unformatted.  I proceed to copy all the data from the old install onto the new Win2k install from within Ubuntu.

I reboot into the new Win2k and it confirms the data is all there.  Thanks Ubuntu!

I then boot back into Ubuntu, get on the 'net and start searching for alternative drivers for the LAN card, sound and video.  I find something, download the files and transfer them to the Win2k drive.  I then boot back into Win2k, install the alternative drivers and cross my fingers.  Reboot.  The LAN card is now alive (yay!) and the video drivers appear to be working (yay!) but still no sound.  (Less important but still...)  I can proceed along to Windows Update and the rest of my install.

Sorry for the long post - I really did cut down on all the steps I took - I just gave the "highlights". ;)  

It's really sad that a free and "amateur" effort (Ubuntu) is required to get a "professional" system to actually work.  But I'm certainly glad of the existence of these "amateurs".  [IMG]http://www.freebeer.is-a-geek.org/graphics/thumbsup.gif[/IMG]

---

### Post by major_rocks on 2008-02-23
good story......i feel your pain, just on a much simpler level. recently i got an HP OfficeJet 6310 (network printer) i go through the whole ordeal of getting it setp on WindowsXP (40 minutes) .......astounding !! 

Once i'm done having lunch and more coffee i tried using the printer (in XP)  to scan and convert a 12 page document into .pdf format for an email. After 7 pages the scanner stops responding and so does windows....i figure WTF, i just spent 150 bucks on this hunk of crap. After a reboot of XP i try again...same results and 3 more attempts](*,)](*,)](*,)](*,),....screw this i'm gonna try in Ubuntu.

15 minutes later i have the printer installed, software (gscan2pdf) to help me get things done, and all 12 pages scanned and converted to .pdf, and off in the mail.......RIGHT ON:!::!::!:

---

### Post by MONODA on 2008-02-23
yeah i remember when i used my ubuntu 7.04 cd to recover my files from my vista installation. great story btw

---

### Post by wolfen69 on 2008-02-23
the next step is to get these people to lose the zero,(windows) and get with the hero.(ubuntu) ive  already talked a couple customers into using ubuntu.

---

### Post by zero244 on 2008-02-23
A familiar story.........Ive used a Ubuntu Live CD to recover files from a XP partition. I have also done what you did......download drivers from within Ubuntu that would not install off the cd.
With a install Windows you never really know what is going to happen. Most times it will install without a hitch. Then sometimes weird things happen.
If you didnt have the savvy to use Ubuntu to work around the W2K problems you might of lost some data.
Good luck.

---

### Post by freebeer on 2008-02-23
Yeah, getting them to leave Windows (a hard task under normal circumstances) is hampered by a particular app they use.  There is no Linux client (I checked ;)) nor is there expected to be one at any time in the future.  I've already migrated them to **some** open source apps and that process will continue.  They are running Ubuntu/Samba as a PDC which replaced their ancient and dying NT box.

My next little project will be to see if I can't get that key app to function in a virtual machine.  If I can get that to work then there's no other technical barrier (perhaps one involving one person's use of a cell phone/PDA running Windows CE, I think).

---

### Post by freebeer on 2008-02-23
> **zero244 said:**
> 
If you didnt have the savvy to use Ubuntu to work around the W2K problems you might of lost some data.


I probably would not have lost any information, since before I did anything I rsync'ed the original disk's data to the server. I've often used Ubuntu before to access Windows drives for various and sundry reasons, so I knew I had my ace-in-the-hole.  I don't take chances with data.  ;)

---

### Post by jdrodrig on 2008-02-23
To be fair I feel forced to comment, how old is the build on that Win2K? five years old? if so, it is a bit unfair to compare it to the just released 7.10. Driver support has ofcourse improve as years pass.

---

### Post by freebeer on 2008-02-23
Actually, the old Wink2k install was about a year old and while slow, the file integrity (relatively speaking) was fine.  There's no reason that the new install should have refused to read the old hard drive.

With regards to the actual drivers, the drivers I was using (and so far failed to completely install) was for a new motherboard/cpu/chipset.  I wouldn't expect Win2k to have, natively, drivers for newer hardware.  But the driver install disk had versions supposedly for Win2k.  They were (and with regards to sound, still are) the problem.

---

### Post by stalkingwolf on 2008-02-24
> To be fair I feel forced to comment, how old is the build on that Win2K? five years old? if so, it is a bit unfair to compare it to the just released 7.10. Driver support has ofcourse improve as years pass.

WHY? winblows is supposed to be the be all end all, bees knees,super hero of OS's. Yet it constantly provides flawed software, copies files
to locations it cant even find, and in general is so FUBAR it is a wonder it operates at all.  However if you wish to spend the $$$$$$$$$$$$$$$$$
it can be fixed.  IF you can wait and dont mind " press 1 for english"

---

