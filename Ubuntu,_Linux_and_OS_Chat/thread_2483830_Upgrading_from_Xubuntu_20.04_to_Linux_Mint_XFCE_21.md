---
title: "Upgrading from Xubuntu 20.04 to Linux Mint XFCE 21: Is it okay to carry over my exist"
date: 2023-02-09
forum: Ubuntu, Linux and OS Chat
---

### Post by ardouronerous on 2023-02-09
[SIZE=4]**Upgrading from Xubuntu 20.04 to Linux Mint XFCE 21: Is it okay to carry over my existing login password?**[/SIZE]

I'm upgrading from Xubuntu 20.04 to Linux Mint XFCE 21.1 because of the support timeline, Xubuntu 22.04 is supported for 3 years, while Linux Mint 21 is supported for 5 years.

My question is, is it a good idea to carry over the login password I used for Xubuntu 20.04 to Linux Mint XFCE 21? Or should I go with a unique password ever time I do a fresh install, why or why not?

Also, is there a difference between Xubuntu 20.04 and Linux Mint XFCE 21, besides from the taskbar being below on Linux Mint? Is there a learning curve? Thanks.

---

### Post by guiverc on 2023-02-09
Have you contrasted the support for each?

Xubuntu 20.04 LTS has *five* years for packages in the ***main*** repository, but only *three* years applies to the Xfce/Xubuntu packages found in ***universe*** (*though if bugs are reported, a MOTU can still fix them during those five years of standard support*).  3 & 5 years being the guarantee; and recall 5 years doesn't apply to everything.

Linux Mint has (*in my view anyway*) a lower level of security; thus why it can offer the *five* years, not worrying about that fact that upstream Ubuntu no longer *patches* the packages they rely on.  ie. consider the level of security offered in the 3 vs 5 years (*not just the number*). This doesn't imply it's 'bad', just you need to consider all the facts with regards your security needs/wants.

Linux Mint uses *runtime adjustments* as they do rely on packages from upstream Ubuntu, that they cannot patch/change (*without cost & a lot of work/cycles*), which is part of the reason why they've historically had to use the *lower level* of security. That to me is a HUGE difference. How you rate that is up to you though (*security difference isn't actually that great, but it's still there!*).

The main difference between Linux Mint & Ubuntu is (*as I see it*)

- Ubuntu treats security as a higher value requirement  (*eg. what Pro provides if you want to add it; it's optional with 'universe' security patches now; which have not been available before!*)
- Linux Mint relies on *runtime adjustments*, as producing everything themselves has a cost they cannot afford (*the level of adjustments, as well as their security approach varies on release; I'm only speaking generically here*).
- Linux Mint works hard to avoid *snapd* as used by upstream Ubuntu  (*if you don't want snaps, agree with the views of Linux Mint, they've done work you'll have to do yourself if using Ubuntu; it may not complex changes but its still done for you*)
- Linux Mint is *greener* (*in color*) so if you don't like Ubuntu colors that's good!
- Linux Mint I've always found looks visually "*polished*" & impressive; if you value *looks* that's big  (*Ubuntu can work on this too, but tastes are subjective*)
- setup; Xubuntu setup I tend to think of as '*somewhat **boring*', but they feel it should be in that it won't distract you from your work.  Xubuntu also give a rather pure '*upstream Xfce*' experience, so if you like what the Xfce team  provide you'll love it, if you want it different then you may appreciate it altered (by Linux Mint for example).

As for password etc..  I don't see much need/difference.

I use second hand hardware & tend to test it a couple of weeks before I *CLEAN* install the OS I want to use on it; and on my last PC (*mid-late 2017*) I used a Linux Mint system during that testing to have a look.  I was impressed with the presentation; impressed enough that I didn't want to *CLEAN* install when I installed the Ubuntu products I intended using; so I booted a *live* system & deleted what I didn't want to survive, then did a *UNCLEAN* (no format) install of the Ubuntu release over what was Linux Mint, thus the parts of Linux Mint I didn't want to re-create survived.  Once or twice a year I'd be reminded of that when I'd see a Linux Mint trail on the machine, but the bits I didn't want to survive I'm convinced didn't.  Despite what I've said of Linux Mint, I didn't feel a need to *CLEAN *install  (*and I kept using that PC until its PSU gave out  October* *2022*).

(*Linux Mint is a Ubuntu based system as I see it; so its 95% a Ubuntu system; Xubuntu is a Ubuntu system* ...  *My 2c*)

---

### Post by ardouronerous on 2023-02-09
Thank you guiverc for your response. I will process what you have written and will make my decision accordingly on whether to upgrade to Linux Mint or stay with Xubuntu and upgrade to 22.04.

Thank you.

---

