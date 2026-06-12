---
title: "Ubuntu gets respun due to MAJOR BUG"
date: 2010-04-30
forum: The Cafe
---

### Post by Digikid on 2010-04-30
[http://www.phoronix.com/scan.php?page=news_item&px=ODE5Ng](http://www.phoronix.com/scan.php?page=news_item&px=ODE5Ng)

Funny....do not see this news on the forums anywhere.

While you are at it....fix the Radeon 5000 Series bug as well.

---

### Post by philinux on 2010-04-30
> **Digikid said:**
> [http://www.phoronix.com/scan.php?page=news_item&px=ODE5Ng](http://www.phoronix.com/scan.php?page=news_item&px=ODE5Ng)

Funny....do not see this news on the forums anywhere.

**While you are at it....fix the Radeon 5000 Series bug as well.**

You would have seen it in this forum. It's closed now.

[http://ubuntuforums.org/forumdisplay.php?f=377](http://ubuntuforums.org/forumdisplay.php?f=377)

There were some threads in CC and ABT.

The devs dont look here. Have you bugged your problem at launchpad?

---

### Post by P4man on 2010-04-30
You mean, ubuntu **got** respun?

---

### Post by Digikid on 2010-04-30
> **P4man said:**
> You mean, ubuntu **got** respun?

No.  I meant what I typed out.

---

### Post by sgage on 2010-04-30
The grub problem was discovered yesterday very early, quickly fixed, and the iso's respun before release. The Phoronix article is from yesterday. There is no "respinning" going on today.

---

### Post by doas777 on 2010-04-30
ummmm, where were you yesterday morning (PDT)? I was in several threads discussing the bug and the status of the testing and respin. one was close to 200 pages long.

they made the right choice to patch the ubiquity/mig assistant bug, but I am not sure I would call it a major bug either way. the workarounds were easy. the biggest problem was that there was no good way to inform those who needed to know, and it does run against the users expectation, so notification is important.

---

### Post by philinux on 2010-04-30
Thread moved to community cafe.

---

### Post by eriktheblu on 2010-04-30
Let me see if I have this right:
Ubuntu installs were not adding other OSs to Grub.
Other OSs could be added after install with sudo update-grub.

And this is a "major" bug?

---

### Post by P4man on 2010-04-30
> **eriktheblu said:**
> Let me see if I have this right:
Ubuntu installs were not adding other OSs to Grub.
Other OSs could be added after install with sudo update-grub.

And this is a "major" bug?

Windows has been shipping with the same bug for 20 years :)

---

### Post by ikt on 2010-04-30
> **eriktheblu said:**
> Let me see if I have this right:
Ubuntu installs were not adding other OSs to Grub.
Other OSs could be added after install with sudo update-grub.

And this is a "major" bug?

Well naturally, I'd like to see how you would react if you installed windows on your computer assuming it would dual boot only to discover your ubuntu partition missing. I personally, would wet myself.

---

### Post by 10027586 on 2010-04-30
New users won't know how to do it and likely won't always know about the forums. And yes Windows has had this showstopper for quite some time now.

---

### Post by Digikid on 2010-05-01
Do not get me wrong....I am not here to cause trouble I just thought that it was strange that it was NOT mentioned and it seemed that Canonical was trying to hide something from us.

Plus I was HOPEFUL that they would listen for once and fix the issue with Digital connections on Radeon 5000 series cards ( Cannot use DVI or HDMI with them have to use a VGA connection ) while they were at it.

---

### Post by Danny Dubya on 2010-05-01
> **P4man said:**
> Windows has been shipping with the same bug for 20 years :)

You know what, I think I have the same bug as Windows. OHSHI--be right back, gotta stab someone that's better than me!

---

### Post by Yes on 2010-05-01
> **Digikid said:**
> Plus I was HOPEFUL that they would listen for once and fix the issue with Digital connections on Radeon 5000 series cards ( Cannot use DVI or HDMI with them have to use a VGA connection ) while they were at it.

Is that a bug with Ubuntu or the graphics driver?

---

### Post by Khakilang on 2010-05-01
Yeah I saw the news and upgrade it anyway since I don't do dual boot what the heck.

---

### Post by Digikid on 2010-05-01
> **Yes said:**
> Is that a bug with Ubuntu or the graphics driver?

Honestly I do not know.....but it needs to be fixed and since it only happens with Ubuntu I guess the finger gets pointed at them.

---

### Post by JT9161 on 2010-05-01
> **Digikid said:**
>  Canonical was trying to hide something from us.

Trying to hide a bug that has been posted to the Internet for all to see ?

---

### Post by Foster Grant on 2010-05-01
> **Digikid said:**
> Do not get me wrong....I am not here to cause trouble I just thought that it was strange that it was NOT mentioned and it seemed that Canonical was trying to hide something from us.

There was at least one thread here in the Cafe on Thursday. :)

---

### Post by doas777 on 2010-05-04
> **Digikid said:**
> Honestly I do not know.....but it needs to be fixed and since it only happens with Ubuntu I guess the finger gets pointed at them.

not really. the ATI driver is written by ATI so if there is a problem with the quality or features of the driver, it pretty much lies with the company that wrote it. there is some ubuntu custom code in the kernel and in userspace, but for the most part, if it works on vanilla 2.6.31-20, then it should work in ubuntu. when you say it only happens with ubuntu, does that mean you have tested it with other linux distros running the same kernel version you use in ubuntu?

and the "ubiquity/migration assistant" bug was pretty visible and transparent. I felt like they were providing us with info as up to date as possible.

here is one of the artifacts of this bug:
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/570765](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/570765)

and we got updated information on the respin and testing process here:
[http://iso.qa.ubuntu.com/](http://iso.qa.ubuntu.com/)

---

