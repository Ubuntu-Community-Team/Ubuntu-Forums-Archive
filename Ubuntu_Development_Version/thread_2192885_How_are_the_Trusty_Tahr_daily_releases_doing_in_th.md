---
title: "How are the Trusty Tahr daily releases doing in the usability stakes?"
date: 2013-12-10
forum: Ubuntu Development Version
---

### Post by WebDrake on 2013-12-10
I'm finding myself rather tempted to get up to speed on Trusty Tahr rather than sticking with 13.10.  I've often upgraded during the alpha period of previous releases, and over the last few years at least this has been a largely painless experience -- while obviously not stable, the levels of stability in practice are typically very admirable.  So how are things going on this front with Trusty Tahr?  Is it in a usable state, or is there still a lot of instability?

I'm running an 18-month-old ThinkPad with Intel graphics, so I don't anticipate any particular hardware problems (famous last words...), if that is relevant.

---

### Post by Nr90 on 2013-12-10
I've been running 14.04 the whole time as my daily driver.
Have had no major issues. Very few minor ones.

---

### Post by sammiev on 2013-12-10
Never had any issues so far, it has been a smooth ride.

---

### Post by Hazzabin on 2013-12-10
Both Trusty Tahr with Unity and Trusty Ubuntu Gnome running fine on my machines

but note that going off into Gnome with compiz and or metacity it does run into various problems

just my two pence worth

---

### Post by fantab on 2013-12-10
Both Ubuntu and Xubuntu seem quite stable for now.

---

### Post by oldfred on 2013-12-10
I prefer to just install to another 25GB / (root) partition. Then I can experiment with settings and not worry about corrupting my working system.

 I link data back in so it has all the same data and Firefox profiles.

---

### Post by JonPaul on 2013-12-10
Yes but is it 'better' than Saucy and if so in what way? Other than being on the bleeding edge is there are advantage to trying Trusty?

---

### Post by zika on 2013-12-10
> **JonPaul said:**
> Yes but is it 'better' than Saucy and if so in what way? Other than being on the bleeding edge is there are advantage to trying Trusty?To (mis)quote: ask not what Ubuntu can do for you—ask what you can do for Ubuntu. In other words, here we are not (noly) seeking for the improvements that are getting to RR but we are testing RR in order to provide/secure those improvements get into RR on time. At least that is the way I do sincerely look at things here.

---

### Post by shwallace on 2013-12-10
just started testing the 14.04 daily build from 9 Dec. I have a newer Toshiba laptop that 13.xx versions could not find the wireless. 14.04 finds it with no problems. System speed seams very good. Attempting to change the screen brightness hangs up the machine.

---

### Post by marco-parillo on 2013-12-10
> **JonPaul said:**
> Yes but is it 'better' than Saucy and if so in what way? Other than being on the bleeding edge is there are advantage to trying Trusty?
In the case of Kubuntu you get [KDE Release Candidate of Applications and Platform 4.12]("http://www.kubuntu.org/news/kde-sc-4.11.97") without resorting to a PPA.

---

### Post by Cavsfan on 2013-12-10
> **oldfred said:**
> I prefer to just install to another 25GB / (root) partition. Then I can experiment with settings and not worry about corrupting my working system.

 I link data back in so it has all the same data and Firefox profiles.

+1 I'll second that opinion. It's pretty smooth. I'm mainly in (what is listed as ) Flashback and it has a 1:30 delay before everything kicks in but, nothing has been a show stopper.

I've got most of mine on 20GB partitions except 2 and that seems to be enough although 25GB sounds good.

I too simply drop .mozilla and .thunderbird into the new home directory and chromium into ~/.config/ and everything is all saved.

---

### Post by oldos2er on 2013-12-10
It's stable for me running a wm instead of a full DE.

---

### Post by craig10x on 2013-12-11
I'm running 13.10 final now and tempted to upgrade into development again (14.04)....resist....resist...:D
So, it's been pretty trouble free then?   Maybe i should toss a coin (lol)... ;)

---

### Post by sammiev on 2013-12-11
> **craig10x said:**
> I'm running 13.10 final now and tempted to upgrade into development again (14.04)....resist....resist...:D
So, it's been pretty trouble free then?   Maybe i should toss a coin (lol)... ;)

Use a quarter with double side heads and call heads after you flip! ;)

---

### Post by JonPaul on 2013-12-11
Thanks for your reply Marco but I am a Unity user - I prefer that to KDE having tried several DEs

---

### Post by Cavsfan on 2013-12-11
Personally I can't stand Lunity. I do love Flashback though. ;)

