---
title: "Balzing Speed of Win 7 in Virtualbox"
date: 2009-12-27
forum: Virtualisation
---

### Post by VastOne on 2009-12-27
I am curious if any one else sees incredible speed of Win 7 in Virtualbox compared to the real deal on a system

I have to use Win 7 at work and I built the same system that I use at work that I have at home, identical hardware. I have also loaded and setup Win 7 for several clients and know the average speeds.

In Virtualbox Win7 installs in about 12 minutes compared to the 45 or so on a live setup.

In virtualbox Win7 updates install in mere seconds while in the real deal it can take as much as three minutes.

There are several other things (software load, installs, dloads etc) that I see in Virtualbox as well.

Why is it then that Virtualbox seems to be more suited for Win7 than the actual thing?

Looking for the technical reasons as to why this may be and not the usual slams of MS

Thanks

---

### Post by Uncle Spellbinder on 2009-12-27
Yep. Just installed. Very quick. Nearly as fast as my 'regular' install of 7.

To bad no Aero or sound though, at least in my case.

---

### Post by VastOne on 2009-12-27
> **Uncle Spellbinder said:**
> Yep. Just installed. Very quick. Nearly as fast as my 'regular' install of 7.

To bad no Aero or sound though, at least in my case.

I have sound but no aero (and do not want). Are you 64 bit? I could not get sound on 64 bit and know that that is a Win7 64 bit driver issue

---

