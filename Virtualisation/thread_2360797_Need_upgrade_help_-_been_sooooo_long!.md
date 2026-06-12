---
title: "Need upgrade help - been sooooo long!"
date: 2017-05-08
forum: Virtualisation
---

### Post by Franknj229 on 2017-05-08
Hi all,

Please forgive my lack of expertise.  I'm in need of detailed, hopefully simple, instructions.  I created a VM probably about 10 years ago and have been running Ubuntu 10.04 guest in a Vista64 host ever since.  I know, I know....

I'll be upgrading my whole system soon, but for now, Ubuntu is on its last legs and it's such an old version I can't even upgrade it in stages, so I just want to do a clean install of the latest and greatest.  But how?

Please assume I don't even know step 1 of this process (since I probably don't) and try to be as "VMs-For-Dummies" as possible.

Thank you!

-Frank

---

### Post by #&amp;thj^% on 2017-05-08
First Download the .iso from here: [http://releases.ubuntu.com/16.04/](http://releases.ubuntu.com/16.04/)
The link I provided assumes you want a LTS=Long Term Support 5 years...and you wanted a Ubuntu Unity DE.
Or Download your choice.
Next follow this straight forward How to: [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

---

### Post by mörgæs on 2017-05-09
Keeping the unsupported Vista is a security hazard. Are you aiming for a clean install of 16.04.2, erasing the entire hard disk in the process?

---

### Post by Franknj229 on 2017-05-09
Yes, clean install of 16.04.2, erasing entire hard disk of guest.

Can anyone be a bit more "for dummies" than the post above?  It didn't work for me and it's probably because there are steps that you are assuming I know because they are so second nature to you.  The link provided ([http://releases.ubuntu.com/16.04/](http://releases.ubuntu.com/16.04/)) doesn't just bring up a single, obvious download.  There is an entire page of clickable links.  I chose "Desktop image for 64-bit PC (AMD64) computers", because I'm running Vista64, but It's not an AMD machine.  Anyway, it downloaded the file but then couldn't open it.  Should I be clicking on "32bit PC (i386) computers" instead?

Also, should I be starting completely from scratch, uninstalling VitualBox from my computer and then downloading it as if I never had it?  Or can I start from the point of just opening up VirtualBox and installing the new version of Ubuntu?

---

### Post by KillerKelvUK on 2017-05-09
Hey Frank, so you've download an CD image (.iso format) this is what you feed into Virtualbox as the installation disk for your new virtual machine.  The AMD64 reference can be misleading, it just means its 64bit and will work with AMD/Intel processors so you made the correct assumption.

Before you get to trying to install the new ubuntu guest check you are running the latest version of Virtual Box, if you are then there's no reason to uninstall it but if its out-of-date then go ahead and install the latest version.

Are you keeping Vista64 on the host or are you upgrading this as well?

---

### Post by SeijiSensei on 2017-05-09
> **Franknj229 said:**
> Anyway, it downloaded the file but then couldn't open it.  Should I be clicking on "32bit PC (i386) computers" instead?

Also, should I be starting completely from scratch, uninstalling VitualBox from my computer and then downloading it as if I never had it?  Or can I start from the point of just opening up VirtualBox and installing the new version of Ubuntu?

I would certainly upgrade VirtualBox to whatever version the website at [https://virtualbox.org/](https://virtualbox.org/) recommends.

Older machines won't typically support running a 64-bit VM even on a 64-bit version of the host operating systems.  Newer machines have a BIOS setting (like "VT-x virtualization") to enable this feature.  Use the 32-bit version of Ubuntu instead: [http://releases.ubuntu.com/16.04/ubuntu-16.04.2-desktop-i386.iso](http://releases.ubuntu.com/16.04/ubuntu-16.04.2-desktop-i386.iso)

Start the VB manager in Windows, then click on New to create a new virtual machine.  Give the machine a name and choose "Linux" and "Ubuntu (32-bit)" from the drop-down boxes.  Then either accept the defaults for memory and disk size, or increase them depending on the resources your machine has.    When the entry appears in the VB manager, double-click it to start the initial boot process.  You'll see a dialog asking you to specify the boot device.  Click on the little icon and find the ISO image you just downloaded.

Are you using VirtualBox to give 16.04 a test drive?  If so, it's probably better and easier to boot off the installation medium and choose "Try Ubuntu" when prompted.  That will use the whole machine but not make any changes to its disks.  If you don't have optical media handy, you can create a bootable USB drive from the ISO you download.  I use Rufus as recommended here: [https://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](https://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)

---

### Post by Franknj229 on 2017-05-09
After I finish downloading the file from [http://releases.ubuntu.com/16.04/ubu...sktop-i386.iso]("http://releases.ubuntu.com/16.04/ubuntu-16.04.2-desktop-i386.iso"), it's a blank icon on my desktop that windows doesn't seem to recognize.  When I click on it, I get the box with "Windows cannot open this file.... Windows needs to know what program you want to use to open it....."  I know clicking that icon is not the next step after downloading it, but it looked like the download didn't work based on the icon.  Once I open the VB program and follow the steps listed above by Seiji, will VB know how to open it?

Also, I'm not looking to "give 16.04 a test drive", so does that change the rest of the instructions in that paragraph? I just want to do a fresh install of the latest version of Ubuntu.  In that case, do I need to create a bootable USB drive?

Oh, and if I'm clicking "new" to get started and creating a new VM, do I need to somehow delete the old one so it's not taking up space on my computer?

Thank you!

---

### Post by deadflowr on 2017-05-10
If last you ran 10.04 as the vm, perhaps ignore Ubuntu  and try another flavor such as Ubuntu-mate or Xubuntu.
The difference in hardware requirements between Ubuntu 10.04 and 16.04 is staggering, imo.
Ubuntu mate and xubuntu require somewhere around the same that 10.04 did.
I'd go mate over xubuntu simply because it's almost the exact same environment as what 10.04 had.
(That environment was killed off by the gnome developers, but the mate devs took up arms to save it, and might have actually made it better)

---

### Post by mörgæs on 2017-05-10
Again, you are following a path which includes an unsupported Vista, 'unsupported' meaning that all security breaches found are left open. 

It's a sitting duck for the black hats and you should be aware of the consequences.

---

### Post by Franknj229 on 2017-05-10
Thanks deadflowr.  I'm going to try Ubuntu Mate.  I downloaded it to a memory stick, but I'm not sure how to proceed.  This link from a post above ([COLOR=#000000] [/COLOR][http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)) is very detailed and easy to follow, but it seems a bit out of date, or maybe just not universal, as the screen shots are just different enough from what I'm seeing on my machine that I'm not sure what to do at certain points.  Can you recommend another tutorial, or tell me what I should do differently regarding the download?  Should I have it on a mem stick or the desktop?  Does that even matter?

---

### Post by deadflowr on 2017-05-10
Is the file on the mem stick an iso?

Is the downloaded file only on a mem stick, or did it download to the Download folder as well?

In either case, it's just a matter of locating the iso file and setting it as the install media.

Just look for a file marked with .iso and that's it.

---

### Post by Franknj229 on 2017-06-04
Hi again.  Thank you all for the advice.  I'm still having some trouble, but I've really given a lot of thought to what [mörgæs]("https://ubuntuforums.org/member.php?u=939075") mentioned, about running Vista, and I would like to go full Linux at this point.

Just to be clear, before I dive down the rabbit hole, I'm going to backup what I need to an external HD and then, what....exactly?  Any suggestions on my main operating system?  Is anyone using a linux/linux setup with a VM?  Same operating system for both, or different flavors?

What's the best way to convert from Vista to Ubuntu, or whatever system I go with?  I'm not really sure what steps to take.

Thanks again!

Frank

---

### Post by Franknj229 on 2017-06-04
Sorry all.  I feel like I should start a new thread because this one has changed course, but I don't want to be a pest.

Let me clarify where I'm at:

I have completely cleared out my computer (desktop running Vista64). Everything I needed has been copied to an external drive.  I now want to convert entirely to linux.  I assume I will use Ubuntu.

I am requesting a dumbed down, step-by-step process for converting.  I appreciate the attempts above to help me set up the VM, but there were clearly steps "missing", in the sense that you might have assumed a particular step was obvious, but it wasn't to me, so I tried following the advice and was like, "hmmm, why isn't this working?"

So, where do I even begin?

Thank you!

Frank

---

### Post by mörgæs on 2017-06-04
If everything is backed up then just try the install and ask if something looks strange. 

When it all works post back and we can take a look at the virtual machine.

---

