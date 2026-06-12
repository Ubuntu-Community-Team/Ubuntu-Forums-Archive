---
title: "*** Backport Speed Issues ***"
date: 2005-05-10
forum: Ubuntu Backports
---

### Post by ubuntu-geek on 2005-05-10
OK here is the deal. Backports is currently limited to a 3meg internet connection so we do not exceed our monthly bandwidth limits.

I personally pay for this server and the forums server and do not wish to have a $1,000+ bill from overage charges :)

With that being said, it will continue to be capped until we reach out donation goal and can pre-pay the provider for an unlimited connection for a year.

If you wish to help out visit this site: [http://ubuntuforums.org/donationstotal.php]("http://ubuntuforums.org/donationstotal.php")

Currently backports uses roughly 40-50GB of transfer per day.

---

### Post by jdong on 2005-05-10
ok, thanks for the information.

It's unimaginable how much traffic we use. :)

---

### Post by Zelut on 2005-05-10
thanks for the update.  That does answer a few questions :)

---

### Post by fng on 2005-05-10
50gb/day????

That's some massive leeching :)

---

### Post by thegreedyturtle on 2005-05-10
[QUOTE=fng]50gb/day????

That's some massive leeching :)[/QUOTE]
 Random Musing:
I wonder if apt could be rigged to use the bittorrent model for downloading...

---

### Post by dewey on 2005-05-10
[QUOTE=thegreedyturtle]Random Musing:
I wonder if apt could be rigged to use the bittorrent model for downloading...[/QUOTE]
One would probably just write a clone of apt, using the bit torrent model.  Debian packages rely on dpkg, not apt-get.  Also, I'm thinking something like a kazaa model would be more effective for packages like this, but then it removes the whole "controlled" repository idea, and it would be hard to control what packages got onto your system, like $sudo deb-get install gaim could get you 10 different versions, some backdoored, etc etc.  Although requiring all packages to be authenticated and checksummed with the main server first would alleviate many problems.

It's complicated to implement a p2p model, for something like apt-get.  But it's a great idea and I'm sure there's a way to do it effectively.

---

### Post by Technoviking on 2005-05-12
[QUOTE=ubuntu-geek]
I personally pay for this server and the forums server and do not wish to have a $1,000+ bill from overage charges :)
[/QUOTE]
I'm shocked that Ubuntu/Canonical does not help with the funding of the forums  and  backports in some way. I sent $10, and plan to send more each month.

Mike

---

### Post by moopere on 2005-05-13
[QUOTE=dewey]One would probably just write a clone of apt, using the bit torrent model.  Debian packages rely on dpkg, not apt-get.  Also, I'm thinking something like a kazaa model would be more effective for packages like this, but then it removes the whole "controlled" repository idea, and it would be hard to control what packages got onto your system, like $sudo deb-get install gaim could get you 10 different versions, some backdoored, etc etc.  Although requiring all packages to be authenticated and checksummed with the main server first would alleviate many problems.

It's complicated to implement a p2p model, for something like apt-get.  But it's a great idea and I'm sure there's a way to do it effectively.[/QUOTE]


Hmm.  I currently use apt-proxy to feed the 30+ machines on my LAN.  Its invisible for the most part to the local machines once their sources files has been suitably modified.  This saves an absolute ton of bandwidth beleive me.

Now, thinking about this for a moment, it should surely be possible to use a torrent type model so that different apt-proxy's can all talk to each other.  The beauty here being that the local machines still don't really see whats going on so it all stays nice and uncomplex for them.

I think that the signed packages and tight versioning control debian (now) employs should pretty much take care of most security issues.

Craig

---

### Post by AgenT on 2005-05-15
[QUOTE=ubuntu-geek]I personally pay for this server and the forums server and do not wish to have a $1,000+ bill from overage charges :)[/QUOTE]

Holy crap batmat! I did not realize that there was a single person that paid for the forums (and backports). But then again, I have been using Ubuntu for 6 days only :roll:

With that said, I think that I can speak on behalf of everyone and say:

**[size=6]THANK YOU UBUNTU-GEEK[/size][size=6]![/size]**

As one of the shocked readers noted, why does no one from Ubuntu officially pay for at least part of the expense of these forums? That is, Ubuntu/Canonical? My guess is they know how important the forum is, yes? Or do they see it as a somewhat different, yet still somewhat similar, support style system that is in competition with them?