### Post by falconindy on 2009-12-27
It might be fast (and I don't think it is compared to XP), but its still Windows.

It's like going in for an AIDS test and finding out you only have chlamydia.

---

### Post by Uncle Spellbinder on 2009-12-27
Yep. 64 bit. My RC product activation key is for my 64 bit ISO (burned to DVD). So, I guess I'm stuck with this.

---

### Post by Uncle Spellbinder on 2009-12-28
> **falconindy said:**
> It might be fast (and I don't think it is compared to XP), but its still Windows.

It's like going in for an AIDS test and finding out you only have chlamydia.

Ridiculous. We've all got our opinions, but coming on a thread that is about **Windows** virtualization and bashing is just childish. Obviously, this thread isn't for you. I don't go on the Fedora threads or Arch threads and tell them how I don't like those distros. I but out of conversations that aren't for me. You might want to do the same.

I love Ubuntu, and always will. Doesn't mean I have to hate Windows as well. I happen to think 7 is fantastic.

---

### Post by VastOne on 2009-12-28
> **Uncle Spellbinder said:**
> Yep. 64 bit. My RC product activation key is for my 64 bit ISO (burned to DVD). So, I guess I'm stuck with this.

I do believe there is a driver to fix it if you need sound

---

### Post by VastOne on 2009-12-28
> **falconindy said:**
> It might be fast (and I don't think it is compared to XP), but its still Windows.

It's like going in for an AIDS test and finding out you only have chlamydia.

This is precisely what I wanted to avoid when I asked for technical responses....

I also have no fondness for MS but Win7 is the best product they have had since XP and IMHO it blows XP away

---

### Post by VastOne on 2009-12-28
> **Uncle Spellbinder said:**
> Ridiculous. We've all got our opinions, but coming on a thread that is about **Windows** virtualization and bashing is just childish. Obviously, this thread isn't for you. I don't go on the Fedora threads or Arch threads and tell them how I don't like those distros. I but out of conversations that aren't for me. You might want to do the same.

I love Ubuntu, and always will. Doesn't mean I have to hate Windows as well. I happen to think 7 is fantastic.

+1

Could not have said it any better or more eloquently

---

### Post by Uncle Spellbinder on 2009-12-28
I'VE GOT SOUND!

Did some searching and this worked: [http://forums.virtualbox.org/viewtopic.php?p=106886#p106886](http://forums.virtualbox.org/viewtopic.php?p=106886#p106886)

See here (click image to enlarge):
[[IMG]http://content.imagesocket.com/thumbs/Virtual7Sound63f.jpeg[/IMG]](http://content.imagesocket.com/images/Virtual7Sound63f.jpeg)

---

### Post by falconindy on 2009-12-28
> **VastOne said:**
> This is precisely what I wanted to avoid when I asked for technical responses....

I also have no fondness for MS but Win7 is the best product they have had since XP and IMHO it blows XP away
I had a pretty foul experience tonight with Win7 on VirtualBox, so pardon my bluntness. Adding an item to the start menu was **not** a trivial task as it previously was. MS finally creates a decent scripting language (powershell) and you can't even create executables without wading through system policy. What used to be administrator level privileges (that is, access to the whole system) is now the equivalent of a regular user in Linux. The entire operating system has been bandaided to the point of absurdity because MS refuses to fix their core problems and continues to hide low level functionality from technical users who are actually interested in what the OS is doing.

Ridiculous. I used Windows for 15+ years and I can confidently say MS peaked in 2001 with XP's release. It's fast, solid, simple, and it does exactly what I want with no fuss. It's only a shame that the 64-bit release was such a waste.

Constructive enough? I could go on...

---

### Post by VastOne on 2009-12-28
> **falconindy said:**
> I had a pretty foul experience tonight with Win7 on VirtualBox, so pardon my bluntness. Adding an item to the start menu was **not** a trivial task as it previously was. MS finally creates a decent scripting language (powershell) and you can't even create executables without wading through system policy. What used to be administrator level privileges (that is, access to the whole system) is now the equivalent of a regular user in Linux. The entire operating system has been bandaided to the point of absurdity because MS refuses to fix their core problems and continues to hide low level functionality from technical users who are actually interested in what the OS is doing.

Ridiculous. I used Windows for 15+ years and I can confidently say MS peaked in 2001 with XP's release. It's fast, solid, simple, and it does exactly what I want with no fuss. It's only a shame that the 64-bit release was such a waste.

Constructive enough? I could go on...

Honestly I think you are just looking for a fight and I for one will not give it to you. I have been a Windows user since it's inception and know every bit of minutiae it has to offer and as a high level tech for the MS industry I can recite to you anything you would want to hear.  

This is not the place for what you are after, if you want to start a MS bashing thread, be my guest.

Just because you have an issue with such a simple task is not a reason to bash this thread when I was simply trying to figure out why a system would run so much faster on a Virtual Box

Please take you flame elsewhere and any Forum admin has my OK to close this out

---

### Post by VastOne on 2009-12-28
> **Uncle Spellbinder said:**
> I'VE GOT SOUND!

Did some searching and this worked: [http://forums.virtualbox.org/viewtopic.php?p=106886#p106886](http://forums.virtualbox.org/viewtopic.php?p=106886#p106886)

See here (click image to enlarge):
[[IMG]http://content.imagesocket.com/thumbs/Virtual7Sound63f.jpeg[/IMG]](http://content.imagesocket.com/images/Virtual7Sound63f.jpeg)

Well done and thanks for the tidbit of info...

FYI, I loaded 32 bit first, 64 bit did not work until I upgraded my bios. I loaded 64 bit after the upgrade and was not happy at how sluggish 64 bit was and went back to 32 bit.  

If they close this, PM me with any other tidbits  

Thanks

---

### Post by falconindy on 2009-12-28
Not looking for a fight. I'm simply stating my opinion in disagreement with **your** opinion. I'm done here.

---

### Post by VastOne on 2009-12-28
> **falconindy said:**
> Not looking for a fight. I'm simply stating my opinion in disagreement with **your** opinion. I'm done here.

Happy Trails and remind me what my opinion was?

---

### Post by Uncle Spellbinder on 2010-01-01
> **Uncle Spellbinder said:**
> I'VE GOT SOUND!

Did some searching and this worked: [http://forums.virtualbox.org/viewtopic.php?p=106886#p106886](http://forums.virtualbox.org/viewtopic.php?p=106886#p106886)

OK, so the sound hs been choppy, or actually slow/crackling. I ran across this thread: [http://ubuntuforums.org/showthread.php?p=8584891#post8584891](http://ubuntuforums.org/showthread.php?p=8584891#post8584891). Now, Windows 7 via Virtualbox in Karmic produces sound as you'd expect. Crystal clear from system start-up sounds, system sounds and iTunes 8 is working perfectly.

Thanks to Welcomed Rain for the workaround!





.

---

