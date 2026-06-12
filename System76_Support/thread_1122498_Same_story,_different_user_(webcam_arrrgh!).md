---
title: "Same story, different user (webcam arrrgh!)"
date: 2009-04-11
forum: System76 Support
---

### Post by flukeairwalker on 2009-04-11
Just wiped my hard drive and did a completely clean install of Ubuntu 8.10 on my Panp4. So far (in order) I have updated the system, installed the nVidia driver, installed and ran the System76 driver program, and added the Medibuntu repository. Also I took some programs out of the standard repository, including Cheese and Camera Monitor. Now I'm trying to get my webcam to work on Cheese and nothing is happening. I know that at one point the webcam did work with Cheese. Here's some stats I've seen be asked before.

Running lsusb in terminal I get:

Bus 008 Device 002: ID 0402:5606 ALi Corp. 
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 004: ID 04fc:05d8 Sunplus Technology Co., Ltd 
Bus 004 Device 003: ID 0409:005a NEC Corp. HighSpeed Hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 147e:2016  
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Fn+F10 gets me:

Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 004: ID 04fc:05d8 Sunplus Technology Co., Ltd 
Bus 004 Device 003: ID 0409:005a NEC Corp. HighSpeed Hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 147e:2016  
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

So I can assume the webcam is turning on and off, right?

---

### Post by Eldera on 2009-04-11
Did you see the thread TA posted a few weeks ago:[thread]1072437[/thread]

I hope maybe this info may help. I personally am not using the webcam and these forums are pretty inactive on the weekend. Perhaps someone will see your post on Monday who is more knowledgeable about this issue.
Have a nice day, Eldera

---

### Post by flukeairwalker on 2009-04-11
Thanks for pointing me to that post. I tried doing as it suggested, closing all programs and shutting the webcam off and on. TO make sure no webcam program was running I checked the System Monitor and even went as far as uninstalling Camera Monitor just in case. Ekiga ran some tests but didn't tell me anything, then it crashed when I clicked to view the cam. Cheese just has that foot in the center of the screen. I can't test Skype because there's no one that I know online, but I'm going to think it doesn't work either.

What's up? The camera worked originally when I got the computer, so there's no reason it shouldn't work now. The only thing I can think of that's different is the new nVidia driver, which I don't believe is the issue because the camera was still working after the driver upgrade and before the hard drive wipe.

---

### Post by thomasaaron on 2009-04-13
flukeairwalker,

What nVidia driver are you using? If you're not using the 177 driver, try reverting to it and see if it solves the problem.

System > Administration Hardware Driver.

---

### Post by flukeairwalker on 2009-04-15
I downloaded the 180 driver because it was the most recent one. I'll let you know if reverting to 177 fixes the problem.

---

### Post by flukeairwalker on 2009-04-15
Okay, so I reverted to the 177 driver and at least now I get the "no camera found" message as opposed to the perpetually swelling toes. I'm going to call that progress. When that didn't work, I ran the System76 driver installer, gave the computer another reboot and checked. Same thing. Then I ran lsusb to make sure I could at least turn on the webcam, which I can.

So what's next?

---

