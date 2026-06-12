---
title: "Edgy Poll: worst in terms of installation pains, Yes or NO"
date: 2006-11-02
forum: The Cafe
---

### Post by krypto_wizard on 2006-11-02
Hi, I wanted to start a Poll by asking if you think that Edgy is the worst version starting warty in terms of Installations pains.

I don't know how to create a Poll.

But many people in this forum will agree with me that Edgy has been Pain in the A** as far as installation is concerned.

I have alrady two unsuccessful attempts: one on my gf's laptop and one on my dual boot PC.

Mods, is there a way you can make this poll and improve the quality of Edgy.

Thanks

---

### Post by taurus on 2006-11-02
There is a similar thread in the Cafe so please look in there and if you need to create a poll, do it in the Cafe area.

Move to Cafe...

---

### Post by Engnome on 2006-11-02
Had no trouble installing it. The problem for many (including me) is that upgrading (something linux has been good at) didn't work very well with many broken X servers as a result.

---

### Post by dca on 2006-11-02
No problems with Edgy (may be too soon to tell) because I have no high-speed gadgets in my laptop like nVidia graphics and the like, however, I never perform OS upgrades.  ie: 2000 to XP using XP upgrade CD or Ubuntu 6.06 to 6.10 using online update.  I generally copy the /home folder and install (upgrade) fresh from LiveCD(s)...

---

### Post by Tamil on 2006-11-02
No problems with Edgy install.

---

### Post by Rhubarb on 2006-11-02
No problems with installing edgy here either.  In fact it was much more friendly towards my nvidia 7400 Go than dapper was.
Though I do feel edgy is more unstable, but I like being on the edge!

---

### Post by Mr. Picklesworth on 2006-11-02
After I figured out that it wasn't automatically mounting a swap, it went fine.

Of course, not mounting swap was horrible!
My poor old Lesser computer can't handle the live CD without a swap partition, and I bet there are a lot of other people in the same boat.
It really got me by surprise because the Dapper live CD *did* automatically mount the swap partition and ran fine.

After that, the installation was fast and and easy :)

---

### Post by tomdkat on 2006-11-02
After upgrading from Dapper to Edgy (AMD64), X refused to start due to a missing flgrx module.  I booted from a liveCD I have and found how to re-install that module and things have been fine (mostly) since.

Still exploring Edgy 64-bit.  :)

Peace...

---

### Post by Ramses de Norre on 2006-11-02
All went fine here..

---

### Post by BLTicklemonster on 2006-11-02
Install, no problem.

Getting it right, I'm still working on it... but I like it enough that it is what I boot to now. I have totally maimed it twice and fixed it both times without having to reinstall, which says nothing  about Edgy, it's just I'm getting better at linux.

---

### Post by geoffm33 on 2006-11-02
Bought used Thinkpad T23 from Ebay. Arrived at 2pm with Win2K installed. By 3pm I had it dual booting Edgy and Win2K (after resizing the NTFS partition). So far so good.

---

### Post by spinflick on 2006-11-02
So where is it? ...... the Poll that is :p

---

### Post by fuscia on 2006-11-02
upgrading was a mess, but a clean install was drunken child easy.

---

### Post by gerowen on 2006-11-02
I upgraded my wife's laptop from Dapper to Edgy with no problems, and did a clean install of Edgy on my desktop.  The only problem I had was on my desktop, which I also had with Dapper.  The PCI address of my NVidia card wasn't detected and it kept trying to use my on-board card.  A quick xorg edit fixed that so I could get to the desktop and the installation and everything else went without a hitch.

---

### Post by Aranel on 2006-11-02
I didn't have a single problem installing it, configuring it, *or* getting everything to work - and that includes my Broadcom wireless card. Edgy has run flawlessly for me since.

Dapper, on the other hand, refused to install at all - from the LiveCD, alternate installer, or even the other installation methods (KNOPPIX LiveCD, GrUB4DOS, etc.). I ended up installing Debian Sarge instead, and *recompiling* (on a Celeron!) and upgrading my kernel, to be able to even use my wirless card.

