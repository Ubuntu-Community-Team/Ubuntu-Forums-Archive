---
title: "Webcam support"
date: 2009-05-07
forum: System76 Support
---

### Post by fred.warren on 2009-05-07
How good is the webcam on the System76 laptops? I have an Aspire One and the webcam in linux looks good but the image refresh is S-L-O-W. 

Can I expect to be able to use skype, MSN with Kopete and Yahoo with Gyachi? 

Does anyone have any screen shots of what images look like from an IM session with a cam.

So far, Linux support for webcams have been disapointing. A UVC driver that barley works does not cut it. Does System76 actually have a a decent webcam?

---

### Post by thomasaaron on 2009-05-07
I think it performs reasonably well. Although, I've never used one under Window$, so I have nothing to compare it to.

From a tech support perspective, I've not heard any complaints about the quality or speed of the cam (except for some bugs that popped up a while back, which I believe have since been resolved).

We test with Skype, Ekiga and Cheese. As for the other software, I'll have to let other 76ers chime in on those.

---

### Post by hkarl629 on 2009-05-07
Tom,

Wish my webcam issue could be resolved.  SERP2
It's been a long time with several attempts that ended in frustration.

I don't know what it takes in manpower or resources but the fix was supposed to come via the System 76 driver(s).

Henry Karl Juelch
[email]hkj62429@gmail.com[/email]

---

### Post by thomasaaron on 2009-05-08
Henry, I know how much you want it. But we've not been able to figure it out for that particular computer. It's not for lack of trying.

That link you were looking at seems to have worked well for a lot of other serp2 users. It *should* work for your system as well. But it can't be put into the System76 driver unless it can be confirmed on our shop machines. And it doesn't work on our shop machine.

At this point, I don't have a lot of hope for getting it working on our shop machine. If you would like to send your computer in to us, I'd be happy to re-image your machine and try to get it working for you using the steps listed in other threads for that model. If it works, we could then put it in the system76 driver.

---

### Post by hkarl629 on 2009-05-09
Tom,

Your solution seems like the only possibility left to get the camera working. With the last set of instruction you supplied, I couldn't get past the first line which returned an error message. That was disappointing.

I feel this is a really good quality computer and whatever this glitch is, whether induced by me or an upgrade or some other factor, it should be resolved. This hardware is too good to be wasted.

So, what instructions do you have for me to send this back. I will use UPS as the carrier since they are convenient.

Henry Karl Juelch
[email]hkj62429@gmail.com[/email]

---

### Post by flukeairwalker on 2009-05-10
The webcam seems to be the only persistent glitch on the otherwise excellent Panp4 I own. Actually when I first received the computer the webcam worked just fine, and it was only soon after I changed the BIOS (it was accidentally shipped with a Bonobo BIOS instead of the Pangolin BIOS) did it conk out on me.

I don't know how important a webcam is for you. It's a very important piece of hardware for me since I'm stationed in Korea without my family, and even though it doesn't work for now I know Thomas and the other System76 guys have been working on this issue and will get it working very soon. I'd rather have one issue with my computer that's not game breaking than have lots of little issues that render my system nearly unusable.

To answer your question, back when my webcam *did* work, it worked just fine. I mean it's 1.3 megapixels, the image isn't going to be amazing, but the refresh rate was good, and in appropriate light the pictures it took were really good. Even chatting with my wife half a world away she said the video quality was good.

I hope my ranting helped you out. If not, then I hope it entertained. :popcorn:

---

### Post by thomasaaron on 2009-05-10
Henry, shoot me an email.

Flukeairwalker, try your webcam from a live 9.04 64-bit CD. It should work out of the box on that CD. If so, your hardware is good, and we can eliminate that as an issue.

As for the BIOS, if it *ever* worked after the BIOS upgrade, the problem is not the BIOS upgrade. My guess is that some arcane config file somewhere is donked.

---

### Post by fred.warren on 2009-05-12
flukeairwalker - Thanks, that is exactly the info I have been waiting to hear. 

My brother purchased a Dell Laptop. He fell in love with Linux when I installed it on the laptop. He tried to extend the warranty but was getting the run-around at Dell. So 29 days after purchasing it, he returned it.

He wants a system76 laptop. Just waiting for the refund to clear the bank now.

---

### Post by flukeairwalker on 2009-05-12
@ Thomas Aaron,

