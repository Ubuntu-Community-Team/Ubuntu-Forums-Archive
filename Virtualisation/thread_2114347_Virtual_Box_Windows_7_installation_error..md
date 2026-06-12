---
title: "Virtual Box Windows 7 installation error."
date: 2013-02-09
forum: Virtualisation
---

### Post by ChrisInNevada on 2013-02-09
Hello all!  I am trying to install window 7 to virtual box.  Although I have the disk in the disk reader, I keep getting the error message "Fatal:  No Bootable Medium Found!  System halted.  Any ideas?

---

### Post by QIII on 2013-02-09
Thread moved to Virtualisation



My first guess would be that you did not set up your CD/DVD drive in the Storage tab.

Stop the VM.

Select the VM in the setup GUI.  Go to Settings.  Go to Storage.  You should see "Controller: IDE".  Under that I suspect you will see a disk symbol labeled "EMPTY".

Select that.  Then go to the "Attributes" box.  Look for "CD/DVE Drive".  To the right of that, by the edge of the GUI, you should see another disk symbol.  Click on that and select your CD/DVD device from the drop-down list.

I usually select "Passthrough".

Click "OK" in the bottom right.

---

### Post by ChrisInNevada on 2013-02-09
Thanks for the response but I am completely new here and totally lost beyond " Stop the VM."  The rest of your message is Greek to me.  Would you be so kind as to put that in laymen's terms for me, please?

---

### Post by QIII on 2013-02-09
We'll go step by step, then.  I guess I rattled that off pretty quick.

Close VirtualBox and open it up again.  Let me know when you've done that.

---

### Post by ChrisInNevada on 2013-02-09
Thanks.  I am at the "Controller: SATA and I see "windows 7.vdi" below it.

---

### Post by ChrisInNevada on 2013-02-09
Under Controller IDE it says it's empty.

---

### Post by QIII on 2013-02-09
OK.  I made a mistake.  You want to be looking under Controller:IDE.

Do you see a disk icon there?

---

### Post by ChrisInNevada on 2013-02-09
The only disk identified is under SATA.

---

### Post by QIII on 2013-02-09
OK.  We're typing at the same time.  Fun, huh?

Click on the disk icon under IDE that says Empty.

---

### Post by ChrisInNevada on 2013-02-09
I guess I should check the CD box.

---

### Post by ChrisInNevada on 2013-02-09
I did and have selected the CD box which had been unchecked previously.  Thanks!  I'll see if this works.

---

### Post by QIII on 2013-02-09
Now you should be able to insert your CD/DVD and start the VM.  It will boot from the CD/DVD.

---

### Post by ChrisInNevada on 2013-02-09
"Could not read from the boot medium  System Halted"

---

### Post by QIII on 2013-02-09
Does that disk icon under IDE still say "Empty"?

---

### Post by ChrisInNevada on 2013-02-09
Yes

---

### Post by QIII on 2013-02-09
OK.  I didn't explain it well enough then.

Click on the disk icon under IDE.

Move your mouse to the right a bit and you'll see "CD?DVD Drive".  A bit further right and you'll see another disk icon.

Do you see that?

---

### Post by ChrisInNevada on 2013-02-09
Yes.  Should I choose "Host Drive Optiarc"?

---

### Post by QIII on 2013-02-09
Yes.  If that is your CD/DVD device.

Then click OK.

---

### Post by ChrisInNevada on 2013-02-09
My IDE is "secondary".  Should it be master or are we good with "secondary"?

---

### Post by QIII on 2013-02-09
We're good with that.  Here's what it looks like for one of mine.

---

### Post by ChrisInNevada on 2013-02-09
CHA-CHING!!!  We have a winner!  Now I'm getting some message about 24 bit mode color vs optimum 32 bit mode color.  Thanks for your awesome help!  "Windows is loading files" :D

---

### Post by QIII on 2013-02-09
That's what we're here for.

If it all works out, please come back and mark your thread "Solved" by clicking on "Thread Tools".

That will let someone else know that they might find a solution here.

---

### Post by ChrisInNevada on 2013-02-09
Error Message:  "Windows failed to start.  A recent hardware or software change might be the cause.  To fix the problem:

Blah, blah, blappity blah...it wants me to restart and repair Windows.

---

### Post by QIII on 2013-02-09
OK.  This sometimes happens.

Is this a disk that came with an OEM computer?  A Dell or something?

---

### Post by ChrisInNevada on 2013-02-09
Precisely!

---

### Post by ChrisInNevada on 2013-02-09
I wish they'd just play "nice" together.

---

### Post by QIII on 2013-02-09
There you have it.

Unfortunately, I don't think you can proceed, for two reasons:

First, Microsoft's EULA generally proscribes the use of OEM installation disks in a virtual machine.

Second, that Dell disk is tailored by Dell to check to see that it is being installed on a Dell machine.  That's why you are getting the error.

Unfortunately, you really should have a retail disk to use virtualization.

---

### Post by ChrisInNevada on 2013-02-09
Hmmm...so I just wasted an entire day or several.  Screw it!  I need to use this OS.  I have been under extreme cyber attack on Windows.  I guess I'll have to dual boot then.  Such a pain.  Thanks for your help.  Now I am off to read up on "dual boot".

---

### Post by lost sheep on 2013-07-05
hello there
I'm having the same problems.....windows 7 is not installing
I checked the CD I'm using and it seems to be neither a DELL nor an OEM disk...it should be an "original"
could there be any other reasons for Windows 7 not being installed in my virtual box???
I'd be very very very grateful if some hero-type-of-person could help me :)

---

### Post by SeijiSensei on 2013-07-05
Where is the DVD from?  Did you specifically buy a [fully-licensed copy of Windows]("http://www.newegg.com/Microsoft-Operating-Systems/BrandSubCat/ID-1149-368")?  If you are trying to install a DVD you created from the images that came with your machine, it will almost certainly not install in VB.

---

