---
title: "cant update virtualbox to 3.1"
date: 2009-12-04
forum: Virtualisation
---

### Post by mmoalem on 2009-12-04
hi there all i have virtualbox 3.012 and wanted to update to 3.1 but gdebi report:
Error: Conflicts with the installed package 'virtualbox-3.0'
what is going on? any ideas?
BTW i'm running Karmic which was an upgrade rather than a fresh install.

---

### Post by davidmerrick on 2009-12-05
I'm having the same problem.

---

### Post by fouadatmeh on 2009-12-05
Hello,

Faced the same problem, so I took the easy way and removed 3.0.12 from synaptec package manager and installed the new version. it only requested to install "libqt4-opengl" first...
It is working now and didn't even lose the VMs I had.
** Using Karmic 64 bit, and just upgraded to kernel 2.6.31-16

---

### Post by Perryg on 2009-12-05
The version 3.1.0 was a major release and as such you should uninstall the current version before you install the new one.  Usually a simple upgrade would be enough but they changed a lot of things and could not retain the same structure.  Snapshots were changed to allow branching, as well as their new teleportation (live migration) feature.

---

### Post by area124 on 2010-01-05
This work for me as well! On the un-install I did NOT do a "Complete" removal, just the default removal. Thanks much!!!

---

### Post by BobJam on 2010-01-09
I'm getting the same notice.

I don't necessarily want to install the new version because of the changes, but I'm sure there will be other updates and if I don't have it I won't be able to do them.

So, sooner or later I'm going to have to do the uninstall/reinstall routine.

The reason I'm hesitating right now is because I don't want to lose the VM config I have right now and have to start all over again.  I need to do this cautiously.

Now area124 said that he/she didn't do a "complete" removal, just the default.  And that is **exactly** what I need to do I think.

But I'm a relative Ubuntu noob.  As I recall, there is a Synaptic GUI way to do this, and also a CLI way.

So can anybody tell me more about either way?  I know I have to do this, but I want to completely understand what I'm doing before I start blindly removing stuff.

---

### Post by Perryg on 2010-01-10
Using the Synaptic Package Manager you have two choices.  remove and complete remove.  Select the remove and you should be fine.  As always though I suggest a backup first.  ~/.virtualbox has all of the files you should need to recover if it goes south.

---

### Post by BobJam on 2010-01-10
> **Perryg said:**
> Using the Synaptic Package Manager you have two choices.  remove and complete remove.  Select the remove and you should be fine.  As always though I suggest a backup first.  ~/.virtualbox has all of the files you should need to recover if it goes south.Kewl . . . all worked just fine.

Thanks very much!

---

### Post by jocampo on 2010-01-10
I faced a similar problem, was using 2.6. I removed  and installed 3.1 but then I was having weird errors when creating hard disks (my server is headless, so I create VMs via command prompt) My only choice was downgrade again to 3.0

3.1 is a major release. I suggest to wait a bit if you want to move from 2.x version unless you really want to migrate to most recent virtual box edition.

As rule, I always backup my VMs ... just in case  ...so I suggest the same to anyone.

---

### Post by tomsa on 2010-01-11
This may seem like a noob-ish question but, is there any difference between ~/.virtualbox  and exporting my machine to a pair of .ovf and .vmdk files?  Just wondering.

---

### Post by Perryg on 2010-01-11
Exporting is a good way to move VMs to another machine, but do yourself a BIG favor and write down the guest settings.  Some of them are not saved and you may need to know them.  Also snapshots are not included as snapshots.  They are all merged into one flat file. I really like the old fashioned way of copying the files to a different place and it is usually a lot faster, plus you should be backing up regularly anyway, right  ;)

Oh and VMDK files run slower then VDI files in VBox (IMHO)

---

### Post by Hey Gary on 2010-01-21
I just successfully completed this upgrade.  Here are the details of what I did to migrate from Virtualbox 3.0 to 3.1_56127.

Following prior advice I did the following (trying to be extra safe):
1- back up the data from my Guest systems.
2- exit and shut down all Guest (virtual) systems.
3- collapsed and deleted all snapshots (for all guests) so I had one current config (current state) and then did "Export Appliance".
4- closed the application and change $HOME/.VirtualBox to $HOME/.VirtualBox-upgrade

Now I deleted the current 3.0 Installation:
1- Start System -> Administration -> Synaptic Package Manager
2- Did a search for virtualbox (just easier than scrolling); click the search button, enter virtualbox in the popup, and click Search.
3- You should see (or find) the virtualbox-3.0 package name with a green box next to it.  Right click that package and select "Mark for Removal"  THIS IS IMPORTANT, if you select "Mark for Complete Removal" your data may be lost also DO NOT SELECT Complete Removal.
4- Click Apply and wait for the removal to finish.

That should cleanly remove the current install.

Now install the updated version 3.1.
NOTE that I first installed virtualbox-3.1 from the Synaptic Package Manager, but I did not get a cute icon on my Applications -> System Tools menu.  So I downloaded the appropriate (.deb) package from virtualbox.org and right clicked it to select "Open with GDebi Package Installer".

The downloaded package said I was current, but offered an option to "Reinstall Package", I told it to reinstall the package.

When it was done, I did have the icon.  I also found the software at "/usr/bin/Virtualbox".

I then changed $HOME/.VirtualBox-upgrade back to $HOME/.VirtualBox and started the application.

All my virtual machines were recognized and I started them without problem or issue.  The migration was done and I did not have to rebuild, recover, or import the appliance.  But, regardless, you should always have current and valid backups.  ;-)

---

### Post by motorcity909 on 2010-03-28
Thanks Hey Gary.

Followed your list and 3.1.6 installed with no problems, no loss of my virtual machines and Ubuntu 10.04 installed fine (couldn't get it to install in the old Vbox).

Cheers
Dave

---

### Post by Saturn300 on 2010-06-29
Thanks, it worked for me

---