In my experience, Edgy is a giant leap ahead of Dapper as far as, um, actually working. :D

---

### Post by P_Badger on 2006-11-02
Massive upgrade failure in two computers I tried updating, so I had to do a fresh install of edgy on both.

My bf's attempted upgrade of his ubuntu install on his macbook resulted in a complete failure so bad he wasn't able to login at all. : P

I've found edgy to work quite fine after the install, though, and I'm quite happy with it.

On a side note, have the ubuntu people made any mention why the edgy upgrade is so failure prone?

---

### Post by ChadMMc on 2006-11-02
My upgrade to edgy had as many problems as my upgrade to dapper and my install of breezy... i.e. None. 
Ubuntu Rocks!
:)

---

### Post by Bezmotivnik on 2006-11-02
> **BLTicklemonster said:**
> Install, no problem.

Getting it right, I'm still working on it.

Yeah, it really bugs me how people never **explicitly** define their terms.  It seems to be endemic here to leave terms as vague as possible in order that there's enough weasel-room so everyone can stretch reality in favor of a "positive outcome" and "feeling good about" Ubuntu (or Linux, or whatever) at the expense of the truth:

Was it a "problem-free installation" if it got to the end without crashing and booted, but X, Y and/or Z doesn't work when it was supposed to?

In my book, no.

*Vide* "recognized," "supported," etc.

---

### Post by Kateikyoushi on 2006-11-02
Did two clean beta installs almost everything worked out of the box including my wireless already with beta.
I bet upgrading can be a mess especially with modified systems using xgl beryl and whatnot.

---

### Post by hizaguchi on 2006-11-02
I did a fresh install and the only problem was that I had to delete and recreate a partition before the installer would format it.

Now that it's installed though, things are way messier.  Suspend either works perfectly or locks up the computer, with no way to tell which will happen (worked fine in Knot 2).

My sound worked right after install, but now alsa has been mysteriously smote and the only way I can hear anything is with OSS through one speaker.

Network manager freezes up the whole system when I'm connected to a WEP encrypted network for more than a few minutes.

I had to delete my saved Gnome session because it randomly decided to insert 20 or so instances of Nautilus and I couldn't get rid of them any other way.

