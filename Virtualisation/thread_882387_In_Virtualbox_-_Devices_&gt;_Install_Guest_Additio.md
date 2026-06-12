---
title: "In Virtualbox - Devices &gt; Install Guest Additions... doesn't do anything."
date: 2008-08-06
forum: Virtualisation
---

### Post by charliedelong on 2008-08-06
SOLVED - See my last post.  Thanks again everyone!

I pretty much summed up my issue in the title.  I installed XP as a guest OS within my Ubuntu installation (host OS).  When I went into Device Manager it says that the video driver is not found.  I did some googling and came across the info that said I just had to install the "Guest Additions" into VirtualBox.  

I followed multiple postings that all said the same thing (even the part about being patient with it because it is sometimes slow) and got no response at all when I click: Devices > Install Guest Additions...

I was looking for some suggestions.  About that "being patient" thing... I have been waiting for over an hour...

Thank You all in advance!
Charlie

---

### Post by eightmillion on 2008-08-06
Look in the folder **/usr/share/virtualbox/** and see if you have **VBoxGuestAdditions.iso** in there. If it's there then try mounting it manually by clicking Devices>Mount CD/DVD-ROM>CD/DVD-ROM Image... and selecting that file.

---

### Post by Victormd on 2008-08-06
When you choose "install guest additions" virtualbox automatically mounts a virtual drive, but if you've disabled autorun in windows, you'll have to go to the drive and double click to install...

---

### Post by overdrank on 2008-08-07
Moved to Virtualization :)

---

### Post by charliedelong on 2008-08-07
Thanks for all the quick replies!

I looked for the folder /usr/share/virtualbox/ and it doesn't exist...  I had some trouble getting the VirtualBox working, so I don't know if there was an error or something.

I also checked the (guest) XP system to make sure that autorun was enabled.  I even went as far as checking the registry to be safe... 

Is there somewhere that I can manually download the VBoxGuestAdditions.iso file and then just mount it myself?

---

### Post by eightmillion on 2008-08-07
I uploaded the file [here]("http://www.filedropper.com/vboxguestadditions_1"). I feel your pain. That file is nearly impossible to find online. I don't know why sun doesn't just have it available for download on their site. Maybe they do and I just can't find it.

---

### Post by Victormd on 2008-08-07
That's odd. Are you using the OSE (from the repos) or PUEL (from sun website) version? I've always used the PUEL version (due to USB support) and never had any problems with the guest additions. If you're not using the PUEL, you can download it from [here]("https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI").

---

### Post by charliedelong on 2008-08-07
I downloaded the .iso file and it worked flawlessly... (Thanks eightmillion) I'm wondering what the repercussions of me hosting that file on my website as a service to all would be...    

For anyone else that may be wondering - I am using the version of VirtualBox from the Sun site, and aside from this little glitch (and some headache's installing it) it is one of the most amazing programs I have ever used.  

For now I think I will put that link to download the file on one of my site's... probably clerksblah.com if anyone's interested...

Well thank you all for all the great help.  Maybe some day I will get to a point where I can answer some questions on here!

-Charlie

---