I can't remember precisely when the webcam stopped working but it was around the time I switched from the Bonobo BIOS to the Pangolin BIOS. And as for Jaunty, it's still doing the same thing in Jaunty that it was doing in Intrepid. Everything is detailed in the thread I made about my problem. I did a fresh install of the / partition when I installed Jaunty, and other than installing a few programs and all updates, I haven't really messed with it since most of my settings transferred over. It's probably still fresh enough to consider stock.

---

### Post by thomasaaron on 2009-05-12
Hi, flukeairwalker.

If you upgraded from intrepid to jaunty, it could have donked something. This has been a very rough upgrade.

We really need to find out if your cam works from a live CD. That's the determining factor right now as to whether you have faulty hardware.

---

### Post by bill516 on 2009-05-12
I have a new Pangolin and I use Skype on the Ubuntu 8.10 as installed by S-76.  Prior to that I used Skype on a Windows XP laptop by Asus.  Video and sound are quite comparable.  The major difference is just that Skype does not upgrade its Linux version as often as it does the Windows client.  Diferences, if any show up, might be as much attributable to that as anything else.  Suffice it to say I have not seen anything that disqualifies the Ubuntu/Skype combination, though I would like to use Ekiga just to compare.

I must say that 8.10 works sufficiently well that I am in no hurry to upgrade.  I also have not bothered to install Windows.  There is just no need in terms of what I do.

---

### Post by flukeairwalker on 2009-05-13
Skype has its faults. It's one of two programs I've ever had to force quit my entire time in Linux (the other being Second Life). It was the one necessary compromise I've had to make because my wife will not give up Skype even if it means she won't get to talk to me.

ThomasAaron,

I booted up Jaunty live from the CD and tried to view the webcam through Ekiga. I got nothing. Does that mean it's a hardware problem?

---

### Post by thomasaaron on 2009-05-13
Sounds like it. Did you press Fn-F10 and lsusb to make sure it was turned on? Also, I think you can download cheese from the live CD. You might want to try that. It should also work with no tweaking.

---

### Post by flukeairwalker on 2009-05-13
Doing the lsusb + FnF10 trick showed it was indeed turning on and off. I couldn't get Cheese to download, either through the terminal or through the Add/Remove programs option. I tried downloading it from the page but it required compiling and I am *not* going there. So I only tested in Ekiga.

---

### Post by thomasaaron on 2009-05-13
Does Ekiga detect your camera? (Go to edit > prefs > devices > video devices.) And are you configured as V4L2 and PAL (Europe)?

If so, my best estimation is that it is a hardware issue.

I'm sure it is not the BIOS upgrade, as we've upgraded many Pangolins without this problem occuring.

---

### Post by flukeairwalker on 2009-05-13
Make that three times I've ever force quit an application. Ekiga hangs when I click on preferences. I haven't even used Ekiga for anything but trying to see my webcam so it can't have been something I did to it. And I figure it can't be a BIOS issue because you guys would have figured out and solved that issue a while ago. If it's a hardware issue, what can I do? I'm in Korea and I made my Pangolin the center of my entertainment and communications center. I'd really prefer not having to give it up, but I will if it means solving the issue. Do you count APO boxes as a US address?

---

### Post by thomasaaron on 2009-05-13
We can't ship to APO addresses. We don't sell internationally because we are not yet able to provide hardware support internationally.

If you can ship the computer to a stateside family member or friend, we can provide shipping from and to them.

---

### Post by flukeairwalker on 2009-05-13
Wow. That's a hassle. Glad I didn't buy the extended warranty in that case. I also don't feel confident enough to open the laptop myself and find whatever's wrong with it. I guess I'll have to find a computer shop around here or buy an external one.

Anyone know of a webcam I can buy that will work with my Pangolin?

---

### Post by thomasaaron on 2009-05-14
Here is a good link on webcams...
[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

Anything that is UVC compatible should work well. Here is a link to some cams that work well with Linux...
[http://linux-uvc.berlios.de/#devices](http://linux-uvc.berlios.de/#devices)

---

### Post by flukeairwalker on 2009-05-14
That list is very handy. I'm lucky that the PX here at Camp Humphreys carries Logitech and Creative webcams, so I'll head over there tomorrow morning to see what I can find. I'll be taking this list with me when I shop for it. I cannot thank you enough for your help.

***Update***

I went to the PX just now and bought the Logitech Quick Cam Communicate. I just plugged it in, switched the settings, turned off the built in cam and it was ready to go. The picture looks good even in a dimmed room! It has a built in mic too which I haven't even tried to get to work, but I will try to, since most of the time I'm using my laptop through my projector/wireless keyboard and mouse. Again, thanks for all the help. I'm so relieved!

---

