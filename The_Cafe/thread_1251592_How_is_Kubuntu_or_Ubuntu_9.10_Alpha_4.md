---
title: "How is Kubuntu or Ubuntu 9.10 Alpha 4?"
date: 2009-08-27
forum: The Cafe
---

### Post by gymophett on 2009-08-27
I'm planning on using Kubuntu 9.10 Alpha 4 as my main OS.
I know it isn't recommended.
But how is it? Any major bugs?

EDIT: When a new aplha comes... will I be able to upgrade to it?

---

### Post by Bölvaður on 2009-08-27
grub is strange, there is no manu.lst any more only grub.cnf or something like that which is more like code than a config file at a quick glans.

the intel graphic bug is still there as in jaunty.

Im getting crash reports but not seeing why (only used it for about 20 minutes).

---

### Post by nowin4me on 2009-08-27
Have a look [HERE]("http://ubuntuforums.org/forumdisplay.php?f=359") and you can get a brief idea on some of the problems that are around. I am personally am not using it at the moment but I did test Alpha 1 and maybe 2 out, but things have probably changed since then (hopefully for the better).

---

### Post by rajcan on 2009-08-27
It's actually rather decent. I ran it in vbox so I couldn't fully test the graphics, but from all that I can see it works nice.

---

### Post by SunnyRabbiera on 2009-08-27
> **Bölvaður said:**
> 

the intel graphic bug is still there as in jaunty.

I hope its resolved, I cant take another crap release.

---

### Post by nowin4me on 2009-08-28
You SHOULD be able to upgrade to it (unless you have problems updating). I am going to wait until Alpha 5 which will be realised on September the 3rd.
O and also check what other people's problems are by going to [Lauchpad]("https://launchpad.net/ubuntu/karmic").

---

### Post by Bölvaður on 2009-08-28
> **SunnyRabbiera said:**
> I hope its resolved, I cant take another crap release.

I heard the new driver will be in the final release. But do you know what? I am an optimist and want to quote the great poet that said:

"[I]Life sucks
and then you die.[/I]"

in his poem named *The Optimist*.


I have no idea why I just said that.

---

### Post by bkratz on 2009-08-28
> **gymophett said:**
> I'm planning on using Kubuntu 9.10 Alpha 4 as my main OS.
I know it isn't recommended.
But how is it? Any major bugs?

EDIT: When a new aplha comes... will I be able to upgrade to it?

I tried it and took it back out. It wouldn't let me use my VGA monitor only if I used my DVI. Went back to 9.04

---

### Post by afroman10496 on 2009-08-28
Grub2 is awesome. I think you can get a Grub GUI too.

---

### Post by Paqman on 2009-08-28
> **gymophett said:**
> I'm planning on using Kubuntu 9.10 Alpha 4 as my main OS.


I say go for it, providing you:
[LIST=1]
[*]Realise that keeping a copy of Jaunty on the machine as a backup is a smart thing to do
[*]Are prepared to put in the time filing and tracking bug reports, doing any further testing that's requested, providing feedback and generally being a useful tester
[*]Don't mind truckloads of updates, unexpected breakage, and  half-finished things that just don't work properly
[*]Know how to find the info you need to fix the above breakage
[/LIST]

If you can answer "yes" to all of the above, welcome to the testing branch! Otherwise, stick with Jaunty until into the beta stage at least.

---

### Post by Paqman on 2009-08-28
> **Bölvaður said:**
> grub is strange, there is no manu.lst any more only grub.cnf or something like that which is more like code than a config file at a quick glans.


It's different, but not difficult. The new grub.conf is a actually written by a bunch of scripts, you don't edit it manually at all. Ever. You just tell the scripts what to do. For example, if you want to remove a whole category from the list, just remove the executable flag for that section's script and "sudo update-grub2". Job done!

The new version of startupmanager does actually play nicely with Grub2 now, anyway.

---

