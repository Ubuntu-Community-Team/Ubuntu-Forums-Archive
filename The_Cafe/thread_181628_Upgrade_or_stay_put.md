---
title: "Upgrade or stay put?"
date: 2006-05-24
forum: The Cafe
---

### Post by meng on 2006-05-24
I see a lot of posts to the tune of, "Everything was working fine on my system until I upgraded from Breezy to Dapper". Just before the Breezy release, were there similar posts (i.e. "Everything fine till I upgraded from Hoary") ?

I ask because my Hoary-Breezy upgrade did not break anything on my system (well the dist-upgrade screwed everything up but I fixed that by doing a full reinstall), but I'm getting nervous now.

---

### Post by prizrak on 2006-05-24
I played with Dapper Flight 7 Live and it was working beautifully. Even my touchpad was fully functional (scrolling and all), even though I had to configure it on Breezy. I personally think an upgrade (fresh install not dist-upgrade) is worth it. Best course of action is try out the LiveCD and see if that doesn't screw your system up.

---

### Post by blueturtl on 2006-05-24
> I see a lot of posts to the tune of, "Everything was working fine on my system until I upgraded from Breezy to Dapper". Just before the Breezy release, were there similar posts (i.e. "Everything fine till I upgraded from Hoary") ?

Yes there were posts just like yours before Breezy and also plenty (mine included) that complained about loss of stability after it went final. I never trusted upgrading anyway (paranoia left behind by years of Windows-usage) but even after a full reinstall Breezy just wasn't as stable for me as Hoary was. Some of it can be attributed to the fact that when you install a new system you tend to do things differently than on the first install (at least if you were a newbie back then). One of the bugs that drove me back to Hoary was actually present in it as well, I just had failed to notice it before. The other instability issues were around high CPU usage and failing OpenGL (tested via screensavers). Had these issues plagued me with Hoary I would have propably shrugged and gone ahead, but it was just too big a step backward for me to be comfortable with.

This time however I plan to work on my install. Nobody benefits from people who encounter bugs and fail to report them and I see so much potential in Dapper that I'm willing to put a little effort to make it work for me and everybody else. This is a personal call though, and everyone else is free to do as they please.

If there ever was a point to my post it is that the upgrade propably won't go smoothly for everyone. Heck, a lot of people propably will complain; but that doesn't mean that Dapper isn't and won't be a beautiful polished product. Some things can mess up because a lot of us mess with the system manually (installing uncertified debs, building things by hand) that will cause problems when the system is upgraded. The new NVIDIA driver might not work with your card, or there's a single notable bug in Firefox that will make you think the whole system is a failure. It has a lot to do with impressions. If you want my advice, I will probably be doing a fresh install (while keeping my separately partitioned /home intact of course)...;)

---

### Post by Kimm on 2006-05-24
If you install using a CD you wount have any problems.

If you upgrade using dist-upgrade (as I did), you might run into problems. Mainly if you have installed nonstandard packages (perhaps by using checkinstall or by downloading from a website).
I had been tinkering alot with my Breezy before the update (I had the latest version of GTK and GLIB to name a few, all enhanced for i686) and this made it difficult (but not impossible) to upgrade. I ran alot of dist-upgrades and -f installs to get everything installed, sometimes I had to trace down the package that was dysfunctional and replace it with a dummy so other packages would install.

All in all, my upgrade took about 8 hours.

But then again, my upgrade on my laptop went smoothly (almost untuched system), so unless you messed with it too much, a dist-upgrade should do the job just fine.

Note: Unstandard repositories can also mess the upgrade up.

---

### Post by therunnyman on 2006-05-24
Apropos, isn't today (well, tomorrow, UTC, so today where I live) "Candidate Release Day"?

runny

---

### Post by Stew2 on 2006-05-24
Upgrade or stay put? I guess it all depends on you. If Breezy is doing everything you need it to and you are comfortable with it thats fine. I personally like Dapper a lot better and have had no stability issues with it at all. Mind you I have only been using it for a few days and havent done anything too intensive with it. It seems a little quicker to me than Breezy as well. If you are still a little nervous you could wait until the stable release has been out for a while just to see what the majority of people say about it as far as reliability etc. From what I have read on the forums, the people who do the dist upgrade online are having problems with the Dapper install and the people doing the fresh installs from the disc iso's seem to be having a lot less trouble. I did an install from the Dapper flight 6 iso and then updated it to current, no problems at all. Just make sure you back up everything you dont want to lose before doing the upgrade, that way if things dont work out for you, you can always reinstall Breezy and restore your files and settings. (that is if you decide to upgrade) I personally love Dapper... its got "Bling" :D 

Cheers!
Stew

Edit: If you go the disc install route, you can keep Breezy and put Dapper on another partition to try it out and see if you like it (if you have the hard disc space that is).

---

### Post by meng on 2006-05-24
Appreciate the advice everyone. Probably will make myself wait 1-2 weeks after official release and then take the plunge. Can always go back to fully updated Breezy if things don't work out.

---

### Post by Jucato on 2006-05-24
You have to consider that these comments come from users installing/using the beta versions of Dapper. Although many will say that the latest beta version is already quite stable, it is still not equal to an official thumbs up from Ubuntu.

If you have the time or resources, I suggest you either get a Live CD (or an installer CD and install on a different partition) to test out Dapper and see if it has features that you like or need to be worth the hassle of upgrading (if it will really be a hassle). Some features like XGL or the latest GNOME are hard to install/setup in Breezy.

If you are still quite unsure, I suggest you really wait for a few weeks and see what the reactions are and if there will be any problems.

Whichever path you take, I can't overemphasis the importance of backing up your system/date, whether or not your /home directory resides on a different partition. You never know what might happen. :D

(And this does not only happen to upgrading OSes, but also installing new ones)

---

