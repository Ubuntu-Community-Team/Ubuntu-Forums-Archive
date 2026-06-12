---
title: "Dont allow Ubuntu to drop alternate installers!"
date: 2012-10-20
forum: The Cafe
---

### Post by SimonDoe on 2012-10-20
Today im rolling out 12.04 for my new servers with custom installers based on alternate installers.

And now i found out this !
**Proposal to drop Ubuntu alternate CDs for 12.10**
* [https://lists.ubuntu.com/archives/ubuntu-devel/2012-August/035675.html](https://lists.ubuntu.com/archives/ubuntu-devel/2012-August/035675.html)
**Linux Today - Canonical Drops Alternate CDs from Ubuntu 12.10**
* [http://www.linuxtoday.com/upload/canonical-drops-alternate-cds-from-ubuntu-12.10-120831062000.html](http://www.linuxtoday.com/upload/canonical-drops-alternate-cds-from-ubuntu-12.10-120831062000.html)

Dear **Steve Langasek. **(writer of this proposal)
Altho i want to use a ton of insulting and not appropriate words at this point i try to remain calm and lay out why nobody should kill alternate installers.
* What you say: "*Other flavors are free to continue building alternate CDs (i.e., "debian-installer" CDs) according to their preference*".
It is a bit absurd because i build my personal flavour with install automation and a slight different application choices off the original Ubuntu alternate installer.Isn't it absurd to use example: LUBUNTU alternate to stripp off LUBUNTU-GUI and replace it with GNOME-GUI again, just to get your slightly modified automatically installing Ubuntu ?[B]?

Maybe **Steve Langasek**, the proposer of this change thinks we dont care.
Show that you care about alternate installer by taking part in this petition:
[http://www.change.org/petitions/ubuntu-do-not-drop-altrnate-installer-support](http://www.change.org/petitions/ubuntu-do-not-drop-altrnate-installer-support)

* **Only thing left to build _offline_ autoamated installers is from alternate installer**:  
InstallCDCustomization - [https://help.ubuntu.com/community/InstallCDCustomization](https://help.ubuntu.com/community/InstallCDCustomization)
(if you can add the link to this topic on that wiki page, my launchpad account seems broken or something)
By RoyK                 Oct 14, 2012, 06:05: This isn't too smart. They should have either integrated the text installer in the main CD, or kept the alternate...

* [B]The other primary reason is when graphical installer just fails!
[/B]By  ac                 Aug 31, 2012, 19:55: ... installation CD fails my  graphic card (Nvidia GT550 ti). I get around this by installing Ubuntu  with the alternate CD...

* LVM / RAID / DRBD / other filesystems etc.. 
Again for special server purposes mostly.
Why even bother making them available for graphical install. 
How many % home PC-s use this complex stuff ? 
I dont use it for my laptop nor home server. 
Fine.. and if you make it to GUI installer.. 
can we (server admins) automate/preseed the GUI installer ? 
Probably not !

* Minimal installer wont work so good in (firewalled/offsite internetless server rooms).
You could try to create a repository on your laptop and install from it via minimal installer.. 
but that takes like 1000% more effort, than just to remaster the alternate installer.

* More ? Read the comments from the news:
[http://news.softpedia.com/news/Canonical-Drops-Alternate-CDs-from-Ubuntu-12-10-289338.shtml](http://news.softpedia.com/news/Canonical-Drops-Alternate-CDs-from-Ubuntu-12-10-289338.shtml)
[COLOR=DarkRed]
[/COLOR]

---

### Post by whatthefunk on 2012-10-20
While I too agree that Alternate Install CDs should not be dropped, your poll options are really confusing.

> Agreeing to the topic reasoning more than to the proposal of dropping alternate.
:confused::confused::confused:

A simple "Yes" and "No" would be much better.

---

### Post by mips on 2012-10-20
The decision is already made, a poll is not going to change that.

You said you are using this for servers? Why don't you customise the server or mini iso? As far as I know they still use the text base installers.

I'm not happy with the dropping of the alternate images either but no amount of unhappiness from my side is gonna make them change their minds.

---

### Post by castrojo on 2012-10-20
You can preseed the GUI installer: [https://wiki.ubuntu.com/UbiquityAutomation](https://wiki.ubuntu.com/UbiquityAutomation)

- Also the mini ISO isn't going away if you want to use that, which is basically the same thing.

---

### Post by SimonDoe on 2012-10-21
**_offline_** = you most likely need most packages in "main" pool, which are not included in mini iso. So you either have to create your own repository, or modify mini iso in such exent that it becomes like "alternate installer", which both seem really complex tasks.

**_GUI fail_** = ubiquity cannot run with some graphics problems it may have. I have not tryed "ubiquity automation", so i wouldn't know if only the graphics fail, or the whole installer. 
(The hardware that had that problem is currently running windows, so i can't test it - servers all used text-mode, so i don't know how many would fail in GUI mode.)

Im usually not preseeding formatting (risky stuff with production servers).
So with GUI fail, the partly automated installer will get stuck at this step.

PS:
Decision being done and being undoable ?
They brought back abaility to use classic GNOME, 
and there are other changes because of what people expressed they need.
You as a user just express what you think.

---

### Post by Paqman on 2012-10-21
The mini.iso spanks the alternate installer IMO. Haven't used the alternate in years. If it's true that you can do even the more specialised partitioning schemes like LVM without it then it does seem like it's become a bit superfluous. Are offline installs common? Bit of a special case, surely?

---

### Post by SimonDoe on 2012-10-21
> **Paqman said:**
> Are offline installs common? Bit of a special case, surely?
Im the guy who uses the stuff that ALWAYS works. I can never be sure if my client has 56kb internet/or none at some remote office site.

So far i have never failed at installing step thanks to alternate.

Are installs in general common for regular people ? 
Probably not. That doesn't mean you should fail installing to some hardware because of a GUI.

---

### Post by whatthefunk on 2012-10-21
> **Paqman said:**
> The mini.iso spanks the alternate installer IMO. Haven't used the alternate in years. If it's true that you can do even the more specialised partitioning schemes like LVM without it then it does seem like it's become a bit superfluous. Are offline installs common? Bit of a special case, surely?

The mini.iso has one major flaw.  If the installer doesnt auto configure your internet connection (no linux distribution ISO has ever been able to do this with mine) you can do nothing.

---

### Post by Lisiano on 2012-10-21
What's the problem?
If you need to install via a text-based mode, pop in the server CD.
Then once you are done, just tell Ubuntu to apt-get update and to install ubuntu-desktop
If for some magical reason you are with a person who has no internet and needs a desktop, pop in the server CD, install, pop in the desktop cd, run apt-cdrom add and the usual apt-get update and install ubuntu-desktop.
And IMHO, if the person needs to use a text based installer, I'm sure that same person won't be afraid to run 2 or 3 commands after they boot up.

Also, a simple Yes/No would be better in this pool. Maybe also a Maybe in it, for those who more or less have no opinion on this subject.

---

### Post by Paqman on 2012-10-21
> **whatthefunk said:**
> The mini.iso has one major flaw.  If the installer doesnt auto configure your internet connection (no linux distribution ISO has ever been able to do this with mine) you can do nothing.

Have you filed a bug? That's a pretty major one. I would consider slapping in a new NIC if your current one is that broken on Linux. They're cheap.

---

### Post by whatthefunk on 2012-10-21
> **Paqman said:**
> Have you filed a bug? That's a pretty major one. I would consider slapping in a new NIC if your current one is that broken on Linux. They're cheap.

Havent filed a bug.  Is this even a bug?  Its not a hardware issue.  The box Im on now is only 6 months old and has always had this problem.  My laptop, which works fine at my parents house, has the same problem.  Network Manager has also proven to be completely useless in configuring my network.  the only thing that works is pppoeconf.

---

### Post by mips on 2012-10-21
> **whatthefunk said:**
> Havent filed a bug.  Is this even a bug?  Its not a hardware issue.  The box Im on now is only 6 months old and has always had this problem.  My laptop, which works fine at my parents house, has the same problem.  Network Manager has also proven to be completely useless in configuring my network.  the only thing that works is pppoeconf.

I might be confused but what does pppoeconf have to do with your NIC? Does it not establish a ppp session to your isp?

---

### Post by whatthefunk on 2012-10-21
I dont understand either.  The problem is that no Linux installer has ever been able to connect during install.  After install, I use pppoeconf to establish the connection.

---

### Post by wojox on 2012-10-21
I've done numerous off-line installs with 12.04 - 12.10 with no problems using the Live Desktop ISO.
Really is no need for the Alternate.

---

### Post by qamelian on 2012-10-21
> **wojox said:**
> I've done numerous off-line installs with 12.04 - 12.10 with no problems using the Live Desktop ISO.
Really is no need for the Alternate.
Not so. I have frequently run into PCs that will not install from the Desktop ISO, but they install flawlessly from the alternate. In my opinion, the alternate still serves a definite purpose and eliminating it is a mistake.

---

### Post by whatthefunk on 2012-10-21
> **qamelian said:**
> Not so. I have frequently run into PCs that will not install from the Desktop ISO, but they install flawlessly from the alternate. In my opinion, the alternate still serves a definite purpose and eliminating it is a mistake.

Agreed.  The Desktop ISO takes a lot of gpu power and doesnt work on even slightly old pcs with onboard graphics.

---

### Post by wojox on 2012-10-21
True, Ubuntu doesn't have much love for older hardware anymore. There are other distros for that though. 

You can't run "The Compiz" that well on older machines and that's the default window manager now.

---

### Post by mips on 2012-10-21
> **whatthefunk said:**
> I dont understand either.  The problem is that no Linux installer has ever been able to connect during install.  After install, I use pppoeconf to establish the connection.

Then it's not really an issue with your nic but pppoe. I'm not a fan of pppoe and anybody I come across I recommend they let their router handle the ppp & authentication stuff instead of running it client side. This way all you need is to have TCP/IP configured for your nic and you are good to go.

Who's your isp and what router did they supply?



> **qamelian said:**
> Not so. I have frequently run into PCs that will not install from the Desktop ISO, but they install flawlessly from the alternate. In my opinion, the alternate still serves a definite purpose and eliminating it is a mistake.

My pc happens to be one of those. I can't remember the last time I could get a (x)ubuntu desktop iso to boot on it no matter what boot options I specified. Weird thing is it's not even exotic hardware, it's a Gigabyte MB with Intel CPU & nVidia GPU. Alternate installer always works though. Desktop iso works fine on my laptop though but that i686 vs amd64 for the desktop.

---

### Post by zer010 on 2012-10-21
Well, this is quite unfortunate. I deal with older PCs almost exclusively and some of them do not handle the GUI installer very well which made the Alt installer invaluable.  The argument for using the mini.iso is ridiculous because *gasp!* yes there are still those that either have no internet or are stuck with dial-up(something Linux doesn't handle well these days).   I guess one could use the server.iso  and then apt-get the desktop then apt-get uninstall all of the server stuff,  but that's just silly... not to mention the server edition has a modified kernel vs the desktop version, IIRC.

Of course there are other distros that might work, but I use *buntu because it's my distro of choice.  If I use another distro because of this, I must admit that *buntu is lacking in it's completeness. Bummer....

---

### Post by cariboo on 2012-10-21
@whatthefunk, I'd suggest you create a bug report. I created a bug report about wireless firmware not being included with the mini.iso, and that was solved very quickly.

---

### Post by qamelian on 2012-10-21
> **wojox said:**
> True, Ubuntu doesn't have much love for older hardware anymore. There are other distros for that though. 

You can't run "The Compiz" that well on older machines and that's the default window manager now.
I'm not talking about exclusively older hardware. Many of the machines I've had problems with are less than 3 years old.

---

### Post by mr john on 2012-10-22
Getting rid of the alternate installer would be a big mistake. It's the best contingency measure for installing Ubuntu on machines where the graphical version fails. Doing it with the server cd would be messy, take extra work and I thought the server version came with a different kernel anyway? 

It seem that the resources in Ubuntu are being put into Unity and Ubuntu One instead of helping Ubuntu be compatible with hardware.  The only reason I kept using Ubuntu was because it worked well with my hardware, but if the focus is only on aesthetics then things are going to stop working pretty soon.

---