Speaking of Gnome, some of the components (notably the theme manager, but probably others I've not found yet) use 100% CPU after running for a few minutes.  This was a problem that came and went back during Knot 2, and I guess it's here to stay now.

About 30% of the time, if I kill X the computer locks up when GDM tries to restart it.

Xorg 7.1 comes with compositing enabled by default, which breaks direct rendering with fglrx unless disabled in 2 different places in xorg.conf.

Gnome-settings-daemon sometimes fails to start with the rest of Gnome.


That's all I can think of off the top of my head, but I've only been using Edgy for 2 days.  But it sure is up to date and stuff!  I hope the next release is tested a little more thoroughly.  Dapper really set a high standard thanks to the extra 2 months, and that makes Edgy a huge disappointment.

---

### Post by qamelian on 2006-11-02
> **krypto_wizard said:**
> Hi, I wanted to start a Poll by asking if you think that Edgy is the worst version starting warty in terms of Installations pains.
Not even close! Warty was good enough to get me interested in Ubuntu, but Edgy gave me far less grief when installing. After Warty, I had to do about a dozen different things just to get sound and never could get wireless working. On Edgy, I spent maybe five minutes sorting wireless out with bcm43xx-fwcutter and everything else worked without any intervention on my part at all.

I'm liking Edgy so much, I might just buy me a newt!

---

### Post by .t. on 2006-11-02
No problemos here.

---

### Post by Pathfinder_ on 2006-11-02
I had a problem but with Kubuntu. when i wanted to install it on my sata drive qtparted would quit. For some odd reason gparted didn't have this problem, so i ended up installing Ubuntu, but i would have preferred Kubuntu. 
BTW, I didn't have this problem with dapper

---

### Post by Polygon on 2006-11-02
dist-upgrade from dapper was a disaster. slow download speeds, and when i restarted after all was well i got a "fsck died with error code 8", then after i skipped that, it said it couldent find my home folder, x couldent start... etc etc.

im sure a fresh install would work, but come on, breezy to dapper upgrade was better then this!

---

### Post by NeoLithium on 2006-11-02
I upgraded and everything so far seems to be ok; although time will tell with some things that I might have not noticed yet.

---

### Post by Steveire on 2006-11-02
> **P_Badger said:**
> On a side note, have the ubuntu people made any mention why the edgy upgrade is so failure prone?
They seem to be blaming Automatix and EasyUbuntu

[http://www.netsplit.com/blog/articles/2006/10/30/automatix-and-upgrading](http://www.netsplit.com/blog/articles/2006/10/30/automatix-and-upgrading)

---

### Post by slimdog360 on 2006-11-02
It was about the same as dapper for me, from the live cd that is. I also tried a server install and they updated that nicely. So much easier now from a server install.

---

### Post by 23meg on 2006-11-02
No problems, neither with install nor afterwards.

---

### Post by notoriousdbp on 2006-11-02
A virtually seamless transition.  Had a small issue with ndiswrapper loading on boot with the new kernel but, as I could get online with the old kernel, I found a solution.  Didn't lose any data and now have shiny new versions of firefox and gaim.

---

### Post by viper on 2006-11-02
No major drama here either, just a few bits and pieces to fix after the upgrade (did the upgrade rather a fresh install)

---

### Post by d3v1ant_0n3 on 2006-11-02
My computer had a dizzy spell while I was partitioning yesterday. The comp seems to decide that the battery is dead and turns itself off, even tho it runs on mains 95% of the time. So it killed my install.

I didn't have an edgy disc, and figured it would be faster to install Dapper and upgrade.

Here comes the bit that you've read 1000 times before in the last week or so. EDGY BROKE MY COMPUTER! IT DIDN'T WORK! X IS BROKEN! I CAN'T GET ONLINE. EDGY IS ****!CANONICAL ARE IDIOTS!

Except it's not coming.

Upgrade was flawless. Servers were fast.

Upgraded fine from a fresh install. Was up and running in less than 90 mins, everything back to normal and prettified (themed, Beryl'd up), all my apps and backups back on within 3 hours. Except I've decided to try GNOME for a while rather than KDE.

The new Usplash is much better than the one in the beta, incidentally.

---

### Post by nbound on 2006-11-02
No problems... only had to do basically the same stuff as in dapper/breezy.

(Install proprietary display drivers on both PC and laptop, Install wireless card with ndiswrapper on my laptop). Neither is very complicated.

---

### Post by learning on 2006-11-02
worked great for me on one desktop and a laptop.  Only issue was on laptop had to download gnome network manager to get wireless working right for me, but it was no problem, and has been fine since... and I think if I were better at this I could have made the wireless work from the command line from what I have read.

---

### Post by jnev on 2006-11-02
I burned three different cd's trying to install it... none worked. one wouldn't boot off the live cd. the alternate install froze at the same spot every time I tried it, and the live dvd also froze at the same spot in the install. I finally just stuck in my old dapper cd, installed that and then upgraded by changing the sources.list. everything's worked fine since.

---

### Post by mrgnash on 2006-11-02
No problems on my Travelmate 4402 -- had it up and running with AIGLX + Beryl in no time flat, wheras all my previous Ubuntu installs on this machine have required xorg.conf tweaking in order just to get the xserver up and running properly, let-alone to get XGL/AIGLX working; plus on Dapper, I never overcame the issue of occasional hard-locking under Compiz/Beryl.

---

### Post by katgfan on 2006-11-03
Have no problems installing it, same for me as for Breezy and Dapper,. i have it on my Dell 8400 and NEC Versa.

---

