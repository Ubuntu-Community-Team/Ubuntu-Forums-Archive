---
title: "Darter Lockup . . ."
date: 2007-04-24
forum: System76 Support
---

### Post by MarkID on 2007-04-24
Any word on the fix for the Darter lockup after upgrade to Feisty?  (It seems kinda silly that I've got to keep a CD in there.)

---

### Post by jml on 2007-04-24
I sent System 76 an e-mail to days ago, and they responded yesterday saying that a fix for their customers should be ready in a few days.  Here is a copy of their response to me.

We're working out the best way to send down the fix.  The process will be Upgrade/Install Feisty > Apply Fix.  Applying the fix will most likely be simply installing the System76 driver.  It will be transparent to the user.  We'll post in our ubuntuforums.org forum, our forums, and probably in our upgrade directions (or possibly just remove the notice at the beginning: 

As soon as they make the fix available, I'll take the plunge and upgrade to Feisty.

Joe

---

### Post by thomasaaron on 2007-04-24
We will have it done soon.
Hang tight, and thanks for your patience.

Best,
Tom

---

### Post by Liff on 2007-04-25
How will the official fix affect those of us who applied the fix listed in the launchpad discussion?

---

### Post by thomasaaron on 2007-04-25
We are taking into consideration that some folks may have applied the aforementioned fix.
Don't worry, we will be careful.

Best,
Tom

---

### Post by thomasaaron on 2007-04-25
We are taking into consideration that some folks may have applied the aforementioned fix.
Don't worry, we will be careful.

Best,
Tom

---

### Post by AusIV4 on 2007-04-25
Yeah, I'm looking forward to a fix for this. Keeping a CD in the tray doesn't seem to help any in my Gazelle Value, and this is the last Feisty bug that needs to be worked out before I'll be ready to switch.

---

### Post by Rotarychainsaw on 2007-04-28
seems like the new driver fixed this. It only blacklisted some module though, which I guess reverts to the older module? I don't really care, it seems to work.


edit - ON second thought, Im getting some weird behavior that could be related to this. Investigating...

---

### Post by Rotarychainsaw on 2007-04-29
OK, I wouldn't recommend using the driver. It left me with some large problems. I couldn't read off the cd drive at all, and the darter would still lock up (even with a cd in the drive) if left on for a long time. I finally got back to the original driver, but I almost made my thing unbootable. Be wary.

---

### Post by jgordon510 on 2007-04-29
I had problems with the new driver also.  Really bad lockups accompanied by a dmesg error, something like "hbd: command error and ide:failed opcode".

It's working okay now, but I might still have problems.  It started working after I did two things:  I took the cd out of the drive, and I ran the driver installation again.  I did not downgrade.

---

### Post by jml on 2007-05-02
I experienced lockup several times during my upgrade to Feisty.  Redownloading the System 76 driver and rebooting solved my problem as well.

Joe

---

### Post by Rotarychainsaw on 2007-05-03
Hmm interesting. I'm pretty sure I did have a cd in when I ran the driver. I looked at the code in the driver to see what it did though, and it looks like it only blacklists the newer module. I confirmed it was blacklisted and rebooted a couple of times and it still was messed up. 

Im gonna wait a few more days. Keep me updated please.

---

### Post by thomasaaron on 2007-05-03
Thanks for the information.
I'll get this information to the programmer. He's out of the country for a couple weeks, but I'll get him started on it.

Is anybody else having this problem?

Best,
Tom

---

### Post by crichell on 2007-05-03
Thank you for reporting the problem.  Please run the following command and post your output.

lsmod | grep piix

---

### Post by Rotarychainsaw on 2007-05-04
I assume you'd want that output AFTER the driver has been run, and computer rebooted?

---

### Post by thomasaaron on 2007-05-04
Yes, please.

---

### Post by Rotarychainsaw on 2007-05-04
OK, I just tried the new driver lsmod gives me

piix                   10756  0 [permanent]


CD doesn't work again, only sees it as a blank CD or dvd.


edit - Hmm, if it boots with nothing in the CD drive, cd's are recognized. The computer locked way harder than ever before though right after. I will now try booting with nothing in the CD drive and not putting a cd in at all.

---

### Post by Rotarychainsaw on 2007-05-07
OK, as long as there is no CD in the drive, everything works. A cd drive is kind of important though...

---

### Post by thomasaaron on 2007-05-08
Hi, Rotarychainsaw.
(Curious about the origins of that username...)

That sounds like a major pain in the tush.

Let's take it to the next level and file a bug report on it. Carl will be back on the 14th and will begin digging into it. It's difficult for him to do it from abroad.)

Best,
Tom

---

### Post by Rotarychainsaw on 2007-05-08
Haha, my car at the time had a rotary engine ( yay rx-7's) but with the straight pipe it literally sounded like a chainsaw. It was not fun.

OK, should I file it, or are you gonna do that?

---

### Post by thomasaaron on 2007-05-08
You go ahead and post it if you don't mind.
That way you can provide as much info about your system as possible.

Best,
Tom

---

### Post by Rotarychainsaw on 2007-05-28
Looks like the new kernel upgrade fixes this, without having to use the system76 driver.

---

