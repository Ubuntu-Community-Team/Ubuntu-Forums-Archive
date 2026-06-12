---
title: "Best advice about rootkit"
date: 2010-12-07
forum: The Cafe
---

### Post by MooPi on 2010-12-07
I discovered a rootkit on my brother in laws laptop. I've never had to deal with rootkits before and I'm mining for the best utility to deal with them. Avast discovered the rootkit generator but this is probably just the tip of the iceberg.

---

### Post by cariboo on 2010-12-07
Back up the important data and re-install, you'll never know exactly what was installed or changed.

---

### Post by wilee-nilee on 2010-12-07
> **cariboo907 said:**
> Back up the important data and re-install, you'll never know exactly what was installed or changed.

+1 and there are rootkits that are not detectable as well.

---

### Post by szymon_g on 2010-12-07
> **cariboo907 said:**
> Back up the important data and re-install, you'll never know exactly what was installed or changed.

so why back-up it now, when data could have been already altered/destroyed?
format a disk, install a new operating system, restore important data from back-ups done before security was compromised.
ah, i suspect- since you know it's rootkit, you have an idea (or two) how it get into a system (was it up-to-date? maybe some "codecs" were installed? etc etc)

---

### Post by wilee-nilee on 2010-12-07
> **szymon_g said:**
> so why back-up it now, when data could have been already altered/destroyed?
format a disk, install a new operating system, restore important data from back-ups done before security was compromised.
ah, i suspect- since you know it's rootkit, you have an idea (or two) how it get into a system (was it up-to-date? maybe some "codecs" were installed? etc etc)

How do you know when it was compromised I ask?

I think the post is to back up the important stuff like media....etc, not any of the OS.

---

### Post by juancarlospaco on 2010-12-07
*Nice false positive you got there...*

---

### Post by szymon_g on 2010-12-07
> **wilee-nilee said:**
> How do you know when it was compromised I ask?

Maybe since the last scan of system?
not to mention: every detected virus has got a name- googleing it will help to determine when system could be infected (or, rather: could not).

---

### Post by MooPi on 2010-12-07
Both detections came back with negative google responses. Oddest part is they were strings of random numbers and letters. Nasty behavior when active, the usual, deactivate AV but the applet said it was active and working. msconfig disabled as well as task manager. I'll probably give the bad news to brother in law tomorrow after I dig a little deeper to see what else is happening.
To answer some of the responses, I have general time line of infection( possibly 2days ago) No idea what was being done when infected, (sister and brother in law very computer illiterate),and definite there was/is an infection, not a false positive. I'll double check personal data and wipe drive and restore.

---

### Post by wilee-nilee on 2010-12-07
> **szymon_g said:**
> Maybe since the last scan of system?
not to mention: every detected virus has got a name- googleing it will help to determine when system could be infected (or, rather: could not).

Your argument is in a perfect world, where all virus/malware/rootkits/bots....etc are all detectable and moopi or their kin have all these tools. You are arguing a moot point let it go.;)

---

### Post by matt_symes on 2010-12-07
MooPi

What OS?

---

### Post by MooPi on 2010-12-07
Vista, couldn't get into system controls earlier but found that UAC was disabled too. The digging continues. I'll check for DEP control as well.

---

### Post by inobe on 2010-12-07
malwarebytes to remove the kit and destroying the user account after creating a new one.

turn on uac.

---

### Post by jrusso2 on 2010-12-08
A lot of virus scanners are made for windows and give Linux false positives for rootkits thats why they are pretty useless.

---

### Post by MooPi on 2010-12-08
This was a Windows scan from my computer. Clean install on my machine and Avast scan of my brother in laws hard drive. I removed it from the laptop. I did however scan with clamav afterwards to get second look. It picked up additional virus that were lurking in some temp folders. Seems the addresses for Windows Update have either been deleted or changed , not certain yet. 
Malwarebytes ineffective in this situation, this seems to be a heavy hitter of a virus infection. Clean until 2 days ago and slammed hard with multiple bad guys. I've dealt with some minor foes before but this one is fairly involved virus. I'm still digging just to learn a thing or two because this will be a reload for certain.

---

### Post by chamber on 2010-12-08
If its a TDSS variant you could use something like TDSS killer, you would probably need a proper rootkit detector like GMER to confirm.

---

### Post by MooPi on 2010-12-08
Update: Found the source of infection, Camille Donatacci HOT naked photos and sex pics. And then my brother inlaw does the worst thing possible after the start of this mess, HE CHECKS HIS EMAIL UHHGGG.
I'm going to have a talk about this with him and try to keep from busting up in laughter.

---

### Post by matt_symes on 2010-12-08
> I'm going to have a talk about this with him and try to keep from busting up in laughter.

Yes. Good luck with that. ;)

---

