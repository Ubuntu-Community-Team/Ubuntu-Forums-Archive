---
title: "Should I upgrade?"
date: 2006-10-26
forum: The Cafe
---

### Post by codypumper on 2006-10-26
Should I upgrade to Edgy Eft? Last time I had to reinstall ubuntu (some x windows problem occured when upgrading to dapper)
Is everyone else using edgy eft?
Should I stick with dapper for the lts?
Will any of my configuration change if I upgrade?
HELP!

---

### Post by bdb on 2006-10-26
as the old saying goes...

If it's not broke don't upgrade.

---

### Post by .t. on 2006-10-26
If you want to better performance and support for eye-candy, then go for it. I haven't had any problems for a while. A dist-upgrade (or two, to be safe) should do the trick. Nonetheless, the above advice is indeed wise, and I can only speak for my case.

---

### Post by codypumper on 2006-10-26
Currently, it is broken in three ways.
-i have to restart to mount anything new
-it takes five minutes to boot because it hangs on loading hardware drivers
-and modprobe is always processing, taking up 50% cpu usage

Could it fix any of this, or make it worse?

---

### Post by Old Pink on 2006-10-26
> **codypumper said:**
> Currently, it is broken in three ways.
-i have to restart to mount anything new
-it takes five minutes to boot because it hangs on loading hardware drivers
-and modprobe is always processing, taking up 50% cpu usage

Could it fix any of this, or make it worse?

It'd most likely fix them all, or at least 2 of them. 

I could make a script to kill modprobe which could run at startup for you, if you wished? :-k

---

### Post by codypumper on 2006-10-26
modprobe will not die! I've tried alot

---

### Post by raqball on 2006-10-26
Not everyone is upgrading :)

I am sticking with 6.06 because it's the main and only OS on my laptop. 6.06 is stable and LTS! :)

If you want cutting edge with the possibility of issues then upgrade. If Ubuntu is your main and only OS then I would stick with the good ol reliable Dapper.

My son has edgy on his desktop, but I make sure he backs up his homework and music files daily just in case :)

---

### Post by codypumper on 2006-10-26
another quick question, (as I am one who has learned to ask questions) 
will my firefox profile/customization, and photos be gone after update?
Like, what would be gone?

---

### Post by Rackerz on 2006-10-26
I always upgrade, I like a new challenge if something's broken. I also like having new features, is you want stable then Dapper is your best bet, not that I'm saying Edgy isn't stable because it is for me. But others have a lot more to say.

---

### Post by mips on 2006-10-26
Why do people insist on upgrading ??? If you have modified and tweaked your Dapper install you can expect problems. There are no gaurantees...

DO A CLEAN INSTALL, PERIOD !!!

---

### Post by ember on 2006-10-26
But before you do a clean install - format your partitions, the installer is a bit broken.

---

### Post by .t. on 2006-10-26
nothing will be gone.

and why not upgrade? it's one of the finest points of apt. always works for me.

---

### Post by codypumper on 2006-10-26
I guess I'll upgrade tomorrow. Main reason is for the less buggy alsa package. SKYPE WILL NOT WORK!

---

### Post by deepwave on 2006-10-26
Upgraded to get my scanner and remote to work.  (Never bothered with custom kernels just to get lirc working well).

I do enjoy the bootspeed increase, beryl working and the improvements in alsa, sdl and opengl.

---

### Post by Compucore on 2006-10-26
I'm sticking with Dapper LTS for now personally. Like the others in the past they have their good points. I'll wait until they release the next one. I know cuting edge stuff can painful since it is a double edge sword. Been there for at least a couple of beta tests under the windows for other companies. :D

Compucore

---

### Post by henriquemaia on 2006-10-26
> **mips said:**
> Why do people insist on upgrading ??? If you have modified and tweaked your Dapper install you can expect problems. There are no gaurantees...

DO A CLEAN INSTALL, PERIOD !!!

Very true. On the previous thread I posted, I said that I wasn't upgrading because I didn't need the upgrade - but this is also a very important reason to me. I have customized my Dapper a lot and since it's been here since Flight 3, It's better for me to stay with it. 

If I just thought about changing (if I had the time, patience, etc), I'd bet on clean install.

---

### Post by henriquemaia on 2006-10-26
> **Compucore said:**
> I'm sticking with Dapper LTS for now personally. Like the others in the past they have their good points. I'll wait until they release the next one. I know cuting edge stuff can painful since it is a double edge sword. Been there for at least a couple of beta tests under the windows for other companies. :D

Compucore

That's also a good reason to stay. My plan is to do the same: 1 upgrade per year. And, most definitely, I'll get pretty amazed by then with all the changes in Ubuntu.

---

### Post by chickengirl on 2006-10-26
> **mips said:**
> Why do people insist on upgrading ??? If you have modified and tweaked your Dapper install you can expect problems. There are no gaurantees...

DO A CLEAN INSTALL, PERIOD !!!

Define "modified and tweaked"? Is it "if you have touched your installation at all" or "if you have hacked stuff"?

---

### Post by viper on 2006-10-27
Yes, but backup critical files first, Edgy runs oh so nicely.

---

### Post by mssever on 2006-10-27
> **chickengirl said:**
> Define "modified and tweaked"? Is it "if you have touched your installation at all" or "if you have hacked stuff"?

As a followup, what can go wrong (aside from regressions/bugs in Edgy that would be present regardless) in upgrading a system that has no non-APT software?

The main reason I'm using Ubuntu is because of APT. I ditched Red Hat because it was really difficult to upgrade. I've put enough work into my system that reinstalling isn't an option. It's either upgrade to Edgy or stick with Dapper.

@compucore, unless you plan on reinstalling, you won't be able to upgrade to Feisty without first going to Edgy (although you could do both upgrades at the same time, I suppose).

---

### Post by Reshin on 2006-10-27
So, why am I getting warnings about missing dependencies everytime I run aptitude -f install or aptitude dist-upgrade after dapper -> edgy-upgrade?

---

### Post by Compucore on 2006-10-28
Yes that is very true by the time they get the final out by then.They had a chance to work out of about 90% of the bugs. And still find the hidden ones that were no know. By then I am usually surprised as well by what they have done by release time. ANd it is a good thing for me anyways. Like going from Breezy to dapper a nice change between the two of them. If I were to reinstall even the previous version I would have to for older systems. Since I know they could handle them. And still use the most recent release for my computer that I have here. 
Compucore


> **henriquemaia said:**
> That's also a good reason to stay. My plan is to do the same: 1 upgrade per year. And, most definitely, I'll get pretty amazed by then with all the changes in Ubuntu.

---

### Post by codypumper on 2006-10-28
Either way, I did upgrade. There are no major visual changes, but speed and few of my problems are better. I did backup my precious files to cds before hand in case, and I reccomend anyone else doing so as well (k3b)

---