Whatever the case may be, time to **donate!**

And as a possible request, would it be difficult to rig the donation page so it shows actual amount that has been donated? Or maybe you want to keep that private for whatever reason? If that is so, then it's all fine by me!

---

### Post by harryc on 2005-05-15
I agree it would be 'nice' if you showed a $$target on the donate page and periodically updated it to show attainment percentage of said goal. It might also incent others to help you reach that goal. ;)

---

### Post by noderat on 2005-05-15
I wonder if perhaps some kind soul could lend some bandwidth to the project as a mirror.

I was wondering if it was my internet connection having issues (I haven't learned to trust ndiswrapper yet) but now I understand that it's your server. I'm getting an average of 1-3KB/s which is...amazingly slow. Must be because everybody is trying to update to the new firefox that was put up recently.

---

### Post by AgenT on 2005-05-15
For more information about a possible Backports Mirror, please see the new thread created on a possible [Backports Mirror]("http://ubuntuforums.org/showthread.php?t=34581").

---

### Post by crane on 2005-05-15
Wow, I didn't know it was hosted by one person as well!!
I made a donation as well, I hope it help, I know every little bit counts!

Thanks for all the great work you do!!

---

### Post by GeirG on 2005-05-16
Donation made, thanks for the effort.

---

### Post by ubuntu-geek on 2005-05-16
I opened up the full bandwidth on the server today so everyone can get updates quicker depending how much bandwidth we have left at the end of the day I might cap it or just let it ride until the end of the month. 

We are thankful for everyone who has a made a donation to help cover server costs and hopefully we can get this situation resolved soon :)

---

### Post by rykel on 2005-06-05
Hi guys,

The easiest solution to getting the latest software is to simply go to the official websites and download their respective autopackages.

That way, we do not have to backport so many programs, and neither would some of our precious Ubuntu volunteers need to work so hard, spending 48 hours or more trying to convert RPMs to DEBs etc.

Of course, only a handful of programs are available as autopackages for now, but with the support of the Ubuntu and other Linux communities, surely it will catch on. (has anybody tried the new Lincity-ng? Gosh, it's awesome...)

In fact, when autopackage is integrated with the native package managers, it will be even more fantastic!

btw, I keep getting "401 authorization required" from the backport repositories... any idea what's happening? Thanks!!


Best Regards,

Rykel
Singapore

I love Ubuntu Linux, and I love autopackage.

---

### Post by ShaneAu on 2005-06-05
[QUOTE=rykel]Hi guys,

The easiest solution to getting the latest software is to simply go to the official websites and download their respective autopackages.

That way, we do not have to backport so many programs, and neither would some of our precious Ubuntu volunteers need to work so hard, spending 48 hours or more trying to convert RPMs to DEBs etc.

Of course, only a handful of programs are available as autopackages for now, but with the support of the Ubuntu and other Linux communities, surely it will catch on. (has anybody tried the new Lincity-ng? Gosh, it's awesome...)

In fact, when autopackage is integrated with the native package managers, it will be even more fantastic!

btw, I keep getting "401 authorization required" from the backport repositories... any idea what's happening? Thanks!!


Best Regards,

Rykel
Singapore

I love Ubuntu Linux, and I love autopackage.[/QUOTE]
 [http://ubuntuforums.org/showthread.php?t=37525](http://ubuntuforums.org/showthread.php?t=37525)

Mirrors only now. :).

---

### Post by jdong on 2005-06-05
[QUOTE=rykel]
Of course, only a handful of programs are available as autopackages for now, but with the support of the Ubuntu and other Linux communities, surely it will catch on. (has anybody tried the new Lincity-ng? Gosh, it's awesome...)

In fact, when autopackage is integrated with the native package managers, it will be even more fantastic!


I love Ubuntu Linux, and I love autopackage.[/QUOTE]

In order for Autopackage to work, you are assuming that all distributions would be binary-compatible with your packages. Sure this may work with more external apps like GAIM or xchat, but then think about packages like Firefox or Postfix, where a given distro could have hundreds of patches/modifications to underlying libraries.

For example, try installing Redhat's Openoffice on Ubuntu.. the binaries simply don't work, no matter how hard you try!

When the LSB (Linux Standard Base) catches on, Autopackage will succeed. I want this to happen as much as you do :)

---