### Post by Guille Damke on 2009-04-15
Hi, 
I am suspecting that this is a problem with the Pangolin. It seems to be the same problem that I had and [DESCRIBED HERE]("http://ubuntuforums.org/showthread.php?t=1020436") (and still have not solved because I think I'll have to send my panp4n to system76 for repair but I am using it everyday :( ). 

Thomasaaron, how should a working webcam in the Pangolin be listed by lsusb (in the shop machine you have)? I am asking because the same problem was posted last week by another user, and the 3 known cameras with this problem are listed as "Ali Corp." when they not work anymore.
Probably you can try to reproduce the error (I think it's an error), because **as far as I remember** I installed "amsn" and tried to use the camera there when I had this trouble, the weird thing is that the camera was recognized by lsusb but not working under any program even after reinstalling Ubuntu twice after it broke. Also, you can ask the other 2 users about what camera software they installed/ran before getting this problem.

Thanks,
Guille.

---

### Post by thomasaaron on 2009-04-15
The listing in lsusb has actually changed (or it is different on different panp4 notbooks). 

Try running this command from a terminal...
echo options uvcvideo quirks=2 | sudo tee -a /etc/modprobe.d/uvc 

Then reboot. Did that fix it?

---

### Post by Guille Damke on 2009-04-15
Hi,

It did not fix it in my panp4n.
Should I just delete the file or only the line in /etc/modprove.d/uvc ?

---

### Post by thomasaaron on 2009-04-15
Yes. Delete it.

I'm not sure what is going on with your machine. Jaunty is coming out. You might want to just do a fresh install when it is released. That should fix it if it is a config issue.

---

### Post by Guille Damke on 2009-04-15
Hi Thomasaaron,

I agree with you and I had thought about the Jaunty option a while ago. I hope it works. If I just try Jaunty booting in LiveCD, should the camera be recognized without instaling?( I don't know if I have too much free time at the end of the semester for doing this).
Anyway, I would like to hear from the other two guys, and know if they could fix the camera.

---

### Post by thomasaaron on 2009-04-15
Yes, I just checked, and it should work out of the box with Jaunty, so the Live CD is a great idea. 

Don't forget Fn-F10. Not sure if it was on or off by default.

---

### Post by flukeairwalker on 2009-04-15
I ran the command you suggested Thomas, and I got this:
options uvcvideo quirks=2
I'm going to reboot now and let you know if I get anything.

Edit:
After reboot, camera still won't work. Camera Monitor doesn't show like it's turning on.

Will upgrading to Jaunty definitely fix this problem? Should I upgrade, format the "/" partition, or format the whole computer?

---

### Post by Guille Damke on 2009-04-15
Hi flukeairwalker,

Can you still see the camera turning on and off when hitting Fn+F10? (running the command lsusb). We don't know if upgrading to Jaunty will fix the camera, but it's worth trying the new version because it's going to be released in less than 10 days.
A second question, do you remember which program(s) that use the camera you tried to run or install before your webcam broke?

---

### Post by Brian_Newbie on 2009-04-16
I think I'll wait to see if Jaunty fixes my webcam on my Panp4n as well. 

My built-in Bison cam was working perfectly until I downloaded Cheese. At that point my bison cam became a "usb2.0 cam" and when I ran the lsusb command the word "Acer...." changed to "Ali Corp."

Interestingly my external usb plug-in Rocketfish webcam works perfectly in aMSN, GyachE and Cheese. I didn't have to configure anything. I just plugged it in and it worked!!

I'm hoping the bison cam isn't working because of some configuration glitch which Jaunty corrects.

Brian

---

### Post by flukeairwalker on 2009-04-16
Guille Damke,

The programs I'm running now are the same I was running before I killed the computer. I use Skype mainly, but I also use Cheese sometimes, and I have Camera Monitor for paranoia's sake. They all used to work before the kill but are not working now. Fn+F10 does turn the camera on and off. I can't say what it used to say before since I never had to check, but like Brian_Newbie, it reads "Ali Corp" under the lsusb list, and as USB 2.0 Webcam under the preferences menus.

I will upgrade to Jaunty once it is confirmed safe by System76, but my issue is that it used to work under Intrepid, so it should work as well now.

On second thought, there is a difference I can think of. My computer was shipped with the Bonobo BIOS instead of the Pangolin BIOS, and I had to make the switch once the issue was brought to my attention. Even though it still worked once I switched to the correct BIOS, upon reformatting, the webcam failed. I don't know, I'm just throwing that out there. Might that be a possibility?

---

### Post by thomasaaron on 2009-04-16
> it reads "Ali Corp" under the lsusb list, and as USB 2.0 Webcam

I'm pretty sure this is a red herring. I've seen both listings on our shop computers, and they cams work either way.

Try running from a live Jaunty CD and see if it works. It should.

---

