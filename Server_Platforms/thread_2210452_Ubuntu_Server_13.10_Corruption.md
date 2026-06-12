---
title: "Ubuntu Server 13.10 Corruption"
date: 2014-03-10
forum: Server Platforms
---

### Post by bknoll4 on 2014-03-10
I recently installed Ubuntu Server 13.10 on a machine with new hardware but I am having issues. Mainly, after a random amount of time, seems anywhere between an 1-3 hours, it seems that the OS gets corrupt. I say this because when I try to click anything there is a flash and nothing happens. I try a hard reset but then it eventually just gets to a black screen with the message "reboot and select proper boot device or insert boot media in selected boot device and press a key". The only thing that works is is completely powering off and then back on and it is good for another couple hours. Here is what I have:

Software:
- emacs
- Ubuntu desktop
- Plex Media Server 0.9.9.5.411 
- openSSH
I believe that is all I installed, the rest would be the "out of the box" software

Hardware:
- OS installed on 64GB SSD
- NTFS formatted/mounted 3TB HDD
- 2 non formatted and not mounted 3 TB HDDs (Just haven't set them up yet)
- 8 GB memory

I've used Linux in the past but I'm not very familiar with Ubuntu and I'm not sure where to look. I've tried looking at logs in /var/log and also plex media server but haven't really found anything that jumps out at me.

Does anyone have any suggestions or possible knows what I'm dealing with? Any help would be greatly appreciated!

Thanks!

---

### Post by CharlesA on 2014-03-10
Run a memory test and see what that returns. You could be able to do that test on a Ubuntu LiveCD.

---

### Post by bknoll4 on 2014-03-11
I ran the memory test overnight and there were 0 errors.

---

### Post by CharlesA on 2014-03-11
Any reason you chose 13.10 for a server? I'd try 12.04 and see if the same thing happens.

---

### Post by bknoll4 on 2014-03-11
No specific reason for why I chose 13.10.

I have now installed 12.04 and will let it sit without installing any additional software. If it seems to be working I'll install the software and see if the same thing happens.

---

### Post by steeldriver on 2014-03-11
Do you really need ubuntu-desktop (with all its dependent bits... office apps and so on) on a server? if you feel that you need a GUI then have you considered something more minimal like lxde-core?

---

### Post by bknoll4 on 2014-03-11
Well that didn't take long, I ran into the issue again. This time on 12.04 and nothing installed (with the exception of ubuntu-desktop)

As for whether or not I need ubuntu-desktop, unless you think it is related to my problem I would prefer to keep using it. Just a personal preference.

---

### Post by CharlesA on 2014-03-11
That kinda points to some sort of hardware problem, does the keyboard lights flash when it freezes up?

---

### Post by bknoll4 on 2014-03-11
I'll keep an eye on the keyboard lights although it is hard to pinpoint exactly when the failure happens. To rule out the hard drive, I am installing the OS on a different hard drive.

---

### Post by CharlesA on 2014-03-11
Yeah the other thing I would do is check the hard drive with the manufacture's diagnostics, but if you are swapping it out, that'll rule it out as a cause.

---

### Post by bknoll4 on 2014-03-12
So after keeping it on overnight I have not had any issues so far. I'll check the other hard drive with the manufacture's diagnostics but it was almost certainly the issue. Thank you for all of your help!

---

