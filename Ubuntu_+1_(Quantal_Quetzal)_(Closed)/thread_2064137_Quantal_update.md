---
title: "Quantal update"
date: 2012-09-28
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by cariboo on 2012-09-28
I just found this in my inbox, from Kate Stewart:

> Dear Developers,
    We've just released Beta 2 now,  and I wanted to say thank you for
all your excellent work on the release to date!     We're now entering
the final phase of polishing the release and removing those last nasty
bugs. 

    We will be keeping the Quantal archive in pre-release freeze state
from now until release, due to the high rate of churn on some projects,
and the need to keep the dailies building between now and final freeze.
Please continue to upload your fixes to quantal (or quantal-proposed, if
there is likely to be archive skew issues from the build),  and they
will be reviewed by the release team.   

   Only bug fixes should be uploaded now, and features should NOT be
mixed in with the bug fixes.   If you have a compelling reason why a
FFE/UIFE needs to be granted, please make sure that code is in its own
upload, and discuss it with the release team on #ubuntu-release in
advance. 

    Some of the key dates coming up [1] are:

* October 4 - Kernel Freeze[2],  Desktop Infrastructure Freeze[3]
* October 9 - Translation Deadline[4],  Seeded Images Final Freeze [5]
* October 11 - Release Candidate [6], and Release Note Content Freeze[7]
* October 16 - Unseeded Universe Final Freeze [5]
* October 18 - 12.10 Release

   As you can see,  there not that much time left between now and Final
Freeze, so all fixes to Critical/High bugs are most welcome in this next
upcoming week.  

  Thank you again for all your excellent work over this release cycle,
and your help on feeding our Quantal Quetzal those last important bug
fixes.  

Kate Stewart,
on behalf of the Ubuntu Release Team.

