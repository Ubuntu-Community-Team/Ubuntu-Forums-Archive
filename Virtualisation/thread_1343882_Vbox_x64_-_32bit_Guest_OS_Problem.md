---
title: "Vbox x64 - 32bit Guest OS Problem?"
date: 2009-12-02
forum: Virtualisation
---

### Post by kneewax on 2009-12-02
Hi Folks,

It's been a while since I posted, but despite attempting to fix the issues I have previously mentioned with Vbox ([http://ubuntuforums.org/showthread.php?t=1213010](http://ubuntuforums.org/showthread.php?t=1213010))  I have been unable to get my XP guest machines working properly on my (now) Karmic host.  Either from old images or installing new versions of the guest.

Thinking further about the issues  have been having with programs not installing,and constant delayed write errors, I began to wonder if the issues I faced co-incided with me migrating to my x64 desktop from the x86 laptop I was using before.

Is there any known issues running 32bit guests on an x64 machine and Host OS?  Are there any particular tweaks or work arounds that I have missed for this configuration?

ta

---

### Post by fouadatmeh on 2009-12-02
Hello,

I have read the other post and would like to suggest: could it be caused by snapshots?
** I have been using vbox for a while now (x64 Ubuntu host, several x86 guests) with no problems (am not using snapshots)..
Hope this helps or someone provides a better solution...

---

### Post by kneewax on 2009-12-03
Thanks for the response. I did try looking at snapshot to no avail I'm afraid.  Also I did a fresh install of XP in a new VM and have the same issues.  One thing is .exe files that I download in the guest (like SP2) constantly appear as corrupted files. Which is why I wondered about compatability - it's almost as if the way Vbox has allocated the virtual disk space is intrinsically incompatable with 32bit Windoze.

Clearly not an issue anyone else has tho!  What it is to be unique ;-)

Ah well I'll keep tinkering!

---

### Post by kneewax on 2009-12-03
Curiouser and curiouser! I just dusted off an old copy of Vista HP to see if that worked any better than the XP installs - however this installation only got as far as 'running windows for the first time' before the install failed.

It seems that Vbox on this machine has some inherenrent (and understandable)  dislike of Windoze!

Interestingly I was able to install GDGT's vmware version of ChromeOS yesterday without issue...?

I might try a verfsion of linux to see if I get similar issues there.

---

### Post by tymek666 on 2009-12-03
I'm running Vbox 3.0.6 with WinXp guest without any problem from several months on Mint 7 64-bit. However I didn't upgrade to Karmic yet.

---

