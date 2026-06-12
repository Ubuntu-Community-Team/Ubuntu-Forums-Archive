---
title: "Removing Viruses?"
date: 2008-12-04
forum: Windows
---

### Post by jpoRS on 2008-12-04
Hey Folks,

Here is the deal.  My girlfriend has a dual-booting Lenovo ThinkPad running XP(I don't know which one) and Hardy (I know sexy right?).  Ubuntu is her primary OS, she just uses Windows for school work and the like.  Well she was doing some group work, and sharing documents over flash drives, yada yada yada.  She has a very minimal security setup (either MacAfee or Ewido, I don't recall which) and now is showing symptoms like [THIS]("http://www.bleepingcomputer.com/forums/topic81880.html") plus a few other annoying symptoms (popups, Windows constantly alerting her that she has malware on her computer).

Now for the kicker.  Neither of us know anything about Windows.  I jumped into Linux right when I started to understand computers, and she knows even less than I do.  So none of the Windows based solutions are looking viable right now.

Is there a way to remove the virus using Linux?  It would be awesome to be her knight in OpenSource Armor.

If not I guess I finally have a way to convince her to go 100% Ubuntu.

Thanks,
jim

---

### Post by sstusick on 2008-12-04
You can install an anti-virus on Linux and use it to scan your Windows partition. 

Check out ClamAV, it's in the repos.

---

### Post by DieB on 2008-12-04
always use an non-adminastrativ user in windows for daily work and for dministrational the admin account (do it like unix did it always) - that should keep u off of the most annoying parts of viruses.

sure install clam as posted above.

but ever thought about instaling windows in virtualbox to let your girlfriend make her "homework"?

for sure - the suggestion is only if there are no to heavy system recuirements for her programs. (second ability might be wine - bit here u might better look in apppdb on [www.winehq.org](www.winehq.org))

hope that helps

---

### Post by benny bronx on 2008-12-04
I'd first try running a few free scanners such as Superantispyware and Malwarebytes Rogue Remover.

[http://www.superantispyware.com/]("http://www.superantispyware.com/")

[http://www.malwarebytes.org/rogueremover.php]("http://www.malwarebytes.org/rogueremover.php")

Then run the updated antivirus in safe mode. If the computer is so compromised that you can't download the first two apps, run the safe-mode scan first.

 If that fails, you should post on the forum you linked.

---