[1] [https://wiki.ubuntu.com/QuantalQuetzal/ReleaseSchedule](https://wiki.ubuntu.com/QuantalQuetzal/ReleaseSchedule)
[2] [https://wiki.ubuntu.com/KernelFreeze](https://wiki.ubuntu.com/KernelFreeze)
[3] [https://wiki.ubuntu.com/DesktopInfrastructureFreeze](https://wiki.ubuntu.com/DesktopInfrastructureFreeze)
[4] [https://wiki.ubuntu.com/TranslationDeadline](https://wiki.ubuntu.com/TranslationDeadline)
[5] [https://wiki.ubuntu.com/FinalFreeze](https://wiki.ubuntu.com/FinalFreeze)
[6] [https://wiki.ubuntu.com/ReleaseCandidate](https://wiki.ubuntu.com/ReleaseCandidate)
[7] [https://wiki.ubuntu.com/ReleaseNotesFreeze](https://wiki.ubuntu.com/ReleaseNotesFreeze)




---

### Post by ventrical on 2012-09-28
Thanks for the heads up.

---

### Post by SheamusPatt on 2012-09-28
I've been waiting for Beta 2, in the hopes that it would represent a consistent set of packages and fix the "Partial Upgrade" warnings that I've been getting for the past couple of weeks. Based on [https://wiki.ubuntu.com/U%2B1/partial_upgrade](https://wiki.ubuntu.com/U%2B1/partial_upgrade) I have **not** run a partial upgrade, but even though Beta 2 is now out, I'm still getting partial upgrade warnings.

Any advice on how to proceed? Should I just blast ahead, and take the chance that things might be so busted that I'll have to reinstall the release version from scratch? Or, should I wait some more for things to settle down and the Partial Upgrade warnings to go away? Will they ever go away?

I'm running on

Linux xxx 3.5.0-14-generic #15-Ubuntu SMP Thu Sep 6 23:05:06 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by Curtis6767 on 2012-09-28
> **SheamusPatt said:**
> I've been waiting for Beta 2, in the hopes that it would represent a consistent set of packages and fix the "Partial Upgrade" warnings that I've been getting for the past couple of weeks. Based on [https://wiki.ubuntu.com/U%2B1/partial_upgrade]("https://wiki.ubuntu.com/U%2B1/partial_upgrade") I have **not** run a partial upgrade, but even though Beta 2 is now out, I'm still getting partial upgrade warnings.

Any advice on how to proceed? Should I just blast ahead, and take the chance that things might be so busted that I'll have to reinstall the release version from scratch? Or, should I wait some more for things to settle down and the Partial Upgrade warnings to go away? Will they ever go away?

I'm running on

Linux xxx 3.5.0-14-generic #15-Ubuntu SMP Thu Sep 6 23:05:06 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

Don't know if this will work for you, but has worked for me when I've gotten 'partial update' notices.

```
sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade

```

---

### Post by cariboo on 2012-09-28
@SheamusPatt, it may help, if you let us know which packages are being held back.

---

### Post by SheamusPatt on 2012-09-28
Does this help?

 [FONT=Courier New]**sudo apt-get -s dist-upgrade**[/FONT]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  ubuntuone-control-panel-qt
The following NEW packages will be installed:
  libopus0 libpackagekit-glib2-14 libufe-xidgetter0 libvigraimpex4
  linux-headers-3.5.0-16 linux-headers-3.5.0-16-generic
  linux-image-3.5.0-16-generic linux-image-extra-3.5.0-16-generic
  python3-gi-cairo python3-virtkey ubuntu-settings unity-lens-gwibber
  unity-lens-shopping unity-webapps-common xul-ext-unity
  xul-ext-websites-integration
The following packages will be upgraded:
  compiz compiz-core compiz-gnome compiz-plugins-default
  gstreamer0.10-plugins-bad gwibber gwibber-service libcompizconfig0
  libdecoration0 libgstreamer-plugins-bad0.10-0 libnux-3.0-0 libnux-3.0-common
  libunity-core-6.0-5 libunity-webapps0 libvigraimpex-dev
  linux-headers-generic linux-image-generic onboard
  python-ubuntuone-control-panel ubuntu-desktop ubuntuone-control-panel unity
  unity-common unity-services unity-webapps-service
25 upgraded, 16 newly installed, 1 to remove and 0 not upgraded.

(this is after running apt-get update && apt-get upgrade)

---

### Post by SheamusPatt on 2012-09-28
It helped me, at least. I upgraded the 'ubuntuone-control-panel-qt' package in Synaptic, since it seemed to be an issue. Synaptic complained (after it started upgrading), but went ahead, and once it was done, software-manager could update without any 'partial upgrade' warnings.

 Looks like ubuntuone-installer was the one with missing dependencies, if I recall correctly. Sorry, I meant to grab some of the log but lost it. Synaptic currently indicates that 'ubuntuone-control-panel-qt **Breaks** ubuntuone-installer'

Thanks.

---

### Post by SheamusPatt on 2012-10-12
Once again, I have been stymied for days because update-manager offered only a "Partial Upgrade". This time, it seems it's the lowly "lo-menubar" holding things up. When I ran :apt-get dist-upgrade" I see:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  lo-menubar
The following packages will be upgraded:
  libreoffice libreoffice-base libreoffice-base-core libreoffice-calc
  libreoffice-core libreoffice-draw libreoffice-gnome libreoffice-gtk
  libreoffice-impress libreoffice-math libreoffice-writer python-uno
12 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 64.4 MB of archives.
After this operation, 2,048 B of additional disk space will be used.

Should I just give up on update-manager during beta cycles? It seems to detect partial-upgrades more often than not, in my experience. I'm  happy losing lo-menubar in this particular case.

---

### Post by dino99 on 2012-10-12
there is no partial upgrade there, go ahead and drop lo-menubar, its no more required now.

---

### Post by grahammechanical on 2012-10-12
I find that partial upgrade messages come and go. I have only once accepted a partial upgrade and that broke the OS.

I just click cancel and continue with a normal update.

[https://wiki.ubuntu.com/U%2B1/partial_upgrade]("https://wiki.ubuntu.com/U%2B1/partial_upgrade")

> Most Partial Upgrade situations occur due to package archive inconsistencies, which will typically be resolved within a few hours. If your package manager is confused, and so are you, simply wait and hold off the updates until things settle down.

This is something we get used to when testing the Ubuntu development branch. Anyone who installs a release before it is officially released becomes a tester.

Regards.

P.S. Because Update Manager itself has been the subject of development during this cycle I have taken to doing updates through the Synaptic Package Manager. It is not installed by the default. It is in the software centre.

Other uses of the development branch use the terminal.

---

### Post by zika on 2012-10-12
> **SheamusPatt said:**
> It helped me, at least. I upgraded the 'ubuntuone-control-panel-qt' package in Synaptic, since it seemed to be an issue. Synaptic complained (after it started upgrading), but went ahead, and once it was done, software-manager could update without any 'partial upgrade' warnings.

 Looks like ubuntuone-installer was the one with missing dependencies, if I recall correctly. Sorry, I meant to grab some of the log but lost it. Synaptic currently indicates that 'ubuntuone-control-panel-qt **Breaks** ubuntuone-installer'

Thanks.The only thing left is to mark ubuntuone-control-panel-qt as „Automatically installed“ to be totally „legal“...
It is not ubuntuone-control-panel-qt that is important, I'm just making a remark so that a case when You „touch“ a package with apt-get or similar, manually, even though it is not even reinstalled or upgraded, it is marked as „manually installed“ and that could cause mental bookkeeping error later in the process of upadate/upgrade...

---

### Post by SheamusPatt on 2012-10-13
I certainly do appreciate the risks outlined on the wiki about partial updates, so have where possible avoided them. However, the advise that they will usually resolve themselves "within a few hours" is not what I've experienced; it's often days, if they resolve at all. (As noted a few posts back, when Beta 2 came out I was still getting "Partial Update" warnings, so that seemed to be a case where it would not resolve.

The Software Manager seems to be a bit flawed in this regard. It appears that if a package is dropped, then Software Manager will consider it perpetually out of date and give a "partial update" warning until the package is actually removed (and Software Manager will only do so if  you instruct it to update anyway). Do I have that right? If so, the package management system needs some more explicit way of indicating obsolete packages, so Software Manager can deal with them without unnecessarily warning the user about dire things that might happen (as in the case of lo-menubar I just noted).

I guess if I want to be a beta tester, I'll just have to do it "old school" with apt-get or perhaps Synaptic, so that I can at least know what I'm destroying. Software Manager just doesn't provide enough feedback to allow an intelligent decision to be made here.

---

### Post by bra|10n on 2012-10-13
> **SheamusPatt said:**
> ...The Software Manager seems to be a bit flawed in this regard...

If I'm not mistaken the wiki also points out the recommended method to apply updates is from the CLI.

---

### Post by jerrylamos on 2012-10-13
Updates can be problematic in any case especially during development cycles with unstable code.  "Update Manager" over the years has screwed me royally.  On on an install I do system settings > software sources
turn on partner
turn off daily update

Then on maybe daily basis during development,

First I check Ubuntu Forums+1 to see if anyone's reporting trouble.

Second I do in terminal Command Line Interface CLI:

sudo apt-get update
screen floods with pages of stuff
sudo apt-get dist-upgrade
screen floods with pages of stuff
It will ask for Y/n
If it wants to remove something important like the desktop, 
Ctrl-C
out of there.

If as usual wants to update a bunch of stuff I answer y.

After it's done, I do 
df
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove
df

Now if there's a new kernel, i.e. 
ls /boot
....  vmlinuz-3.5.0-17-generic ....
cat /proc/version
will show what is booted.  If it is -16 for example, reboot
then check version
then look at /boot
if there are old versions, and the new one is running O.K., then do
sudo apt-get remove linux-image-3.5.0-16-generic
then
sudo apt-get remove linux-headers-3.5.0-16-generic
then do the clean, autoclean, autoremove.

I use some exec's to help out on all this.

In development I'll do a fresh installs at A1, A2, A3, B1, B2, RC, release good for finding lots of bugs to report to launcpad.

Never update from last release to the next one unless you're looking for a high likely of disaster see the forums....

---

