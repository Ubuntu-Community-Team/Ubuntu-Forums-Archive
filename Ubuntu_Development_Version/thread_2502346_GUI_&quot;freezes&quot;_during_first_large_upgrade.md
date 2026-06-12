---
title: "GUI &quot;freezes&quot; during first large upgrade to plucky"
date: 2024-11-10
forum: Ubuntu Development Version
---

### Post by este.el.paz on 2024-11-10
et al:

This morning I ran what was the first large number of packages after upgrading to plucky . . . the GUI "froze" when it hit the "udisk" package at "77%" completion . . . mouse worked, but nothing repsonded to it.  Had to shut down using power button.  On reboot, went back to plucky, ran apt dist-upgrade again . . . showed "one package" available . . .ran it through and did the usual autoremove/autoclean . . . all that seemed to go well.

Shut it down again, haven't checked it to see if all is again, "well" with plucky . . . ????  It is rare to have this kind of problem with the ubuntu based flavors, even if "alpha" . . . .

---

### Post by guiverc on 2024-11-10
I've upgraded two *oracular* installs to *plucky* using `do-release-upgrade -d` thus far, and had no issues with either (*none noteworthy anyway*).

I'm on my primary box now, and this box was super clean & I noted nothing.  I also *release-upgraded* a QA test box to *plucky* and I'm not sure why, but `featherpad` didn't appear on the *plucky* install which I expected.. but that could have been the result of some changes I'd made myself (*the install wasn't clean as I'd used it for testing & some other exploration, but I didn't check out what I'd done to it*) so I didn't file any bugs about it.

FYI:  I upgraded the QA testbox, as my primary box is using the official packages only, and I wanted to explore the LXQt 2.1 first on the testbox I don't care about if problems occur.. I've not experienced issues with LXQt 2.1 (*used it >16 hours now*) however the Wayland session is still being worked on by the team...  If interested I'm talking about [https://launchpad.net/~lubuntu-dev/+archive/ubuntu/lxqt-2.1](https://launchpad.net/~lubuntu-dev/+archive/ubuntu/lxqt-2.1) but please DO NOTE THE WARNING

> 
Don't enable this, please. You'll likely wreck your system


which is why I'm using a testbox, and my *primary* box.  We'll do an official upload one we consider it *stable* or at least close to it.

I wonder what command you used to perform the *release-upgrade*, as I may have used the [text] terminal, as I don't always look up the *GUI command* that ensures screensaver etc doesn't kick in, and potentially lock the upgrade, and to be honest, I'm too lazy to look that detail up (*unless I'm doing a specific QA test of it, where I just copy/paste the actual command usually*).

---

### Post by este.el.paz on 2024-11-10
> **guiverc said:**
> I've upgraded two *oracular* installs to *plucky* using `do-release-upgrade -d` thus far, and had no issues with either (*none noteworthy anyway*).

I wonder what command you used to perform the *release-upgrade*, as I may have used the [text] terminal, as I don't always look up the *GUI command* that ensures screensaver etc doesn't kick in, and potentially lock the upgrade, and to be honest, I'm too lazy to look that detail up (*unless I'm doing a specific QA test of it, where I just copy/paste the actual command usually*).

I just edit the sources.list . . . changing wherever I see say, "oracular" is changed to "plucky" . . . and then run apt dist-upgrade.  The first time was only like 11 packages, today was perhaps 400+ packages . . . it wasn't the screensaver cutting in . . . .  Perhaps I could have run it in a TTY or as root, but I just sudo'd it . . . .  I was in a hurry this morning, didn't take any "safety" precautions . . . the Lubuntu install is possibly the longest lived linux install I have on that machine, maybe going back to '16, first one in . . . updated to dev each time by editing the sources.list .. . still going and going.

Today's "freeze" was an "anomaly" . . . "atypical" behavior, usually very well behaved . . . nothing blows up, as a few of my other systems do.

---

### Post by guiverc on 2024-11-10
Your method of upgrade can have problems; it's how you upgrade a Debian system, and maybe 95%+ of how the [Ubuntu Release Upgrader tools]("https://launchpad.net/ubuntu-release-upgrader") actually achieve the *release-upgrade*, however they also ensure specific packages can upgrade in a specified order, that can avoid issues where python3 version changes (*as example*), as Ubuntu has a *tad* more python3 code than exists in some parts of Debian, as well as other *niceties* such as disabling screensaver etc (*which can create a stuck GUI*).

Myself, I delayed my *bumping* to *plucky* intentionally, so I could use the *official *procedure, as that also causes your system to *fully upgrade* and catch the changes that *should* occur during *release-upgrade* process, as your method usually doesn't cause the *code* that performs those change to, eg. parts of your *plucky* system may not follow *plucky* procedures, but still use older procedures as you upgraded packages only & didn't run the *release-upgrade* scripts (*some actually do it your [or the Debian way] to avoid the release changes to I suspect; not liking the newer changes that Debian & Ubuntu are introducing*).

---

### Post by este.el.paz on 2024-11-10
@guiverc:

Others have stated the same basic idea . . . but, two things . . . after you posted on the plucky dev thread that you had just run the "do-release-upgrade -d" command . . . sometime after that, hours, or days . . . I ran that command and it came back "nothing to do" or "nothing to upgrade to" . . .?? 

And, then, I have done this method, as yes, I have in debian . . . as well as numerous folks on the ubuntu forums had recommended . . . by editng the sources.

Be it ever so "wrong" since way before the machine I have now . . . many many  times.  It might take a few apt's to get the system running itself well.

---

### Post by guiverc on 2024-11-10
I've used it myself too (*many many times, I'd not be surprised if it was 50% of the times I'd upgraded, though it may have been few times than that; I really can't recall*), but it's not the recommended way to *release-upgrade* a Ubuntu system, as the Ubuntu *devs* do code specific things to run during a *release-upgrade* cycle (*especially tasks that are for specific cycles*), and just changing sources will mean those changes never occurred.

My point was only to make you aware of ***potential*** differences, an example of a difference is if you have a really old install say (install with *focal* or 20.04 for example) and have upgraded thru all releases every six months and are now on *plucky* (25.04) but done it only via modification to your sources may still be found in /etc/apt/sources.list for example, rather than your sources being re-populated in /etc/apt/sources.list.d/ubuntu.sources, this change may not have occurred on my example system here due to that script never being run.   I'm not currently aware of any reasons why this could be a problem (*in fact users who don't like change may prefer it the old way*), but your system is now *slightly* different to what is expected for your release. 

I'm using this as example of a *tiny* difference(s) than can exist; and only mentioning it as *information detail* only. If you're aware of these differences, I have no problem with you choosing to operate your system as you feel is most appropriate for you; after all its your system!

---

### Post by corradoventu on 2024-11-11
On Ubuntu I used update-manager -d -c according suggestion in [https://iso.qa.ubuntu.com/qatracker/milestones/464/builds/316648/testcases/1310/results](https://iso.qa.ubuntu.com/qatracker/milestones/464/builds/316648/testcases/1310/results) and upgrade was successful

---

### Post by grahammechanical on 2024-11-11
Slightly related to this discussion. I updated noble to oracular using the sources.list method and the icon for the App Centre did not update to the new design for the icon. Now I know why.

Regards

---

