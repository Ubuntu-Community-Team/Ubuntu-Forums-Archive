---
title: "Pangolin v3 Gutsy and sound"
date: 2007-10-16
forum: System76 Support
---

### Post by kperkins on 2007-10-16
I upgraded to Gutsy today, and everything is doing fine, except for sound.  I've traced the problem to the newest kernel (2.5.22.14), since sound works in kernel 2.6.20.16.  I tried the old alsa-base file with the new kernel, and it didn't do anything, but the new alsa-base (the one installed by gutsy) works fine with the old kernel. 
I hope the new system76 driver will fix this problem.
I may try running the sound.py manually to see if that fixes the problem.  Can't hurt, I guess.
(OK, can't do that, though I suppose I could run all the commands for the pangolin v3 , but I'll wait for the new driver)

---

### Post by thomasaaron on 2007-10-16
Do this. Don't forget to reboot.

[http://ubuntuforums.org/showthread.php?t=574531](http://ubuntuforums.org/showthread.php?t=574531)

---

### Post by kperkins on 2007-10-16
Thanks, it worked great. :D

---

### Post by gbutler69 on 2007-10-16
What worked great exactly? I'm trying to get sound working on my brand-spankin' new Pangolin V3 with Gutsy.

Also....any luck with the "Desktop Effects"?

---

### Post by thomasaaron on 2007-10-17
gbutler69, I think he means that this worked:

> OK. There are a couple of realtek patches that have to be incorporated into alsa.
I guess they didn't make it into Gutsy.

It's all in the sound.py file if you want to give it a go.

Look at the wget command for the panv3/gazv5. It downloads sys76-alsa.... That is the Alsa version you want. Patches are included therein. Then just compile it based on the commands in that section.

(Note: I believe it will also work with Alsa 1.0.15 (the latest stable: alsa-project.org). That version definitely has the patches included.

The driver that supports Gutsy should be out on Thursday if you want to go that route.


Regarding the graphics, there is a bug in compiz that causes problems with intel's 965 chipset. I believe the patch has already been submitted to compiz. From what I understand, you can make it work, but then your video players may not work.

We're working on this.

---

### Post by Zxaos on 2007-10-20
Following the instructions in the panv2 thread and running the appropriate bits of sound.py manually, Still no luck, although now in the sound control panel I get gconfaudiosink: Could not open resource for writing.

---

### Post by newsun on 2007-10-20
I am having the same problem with my panv3 upgraded to gutsy and sound does not work in2.6.22-14-generic, but it does still work in 2.6.20-16-generic. I have noticed there is some issue in general with the intel sound and gutsy, as seen in some bug threads with dell and lenovo laptops. Doe actually have a fix for this? I have tried configuring, make and installing the .15rc1 version of the alsa driver, but that did not work as well as installing the 2.1.1 sys76 drivers

---

### Post by Zxaos on 2007-10-20
I actually installed Gutsy over Feisty instead of upgrading, so I can't check the older kernel.

---

### Post by thomasaaron on 2007-10-22
Zxaos.

Have you tried running your system 76 driver? System > Admin > System 76 Driver.
Install Tab, Install Button.

---

### Post by thomasaaron on 2007-10-22
OK, folks.

It is getting pretty difficult to keep track of all of you, specifically which machine you have and which you've already tried.

There are huge differences between panv2's and panv3's. If the system 76 driver does not fix your sound, then I need to know what I'm dealing with in order to assist you.

So, please send me an email with:
1. Your computer model (*Look at your system 76 driver to determine the proper model/version)
2. A detailed description of what you've already tried.

---

### Post by Zxaos on 2007-10-22
> **thomasaaron said:**
> Zxaos.

Have you tried running your system 76 driver? System > Admin > System 76 Driver.
Install Tab, Install Button.

Yes. I'll email, too.

---

### Post by cwej on 2007-10-25
Regarding post:

Do this. Don't forget to reboot.

[http://ubuntuforums.org/showthread.php?t=574531](http://ubuntuforums.org/showthread.php?t=574531)
__________________

Do what exactly? The thread has lots of things...

My (latest outstanding) problem is upgrade to 7.10 with clean cd installation, and no resulting sound...yes loaded v2.1.1 system76 driver, install & restore & rebooted, no joy

system = panv3

I had earlier problem with cdrom, but solved with clean install as recommended...sound bad too that time, but I did manage to solve sound...I had found a forum post which recommended clean install and gave a terminal command to try -- being the numberskull I am, I forgot to bookmark the forum page, so when it worked, I forgot exactly what I did, besides reload the drivers...

If anyone remembers such a post, I'd sure like to try it again, whatever that was that worked the first time!

---

### Post by thomasaaron on 2007-10-25
cwej,

There really shouldn't be much to try. If you did a completely clean install (i.e. no remnants of Feisty whatsoever, including the old home partiton, etc...) and ran the driver and rebooted, you should have sound.

1. Did you fully update your system? 

2. Go to System > Prefs > Users and Groups, highlight your username and click properties. Make sure all boxes are checked (particularly the 'use sound device') box.

3. Double-click your speaker icon. Do you get an error message about gstreamer devices? If you do, your install/updates got hosed again.

4. If the sound control gui comes up, go to edit>prefs and make sure all boxes are checked. Then make sure nothing is muted.

If none of that works, something got hosed. Give me a call at support.

Best,
Tom

---

### Post by thomasaaron on 2007-10-25
Try this command:

sudo mv .gstreamer-0.10 .gstreamer.backup

Then re-run your system 76 driver and reboot.

---

### Post by cwej on 2007-10-25
Tom:


Answers:

1. Did you fully update your system? -- [COLOR="SeaGreen"]Yes did complete CD update, downloaded from Canonical, overwrote entire volume -- download was a Live disk version, should that matter?[/COLOR]

2. Go to System > Prefs > Users and Groups, highlight your username and click properties. Make sure all boxes are checked (particularly the 'use sound device') box. -- [COLOR="SeaGreen"]Done: all boxes are/were checked except, "Sent/Receive Faxes," and "Use tape Drive" [/COLOR]

3. Double-click your speaker icon. Do you get an error message about gstreamer devices? If you do, your install/updates got hosed again. [COLOR="SeaGreen"]-- Yes, get Error message: "No volume control GStreamer plugins and/or devices found."[/COLOR]

4. If the sound control gui comes up, go to edit>prefs and make sure all boxes are checked. Then make sure nothing is muted. [COLOR="SeaGreen"]-- Did not/cannot make it come up[/COLOR]

If none of that works, something got hosed. Give me a call at support. --[COLOR="SeaGreen"] OK, will try
[/COLOR]
Cheers, Chuck

---

### Post by thomasaaron on 2007-10-25
I've now talked to so many people about this that I can no longer keep everyone straight.  

We have the fix. Give me a call at support or send an email to support(at)system76(dot)com if you still need help with it.

---

### Post by cwej on 2007-10-25
Thanks; however, I just bit the bullet, downloaded and alternate installation disk, and installed in text mode-- everything works now. I should have done that from the start. Clean instal, text mode seems to be the best first resort...again, many thanks. I really appreciate System76 operating this forum. 
cheers, chuck

---