[[IMG]http://en.zimagez.com/miniature/flashbackscreenshotfrom2013-12-11.png[/IMG]]("http://en.zimagez.com/zimage/flashbackscreenshotfrom2013-12-11.php")



[[img]http://en.zimagez.com/miniature/flashbackscreenshot2from2013-12-11.png[/img]](http://en.zimagez.com/zimage/flashbackscreenshot2from2013-12-11.php)

---

### Post by grahammechanical on 2013-12-11
There is one issue that I do not see mentioned here. It is an intermittent bug where the password panel does not accept character input. I get around it by clicking the keyboard layout icon and then the password panel will accept character input.

Regards.

---

### Post by Redalien0304 on 2013-12-11
what about the Extras Repoisitory has it been fixed yet in Trusty. I have it Disabled now.

---

### Post by Cavsfan on 2013-12-11
> **grahammechanical said:**
> There is one issue that I do not see mentioned here. It is an intermittent bug where the password panel does not accept character input. I get around it by clicking the keyboard layout icon and then the password panel will accept character input.

Regards.

I had that problem for a while but I think it disappeared when I re-installed.

```
cavsfan@cavsfan-MS-7529:~$ ls -ld /var/log/installer | awk '{ print $6 " " $7 " " $8 }'
Nov 24 10:51
```

I think I got that command from VinDSL.

> **Redalien0304 said:**
> what about the Extras Repository has it been fixed yet in Trusty. I have it Disabled now.

No the Extra Repository is unavailable still. You will see Trusty on this link when it is available.

[http://extras.ubuntu.com/ubuntu/dists/](http://extras.ubuntu.com/ubuntu/dists/)

---

### Post by Hazzabin on 2013-12-11
> **grahammechanical said:**
> There is one issue that I do not see mentioned here. It is an intermittent bug where the password panel does not accept character input. I get around it by clicking the keyboard layout icon and then the password panel will accept character input.

Regards.

And I was thinking I had done something wrong, this has only just recently started....was ok before, another screwed-up update no doubt

---

### Post by Cavsfan on 2013-12-11
The Saucy Extras Repository was not even available until after Saucy was at final release.

Saucy 13.10 was Final Release on October 17, 2013 and the Saucy Extras Repository was not available until December 11, 2013.

---

### Post by WebDrake on 2013-12-11
Glad to hear that the quality standard is up there where I'd expected.  I've never upgraded pre-Alpha 1 before, and I may still wait for 19 December, but I was curious about how things would be ...

Thanks everyone for all your comments and advice! :-)

---

### Post by Cavsfan on 2013-12-11
> **WebDrake said:**
> Glad to hear that the quality standard is up there where I'd expected.  I've never upgraded pre-Alpha 1 before, and I may still wait for 19 December, but I was curious about how things would be ...

Thanks everyone for all your comments and advice! :-)

You are most welcome. I hope you will be using an additional partition for Trusty. My main distro is Precise 12.04 the current LTS and I also have Mint 13 Maya (essentially Precise).
The rest are for fun. :)

---

### Post by rrnbtter on 2013-12-11
Greetings,
@WebDrake
I'm have been using Trusty since it opened for testing as my primary and only os. In my opinion it is an excellant OS. I am satisfied with my experience with Trusty beyond expectations. Now for the downside. If your partitions don't facilitate an easy reinstall or if you are unconfortable with a reinstall I would suggest that you stick with what you have until Trusty goes LTS Final. Trusty has had days with great total crash potential depending on your skill set.

---

### Post by WebDrake on 2013-12-16
Well, I updated a couple of days ago, and the main problem was actually building the USB install disk, as Startup Disk Creator on 13.10 just kept crashing.

There was a hairy/worrying moment when the installer seemed to be frozen, although a quick look at top confirmed that dd was hard at work (actually, that could have been more rather than less worrying :-) ).  But now that it's installed it's installed, and working fine, and in fact a couple of small irritations with 13.10 seem to have been fixed.

Yes, there's some potential for things to go BOING in some horrible way, but it's not the first time I've rescued an alpha Ubuntu install via a USB key + chroot, and such a scenario seems to be getting less and less likely with every Ubuntu release (famous last words ...).

---

### Post by pete04 on 2013-12-16
Installed fresh on Friday. Only very small glitches. Have Chrome Stable and Dropbox added. Trying to be minimal in tweaking so as not to upset anything.

Small issues I've had:
1) Have had to select language from the panel on login before I could type. This morning's updates seemed to fix this.
2) Suspend would hang up the system. Happened 3 times.
3) Rhythmbox controls aren't in the sound menu
4) I've had warnings that the repos couldn't be accessed when I run the installer, but the updater works just fine after I close the error window.
5) Image Viewer is having trouble viewing jpgs at random. And hangs when I save photos (usually, having opened them via Thunderbird).

That's it. I have not been blitzed by apports, etc. Just running rather reliably. This is the first time I've run a release pre-beta.

Using a System 76 Lemur Ultra, it's 1 year old approx.

---

