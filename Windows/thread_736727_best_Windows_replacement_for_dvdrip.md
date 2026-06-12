---
title: "best Windows replacement for dvd::rip"
date: 2008-03-26
forum: Windows
---

### Post by gobbles414 on 2008-03-26
Hi all,

I like to rip quotes and music from DVDs (that I own). In Ubuntu, I use dvd::rip to transcode the audio from a DVD to a .wav file. Then, I use an audio editor like Audacity to edit and export the clips as .flac files. **I need a similar freeware solution for Windows.** I've already installed the Windows version of Audacity. But I'm not happy with the combination of DVD Shrink and HandBrake for ripping. Also, I know that AC3 encoding is not lossless. But I would prefer to keep the rest of the ripping process lossless (e.g. AC3 => .wav => .flac).

Thanks in advance for your help!

---

### Post by tbroderick on 2008-03-27
Maybe try DVDDecrypter.  Doom9.org is a good place to start for free tools, codecs and forum help.

---

### Post by gobbles414 on 2008-03-27
> **tbroderick said:**
> Maybe try DVDDecrypter.  Doom9.org is a good place to start for free tools, codecs and forum help.

I would prefer to use a program that is being actively developed. Neither DVD Shrink nor DVDDecrypter are currently being actively developed. In my research, I came across a program called [DVD43]("http://www.dvd43.com/"). I was going to try using it with HandBrake. But DVD43 is incompatible with my OS -- Vista 64-bit. Any other ideas...? I would be willing to use an inexpensive shareware program. It doesn't take much time in the Windows world for one to realize how useful Ubuntu really is. :)

---

### Post by timzak on 2008-03-28
> **gobbles414 said:**
> I would prefer to use a program that is being actively developed. Neither DVD Shrink nor DVDDecrypter are currently being actively developed. In my research, I came across a program called [DVD43]("http://www.dvd43.com/"). I was going to try using it with HandBrake. But DVD43 is incompatible with my OS -- Vista 64-bit. Any other ideas...? I would be willing to use an inexpensive shareware program. It doesn't take much time in the Windows world for one to realize how useful Ubuntu really is. :)

Are you sure?  The latest version of DVDFabHDDecryptor is dated March 22, 2008:

[http://www.dvdfab.com/free.htm](http://www.dvdfab.com/free.htm)

---

### Post by danillo on 2008-03-28
> **timzak said:**
> Are you sure?  The latest version of DVDFabHDDecryptor is dated March 22, 2008:

[http://www.dvdfab.com/free.htm](http://www.dvdfab.com/free.htm)

DVD Decrypter and DVDFab Decrypter are different programs, AFAIK. 

Anyway, it's funny you don't want to use DVD Shrink. I'm on Debian and not happy with the linux alternatives so I use DVD Shrink + wine. When I used windows I always thought DVD Shrink was the best there was.

---

### Post by gobbles414 on 2008-03-29
> **danillo said:**
> DVD Decrypter and DVDFab Decrypter are different programs, AFAIK. 

Anyway, it's funny you don't want to use DVD Shrink. I'm on Debian and not happy with the linux alternatives so I use DVD Shrink + wine. When I used windows I always thought DVD Shrink was the best there was.

US$/&#8364; 39.99+ for DVDFab is MUCH more expensive than I had in mind for a DVD ripper. My absolute maximum is like US$10. But I would still prefer freeware if possible. DVD Shrink is great for creating backups of entire DVDs. But unless I'm missing something -- which is possible -- DVD Shrink does not allow for ripping specific chapters and/or special features. Instead, it rips ALL content. I'd love to use HandBrake exclusively. But it cannot read encrypted DVDs. That's why I backup with DVD Shrink and then rip the content that I want using HandBrake.

I'm searching for a solution that is as elegant and free as dvd::rip. :lolflag:

---

### Post by gobbles414 on 2008-04-01
bump...

---

### Post by jimoz on 2008-04-02
> **gobbles414 said:**
> I'd love to use HandBrake exclusively. But it cannot read encrypted DVDs.

Have you tried AnyDVD? I've been using it with CloneDVD and DVDFab for a while and haven't had a single problem with it...

---

### Post by gobbles414 on 2008-04-02
> **jimoz said:**
> Have you tried AnyDVD? I've been using it with CloneDVD and DVDFab for a while and haven't had a single problem with it...

Thanks for your reply. But as I've already mentioned in my previous posts, I'm looking for a freeware or INEXPENSIVE shareware option. I'm sorry, but US$76.60 is way too much money for me to pay for AnyDVD. It's not even the HD version of the program. That's US$123.49! [-( DVDFab is also too expensive, IMHO. At those prices, I'd rather deal with the inconvenience of running dvd::rip in Ubuntu as a dual-boot or in a virtual machine on my Vista PC.

Are you able to suggest any less expensive options?

---

### Post by KCPokes on 2008-04-02
Another I've heard of, but not had an opportunity to use, is FairUse Wizard ([http://www.fairusewizard.com/lang_en/fairuse_wizard_dvd_divx_xvid_backup_tool_light_edition.html](http://www.fairusewizard.com/lang_en/fairuse_wizard_dvd_divx_xvid_backup_tool_light_edition.html))

The light version is free.

---

### Post by gobbles414 on 2008-04-02
> **KCPokes said:**
> Another I've heard of, but not had an opportunity to use, is FairUse Wizard ([http://www.fairusewizard.com/lang_en/fairuse_wizard_dvd_divx_xvid_backup_tool_light_edition.html](http://www.fairusewizard.com/lang_en/fairuse_wizard_dvd_divx_xvid_backup_tool_light_edition.html))

The light version is free.

That looks very promising indeed! =D> I'll test the software ASAP and report back.

---

### Post by gobbles414 on 2008-04-05
Hi all,

The free version of the FairUse Wizard is a nice program. But apparently, Audacity cannot import AC3 audio. I'm going to try using VLC to rip my DVDs instead. I'll report back as my time allows.

---

### Post by gobbles414 on 2008-04-07
Hi all,

My only complaint so far about using VLC for ripping audio from DVDs is that times are displayed in h:mm:ss, but one must input times for ripping in seconds. Is there a setting in VLC that can change this?

---

### Post by timzak on 2008-04-09
What was the problem with DVDFabHDDecrypter?  They have a freeware version that has never failed to rip a DVD for me (better than DVDShrink).  I use Nero's Recode sub-app to rip out the main movie from there.  Yes, Nero costs money, but it's not unreasonable IMO.  In fact, it is so much more polished and easy to use than anything else I've seen that that alone makes it worth it.

Give it a try if you haven't already.  :)

Edit:  I'm talking about Nero 6.  I hear versions 7 and 8 are bloatware and buggy.  I found Nero 6 on Amazon.com for $19.

---

### Post by gobbles414 on 2008-04-09
> **timzak said:**
> What was the problem with DVDFabHDDecrypter?  They have a freeware version that has never failed to rip a DVD for me (better than DVDShrink).  I use Nero's Recode sub-app to rip out the main movie from there.  Yes, Nero costs money, but it's not unreasonable IMO.  In fact, it is so much more polished and easy to use than anything else I've seen that that alone makes it worth it.

Give it a try if you haven't already.  :)

Edit:  I'm talking about Nero 6.  I hear versions 7 and 8 are bloatware and buggy.  I found Nero 6 on Amazon.com for $19.

Thanks for your reply. I hadn't seen the free version of DVDFab. But I found it and read the description. It seems like I'd have to use another program after DVDFab to rip my audio. VLC is working fine.

---

### Post by gobbles414 on 2008-08-29
Hi all,

I just installed Nero 7 Essentials on my Vista laptop, and it seems like Nero Recode 2 is included. I'll test that program and report back ASAP.

---

### Post by AlphaMack on 2008-08-30
HandBrake?

---

### Post by gobbles414 on 2008-08-30
AlphaMack, I believe that HandBrake is not capable of breaking the encryption that's part of most commercially available DVDs. At least in the past, one had to use a utility like DVD Shrink before one was able to rip using HandBrake. Has this changed?

Also, I've discovered that Nero Recode 2 is locked in my version of Nero 7 Essentials; I'm using an OEM version that came with my computer. I'm contemplating purchasing some version of Nero 9 when it comes out in September, if I can find it at a discounted price.

---

