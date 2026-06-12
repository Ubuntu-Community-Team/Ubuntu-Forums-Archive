---
title: "Any body have Debian Lenny enabled in your Ubuntu Repositories"
date: 2007-10-01
forum: The Cafe
---

### Post by RAV TUX on 2007-10-01
I know they will warn you that it will break something, what would the fun be if you didn't break something is my philosophy.

I enabled Debian Lenny in Elive Gem and nothing broke, it is more stable then before. Theoretically since Ubuntu is simply another Debian derivative couldn't you do the same in Ubuntu?

I am willing to bet if I try it in Ubuntu nothing will break. Even if it does you can just do a reinstall. It's that easy.

People can warn until they are blue in the face,...

[SIZE=1][COLOR=Silver] (click on the image to navigate to Optickle Art, once there Click the image again to see full size)[/COLOR][/SIZE]
[[IMG]http://cafelinux.org/OptickleArt/albums/userpics/normal_snapshot27.png[/IMG]]("http://cafelinux.org/OptickleArt/displayimage.php?pos=-174")

I have Elive, Etch and Lenny enabled, zero problems. 

Some may say that may cause problems later, well a meteorite could hit the Earth later and destroy all mankind also. It makes no sense to put these kind of warnings out there. Another side of every warning, everything could run 100% fine to optimum performance also.

---

### Post by colllin on 2007-10-01
i'm willing to give it a try. i plan on doing a clean install of ubuntu when gutsy comes out anyways.

---

### Post by RAV TUX on 2007-10-01
> **colllin said:**
> i'm willing to give it a try. i plan on doing a clean install of ubuntu when gutsy comes out anyways.

This is exactly what I'm talking about before doing a clean install of Gutsy try enabling Debian Lenny first.

Bravo! for your Bravery!

---

### Post by colllin on 2007-10-01
> **RAV TUX said:**
> This is exactly what I'm talking about before doing a clean install of Gutsy try enabling Debian Lenny first.

Bravo! for your Bravery!

how would i go about enabling lenny?

---

### Post by RAV TUX on 2007-10-01
> **RAV TUX said:**
> [quote=Bart_D;3453824]I think I misunderstood....I thought you had Debian Lenny installed separately. Or did you do it through elive somewhow for something?


I have Debian Lenny enabled through Elive Gem, check the screenshot, add the debs & URL's as I have, afterwards run:

```
apt-get update
``````
apt-get upgrade
``````
apt-get dist-upgrade
```[/quote][http://ubuntuforums.org/showpost.php?p=3453854&postcount=112](http://ubuntuforums.org/showpost.php?p=3453854&postcount=112)

---

### Post by RAV TUX on 2007-10-01
> **colllin said:**
> how would i go about enabling lenny?check post # 5 in this thread:
[http://ubuntuforums.org/showpost.php?p=3455074&postcount=5](http://ubuntuforums.org/showpost.php?p=3455074&postcount=5)

refer to the screenshot in post #1
[http://ubuntuforums.org/showpost.php?p=3455036&postcount=1](http://ubuntuforums.org/showpost.php?p=3455036&postcount=1)

---

### Post by swoll1980 on 2007-10-01
What does it have that makes it worth risk?

---

### Post by colllin on 2007-10-01
well i tried, but when i went to update i got this error:

```
E: Malformed line 51 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

```

i need to get to bed though. i'll try and figure it out tomorrow

---

### Post by RAV TUX on 2007-10-01
Also the way I understand it is Debian Lenny will override any of your existing repositories so you don't have a chance of duplicating repositories, you simply convert your Ubuntu or in my case Elive Gem to Debian Lenny. 

This was how it was explained to me, to test this out I also enabled Elive Testing, I found it to be true, There was a Etch file that Elive Testing was dependent on that was overridden by Debian Lenny.
 Thus I could not run Elive Testing because it was dependent on an obsolete Etch file.

So it held back Elive Testing, so I reinstalled Elive and only enabled Elive Testing without Debian Lenny. Big mistake Elive Testing was too unstable. So I reinstalled Elive Gem and re-enabled Debian Lenny without Elive Testing.

Now I have a very stable version of Elive Gem(testing held back by design now) with Debian Lenny enabled.

In my repositories I now have fretsonfire, cultivation and all my other software is the latest stable version.

This is just my experience, Debian Lenny is more stable then the latest stable version of Ubuntu, and the latest stable version of Elive and probably the latest stable version of ever other Debian derivative out there.

on a daily basis I run:

```
apt-get update
``````
apt-get upgrade
``````
apt-get distro-upgrade
```

---

### Post by RAV TUX on 2007-10-01
> **colllin said:**
> well i tried, but when i went to update i got this error:

```
E: Malformed line 51 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

```i need to get to bed though. i'll try and figure it out tomorrow

I am sure that you can correct any problems, unless Ubuntu has built by design a way for you not to do this. Which I think is highly unlikely.

If you read that it tells you what the problem is and how to correct it. It may just be as simple as going in and correcting the problem as it says.

---

### Post by kerry_s on 2007-10-01
i have mine updated all the way up to sid, bring on the breakage. :lolflag:

---

### Post by Caffeine_Junky on 2007-10-01
lol  ..I updated my Gem to Lenny using the methods that Rav Tux posted in this thread,  ..but when it was all said-and-done, ..well the upgrade went-off with out a hitch, but apon a reboot  I found that my Kernel had been updated aswell and I had no nVidia driver anymore :(...

heh, well I knew in the back of my mind whilst I was doing the update/upgrade  that the Kernel would be upgraded,  ..I watched the whole procedure taking place, keeping an eye out for the mention of a Kernel-image,  but I didnt see one, ..so I thought It might be ok, ..but nahh lol  I was wrong. (I  did a fresh install back to out-of-box state)

Anyhooo,  I know all I probably had to do was go to the nVidia site and get the new driver and Install it,  but,  blahh,  lol ..not worth the effort.

I have been reconfiguring and tweaking files in linux (Ubuntu & Debian) for the last month or so, (i feel like a dog chasing its tail some times) ..now I just want too sit back and enjoy the scenery for a while :)

Elive Gem is fine as it is, .. straight off of the disc! (well for me at least)  I think it has a couple of bugs in it, ..as in I can not get it to accept some font changes I try to make, ...size I am referring too.. (or maybe it is just user error) ..no big deal but I get a bit of eye-strain after a while...

Heh,  this little Gem seems to be a bit temperamental some times.. ..but for the most part I am enjoying it! 

I will be keeping an eye on the Elive Talk in this forum tho,..because this forum is a great place to read posts and pickup little hints and tweaks to get things working.

cheers peeps

ps: Rav Tux, ..I d/l that theme from: [http://www0.get-e.org/Themes/E17/](http://www0.get-e.org/Themes/E17/) that you use,(Carbon 14v3.edj)  ..but I can not get it to showup in the theme switcher,  ..I put it in ".e/e/themes". Is there something "special" I have to do to it to make it work?

---

### Post by nowshining on 2007-10-01
gutsy is Lenny / sid and SELinux :) download sysinfo from add/remove and under release it says what they are. As for the SElinux i have seen it within the Permissions box.

---

### Post by RAV TUX on 2007-10-01
> **kerry_s said:**
> i have mine updated all the way up to sid, bring on the breakage. :lolflag:

Wow! Thats pretty gutsy! ;)

> **Caffeine_Junky said:**
> 

ps: Rav Tux, ..I d/l that theme from: [http://www0.get-e.org/Themes/E17/](http://www0.get-e.org/Themes/E17/) that you use,(Carbon 14v3.edj)  ..but I can not get it to showup in the theme switcher,  ..I put it in ".e/e/themes". Is there something "special" I have to do to it to make it work?

I just selected the theme from the Synaptic Package Manager list and it showed up in the theme selector.

I can't remember if this was before, or after the upgrade to Debian Lenny.

---

### Post by colllin on 2007-10-01
hmm... i thought i had it for a second, but now i'm getting this message:

```
W: GPG error: http://security.debian.org lenny/updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A70DAF536070D3A1
W: GPG error: http://ftp.fr.debian.org etch Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A70DAF536070D3A1 NO_PUBKEY B5D0C804ADB11277
W: GPG error: http://ftp.fr.debian.org lenny Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A70DAF536070D3A1
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

looks like i need a gpg key for the lenny repos?

---

### Post by RAV TUX on 2007-10-01
> **colllin said:**
> hmm... i thought i had it for a second, but now i'm getting this message:

```
W: GPG error: http://security.debian.org lenny/updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A70DAF536070D3A1
W: GPG error: http://ftp.fr.debian.org etch Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A70DAF536070D3A1 NO_PUBKEY B5D0C804ADB11277
W: GPG error: http://ftp.fr.debian.org lenny Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A70DAF536070D3A1
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```looks like i need a gpg key for the lenny repos?
That's odd.

---

### Post by LookTJ on 2007-10-01
> **colllin said:**
> hmm... i thought i had it for a second, but now i'm getting this message:

```
W: GPG error: http://security.debian.org lenny/updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A70DAF536070D3A1
W: GPG error: http://ftp.fr.debian.org etch Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A70DAF536070D3A1 NO_PUBKEY B5D0C804ADB11277
W: GPG error: http://ftp.fr.debian.org lenny Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A70DAF536070D3A1
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```looks like i need a gpg key for the lenny repos?
looks like synaptic is open?

---

### Post by Caffeine_Junky on 2007-10-01
> **RAV TUX said:**
> 

I just selected the theme from the Synaptic Package Manager list and it showed up in the theme selector.

I can't remember if this was before, or after the upgrade to Debian Lenny.

Thanks Rav Tux!
Got it installed, ..liking it allot :)  ..nice theme, ..easy on the eye too
***

I did not think it was possible to use debian repo's in Ubuntu due to binary differences.    

Heh, ..you live and learn huh :)

cheers

---

### Post by RAV TUX on 2007-10-01
> **Taylor said:**
> looks like synaptic is open?

> 
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

You may be right.

---

### Post by RAV TUX on 2007-10-01
> **Caffeine_Junky said:**
> Thanks Rav Tux!
Got it installed, ..liking it allot :)  ..nice theme, ..easy on the eye too
***

I did not think it was possible to use debian repo's in Ubuntu due to binary differences.    

Heh, ..you live and learn huh :)

cheers

Good Welcome, I think it was Einstein who said: "Never stop questioning!" or something like that.

---

### Post by colllin on 2007-10-01
> **Taylor said:**
> looks like synaptic is open?

i don't think it was open at the time, but it could have been. i'm running 
```
apt-get update
```
again, but it looks to be stuck at
```
Reading package lists... 65%
```

edit: I just restarted the computer and tried to 'apt-get update' again and it is stuck at 65% again.

---

### Post by colllin on 2007-10-01
well i think i'm going to give up on this one. if anything i learned a few things from trying to get this to work. stuff like this is a great way to learn linux, for me at least.

---

### Post by cb474 on 2007-10-26
What's the difference between doing this and a clean install of Debian from the Debian Installer CD?

---

### Post by RAV TUX on 2007-10-26
> **colllin said:**
> well i think i'm going to give up on this one. if anything i learned a few things from trying to get this to work. stuff like this is a great way to learn linux, for me at least.
It seems I best learn how things work when I break them and put them back together. ;)

---

### Post by cb474 on 2007-10-28
So when people do this are the leaving they ubuntu repos also enabled? Or commenting them out and just upgrading off of the debian repos?

---

### Post by RAV TUX on 2007-10-28
> **cb474 said:**
> So when people do this are the leaving they ubuntu repos also enabled? Or commenting them out and just upgrading off of the debian repos?
I am no longer doing this btw.

---

### Post by Ebuntor on 2007-10-28
> **RAV TUX said:**
> I am no longer doing this btw.

I'm curious, in the beginning of the thread you said it made your system more stable, do you still think that was the case? Of course Debian packages are more    	 	 	 	 	 	  throughly tested but just mixing Debain with Ubuntu packages, even if it basically is the same distro,  sounds like a very unstable mix. 


But I'm not expert of course. :)

---

### Post by RAV TUX on 2007-10-28
> **Ebuntor said:**
> I'm curious, in the beginning of the thread you said it made your system more stable, do you still think that was the case? Of course Debian packages are more                                   throughly tested but just mixing Debain with Ubuntu packages, even if it basically is the same distro,  sounds like a very unstable mix. 


But I'm not expert of course. :)yes I found my system to be more stable, but I was using Elive Gem back then. So I didn't mix Ubuntu & Debian. 

I am now using Xubuntu 7.10 with e17 CVS.

---

### Post by spamzilla on 2007-10-28
Err what is Debian Lenny? I googled it but the debian sites assumed you knew what is was...or I just didn;t look hard enough :lolflag:

---

### Post by koenn on 2007-10-28
It's the code name for Debian Release 4, the current stable release of Debian.

---

### Post by koenn on 2007-10-28
> **cb474 said:**
> What's the difference between doing this and a clean install of Debian from the Debian Installer CD?
Not much. 
Possibly you could get a higher version number in some cases, eg if the ubuntu repo you chose has your ubuntu has realcoolapp-1.0-ubuntu15 and Debian has realcoolapp-1.0., you'll get the ubuntu version (if apt can work out a satisfactory sollution for the dependencies, if any). Or vice versa, depending on what repo has the highest version number for a particular package.

On the other hand, if realcoolapp-1.0-ubuntu15 pulls in libraries with ubuntu modifications that the debian packages don't handle correctly, the breakage starts. 

If you're interested in migrating to Debian, you'd leave only Debian repo's enabled and not mix the repos. Or re-install (but save your home dir)

---

### Post by RAV TUX on 2007-11-19
> **RAV TUX said:**
> I know they will warn you that it will break something, what would the fun be if you didn't break something is my philosophy.

I enabled Debian Lenny in Elive Gem and nothing broke, it is more stable then before. Theoretically since Ubuntu is simply another Debian derivative couldn't you do the same in Ubuntu?

I am willing to bet if I try it in Ubuntu nothing will break. Even if it does you can just do a reinstall. It's that easy.

People can warn until they are blue in the face,...

[SIZE=1][COLOR=Silver] (click on the image to navigate to Optickle Art, once there Click the image again to see full size)[/COLOR][/SIZE]
[[IMG]http://cafelinux.org/OptickleArt/albums/userpics/normal_snapshot27.png[/IMG]]("http://cafelinux.org/OptickleArt/displayimage.php?pos=-174")

I have Elive, Etch and Lenny enabled, zero problems. 

Some may say that may cause problems later, well a meteorite could hit the Earth later and destroy all mankind also. It makes no sense to put these kind of warnings out there. Another side of every warning, everything could run 100% fine to optimum performance also.

Damn image is the wrong link!...I am testing this method out in a KNOPPIX install...

Anybody know the address I need to point this to either for the most up to date Debian or Ubuntu?

---

### Post by RAV TUX on 2007-11-19
> **RAV TUX said:**
> Damn image is the wrong link!...I am testing this method out in a KNOPPIX install...

Anybody know the address I need to point this to either for the most up to date Debian or Ubuntu?Found the image and corrected the link. ;)

---

