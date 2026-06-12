---
title: "Does Virtualbox 5.0 Need Guest Additions?"
date: 2015-09-18
forum: Virtualisation
---

### Post by Adler on 2015-09-18
Hi All,

I've been Googling about this issue, and thought I'd post here for possible solutions.

I'm running 14.04, 64-bit, and on a fresh install, wanted to install Virtualbox 5.0. Normally, I could install ***Guest Additions*** from the VB menu. However, this is not an option. I've tried this in Terminal, but it keeps reverting me back to an older version of VB. I can add ***Extensions*** via the VB site download. 

Question: Is the old ***VB Guest Additions ISO*** needed with version 5.0? Any help would be greatly appreciated.

Adler
*Down On The Jersey Shore*

---

### Post by slickymaster on 2015-09-18
> **Adler said:**
> Hi All,

I've been Googling about this issue, and thought I'd post here for possible solutions.

I'm running 14.04, 64-bit, and on a fresh install, wanted to install Virtualbox 5.0. Normally, I could install ***Guest Additions*** from the VB menu. However, this is not an option. I've tried this in Terminal, but it keeps reverting me back to an older version of VB. I can add ***Extensions*** via the VB site download. 

Question: Is the old ***VB Guest Additions ISO*** needed with version 5.0? Any help would be greatly appreciated.

Adler
*Down On The Jersey Shore*
I'd say yes, they're needed. VB Guest Additions still consist of device drivers and system applications that optimize the guest operating system for better performance and usability.

---

### Post by Adler on 2015-09-18
slickymaster,

Thanks for your response. I am aware of the past need for the *virtualbox-guest-additions*, but in Terminal when I does this:

[I]sudo apt-get install virtualbox-guest-additions.iso
[/I]
my VB 5.0 gets removed, and I get thrown back to VB 4.3, but with the *guest-additions*.

Any corrective help in getting VB 5.0 running with the *virtualbox-guest-additions.iso*? Thanks in advance for any assistance.

Adler
*Down On The Jersey Shore*

---

### Post by CharlesA on 2015-09-18
They should already be installed if you installed 14.04 as a guest.

Not too sure where you got the command:
sudo apt-get install virtualbox-guest-additions.iso

That shouldn't even be a valid package name, but it could flag the older version of virtualbox for installation, which would remove the current version.

---

### Post by coffeecat on 2015-09-18
> **Adler said:**
> my VB 5.0 gets removed, and I get thrown back to VB 4.3, but with the *guest-additions*.

That's probably because you downloaded the 5.0 version as a deb from the virtualbox site - [https://www.virtualbox.org/](https://www.virtualbox.org/) - rather than install the 4.3 version from the repositories. By trying to install the repo virtualbox-guest-additions.iso package, it needs to downgrade you to 4.3. If you add the virtualbox.org repository to your sources.list as described here:

[https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

That should solve that problem. However, last time I used Virtualbox in Ubuntu as host, the guest additions ISO was copied somewhere in the Virtualbox installed files.

---

### Post by slickymaster on 2015-09-18
> **CharlesA said:**
> They should already be installed if you installed 14.04 as a guest.

Not too sure where you got the command:
sudo apt-get install virtualbox-guest-additions.iso

That shouldn't even be a valid package name, but it could flag the older version of virtualbox for installation, which would remove the current version.

+1

All I do is```
sudo apt-get install virtualbox-guest-dkms virtualbox-guest-utils virtualbox-guest-x11 
```before installing the Guest Additions.

---

### Post by Adler on 2015-09-18
slickymaster,

I am following your lead here. I've purged vitualbox*, removed any repos concerning VB. Then installed it via Terminal, and have 5.0 going, but trying to add *virtualbox-quest-x!! *gives me this:

> The following packages have unmet dependencies:
 virtualbox-guest-x11 : Depends: xorg-video-abi-15
                        Depends: xserver-xorg-core (>= 2:1.14.99.902)
E: Unable to correct problems, you have held broken packages.


I've been using VB for along while, but never ran into this issue. I guess I could add ***"-f"*** after *sudo apt-get install virtualbox-guest-dkms virtualbox-guest-utils virtualbox-guest-x11, *but don't think that advisable.

Thanks - again - for your reply.

Adler
*Down On The Jersey Shore*

---

### Post by QIII on 2015-09-18
Hold on here.  Maybe I missed it, but you are installing VBoxGuestAdditions in the *guest*, right?

That shouldn't affect the host.

---

### Post by Adler on 2015-09-18
QIII,

I am trying to install *guest-additions* in VB 5.0. Then install a* guest* OS e.g. Win 10, Backbox Linux, etc.

Adler
*Down On The Jersey Shore*

---

### Post by slickymaster on 2015-09-18
Did you tried to install the **virtualbox-guest-dkms**, **virtualbox-guest-utils** and **virtualbox-guest-x11 **(clicking on "Devices" and chose "Install Guest Additions" before installing the Guest Additions)?
I'm asking because you have to first do the later and then the former.

You could try this approach [here]("http://askubuntu.com/questions/526995/installing-guest-additions-causing-problems/527077#527077").

Also, you might also be facing [Bug #1424769]("https://bugs.launchpad.net/ubuntu/+source/virtualbox/+bug/1424769")

---

### Post by QIII on 2015-09-18
Why not install the guest, insert the ISO from the mini menu and run the script or .run from the ISO image while in the guest OS?

---

### Post by slickymaster on 2015-09-18
> **QIII said:**
> Why not install the guest, insert the ISO from the mini menu and run the script or .run from the ISO image while in the guest OS?

Exactly. And just after that do what I proposed [here]("http://ubuntuforums.org/showthread.php?t=2295377&p=13358268&viewfull=1#post13358268").

---

### Post by Adler on 2015-09-18
Slickymaster,

All the VB installs worked, and are the latest versions, except for *virtualbox-guest-x11. *That is where I've run into XServer issues. From long hard experience when I've played here, I have always done a backup. LOL!

I'll check out the link you posted, and the guy might be onto something - solution-wise - and, I hope I've not run into a bug, as you mentioned.

THX for your help!

Adler
*Down On The Jersey Shore*

---

### Post by ajgreeny on 2015-09-18
I updated to VBox 5.0.4 from the virtualbox repository using synaptic.  All details of that are at [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads),  scroll down for the section on Debian-based Linux distributions.

That updated my VBox from 4.3.30 without a problem and when I started 5.0.4 the first time it told me I had an old version of the guest additions and offered to update that.

If that is not happening for you just get the guest additions package direct from VBox [http://download.virtualbox.org/virtualbox/5.0.4/Oracle_VM_VirtualBox_Extension_Pack-5.0.4-102546.vbox-extpack](http://download.virtualbox.org/virtualbox/5.0.4/Oracle_VM_VirtualBox_Extension_Pack-5.0.4-102546.vbox-extpack) and double click it; it should then be opened by VBox and installed in it without a problem.

Now when you start the guest you will need to insert the guest additions from the mini-menu Devices at the bottom and then run the VBoxLinuxAdditions.run file in the inserted .iso which in my case in my Ubuntu 14.04 guest is at /media/*user*/VBOXADDITIONS_5.0.4_102546

---

### Post by monkeybrain20122 on 2015-09-18
I had VB 4.3. Then I installed 5.0 from synaptic and 4.3 was removed. Then I started VB, a popup told me the guest-addition (for VB 4.3) was outdated and offered to upgrade it, I accepted that ga was upgraded to 5. That was it.

Edited: just saw ajgreeny's post. should have just said +1 had I seen it.

---

### Post by QIII on 2015-09-18
This is all true on an *existing* VM.  On a new VM, the ISO has to be inserted and the guest additions installed.

You can find the ISO and add it to the storage devices during the machine setup, but the guest additions still need to be installed on the guest.

---

### Post by Adler on 2015-09-18
Hi All,

Thanks for all the posted replies. I'll keep on working on this a time allows. Meanwhile, a picture is worth a thousand words:

[ATTACH=CONFIG]264518[/ATTACH]

In the past I could click the Device Tab, and do the install. This time around not so.

Thanks again to all!

Adler
*Down On The Jersey Shore*

---

### Post by slickymaster on 2015-09-18
I can be misunderstanding you, Adler, but the device tab is only available in the guest OS, and your picture is just showing the VB GUI in the host with no guest installed.

---

### Post by flocculant on 2015-09-18
Pictures being worth a 100 words - this is what QIII is pointing to (also the way I use guest additions) from a running guest.

[ATTACH=CONFIG]264521[/ATTACH]

---

### Post by Adler on 2015-09-18
flocculant,

It appears my* menu* is missin' a few things versus yours. LOL! 

[ATTACH=CONFIG]264522[/ATTACH]

What has been normally a pretty easy install has turned into a mystery. In the past, the only issues that I've run into with VB has been with Kernel Up-Dates. 

Thanks for pointing out the obvious issue in pictures!

Adler
*On The Jersey Shore*

---

### Post by CharlesA on 2015-09-18
You do not have any guest VMs set up.

---

### Post by Adler on 2015-09-18
> You do not have any guest VMs set up. 		

CharlesA,

You seem to have found the solution, which is much to my embarrassment. I did do a guest OS install, and the menu, that I did need appeared!

[ATTACH=CONFIG]264523[/ATTACH]

Now I just need to find the matching *Guest-Addition-ISO* from this [blog]("https://blogs.oracle.com/joshis/entry/virtualbox_guest_additions_iso_download"), and the appropriate version. 

Thanks for your post!

Adler
*Down On The Jersey Shore*

---

### Post by ajgreeny on 2015-09-18
I already gave you the link for downloading the guest additions in my post #14.
[http://download.virtualbox.org/virtualbox/5.0.4/Oracle_VM_VirtualBox_Extension_Pack-5.0.4-102546.vbox-extpack](http://download.virtualbox.org/virtualbox/5.0.4/Oracle_VM_VirtualBox_Extension_Pack-5.0.4-102546.vbox-extpack)

Save it to disk then double click it to open and install it in VBox.  You will then have to insert it into your guest OS from the Devices menu, and finally run the VBoxLinuxAdditions.run file from the installed iso that you will find in /media/*user*

You need to execute that. run file as root in Ubuntu with sudo but I don't know how backbox does that.

---

### Post by Adler on 2015-09-19
ajgreeny,

I hear what you are saying, but when I scrap the Backbox Linux Machine, which gave me the File Machine View Input, etc. menu, and install M$ 10, that menu disappears.

[ATTACH=CONFIG]264524[/ATTACH]

I'll be deleting / purging Virtualbox 5.0, and starting over. I do like the new 5.0 - just got to get it installed. LOL!

Thank you for the input, and help!

Adler
*Down On The Jersey Shore*

---

### Post by QIII on 2015-09-19
Please, everyone.

Don't paste large images in your posts.  There are Forums users who have low bandwidth connections and data transfer limitations.  Besides making opening a page very slow for them, you may actually cost them money.

Please use the attachment functionality (the paper clip above the text entry box) to add images.  Let other users decide if they want to enlarge the images or not.

Thanks.

---

### Post by Adler on 2015-09-19
QIII,

Message received.

Adler
*Down On The Jersey Shore*

---

### Post by ajgreeny on 2015-09-19
OK, here's what I think you must do to get VBox 5.0.4 working properly.

If you have currently removed VBox from your machine, install it again from the repos, assuming, of course, that you have the VBox repos enabled as I have.  Do not try to install the guest additions from the repos as they are not available that way for the 5.0.4 version.
Now get hold of the guest additions if you don't already have the package from Oracle VBox website, but if it is already on your disk somewhere just double click on it and it will be installed in VBox.

When you now make a new virtual machine from an .iso of the distro of your choice you will need to boot to it, then insert the guest additions from the devices menu, and  finally as root run the /media/*user*/VBOXADDITIONS_5.0.4_102546/VBoxLinuxAdditions.run.

That should be done until you next upgrade the VBox version, at which point you will get an error about guest additions being out of date and offering to update it.  Accept that and after the update you will have to re-run the new VBoxLinuxAdditions.run file.

---

### Post by JKyleOKC on 2015-09-19
> **Adler said:**
> QIII,
I am trying to install *guest-additions* in VB 5.0. Then install a* guest* OS e.g. Win 10, Backbox Linux, etc.

Sorry, that's not the way it works. After installing vbox 5.0, use its internal menu's "Extensions" choice to locate and install the extensions package (which you might need to download separately). Once you have done that, create one or more new VMs and install their guest systems. Finally, run the VM and after the guest system boots, pull down the "Devices" item from the VBox menu bar and select "Install Guest Additions" which should be the bottom entry of the drop-down submenu.

What you do next depends on the guest system. If it's Windows, the Guest Additions wizard will open automagically and you then follow its instructions. If it's Linux, you'll have to mount and open the cdrom (which will now contain the Guest Additions ISO file), then launch the appropriate executable program from those displayed.

This has been the routine as far back as I've been using vbox, which goes back to the days of Version 2.

Because the standard for all Ubuntu packages is NOT to update add-on utilities between major versions of *buntu, you won't find vbox 5.0 in the normal repositories for 14.04 Trusty. You need to add the PPA that Oracle provides in order to use apt-get for it. Full instructions can be found at [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads) if you're interested.

---

### Post by Adler on 2015-09-20
JKyleOKC / ajgreeny,

Thanks for your posts. I do have the ***guest additions*** ***iso*** installed, but via the guest OS (Win 10 Enterprise). With Win 10 I have enabled a USB Device, and have video capture enabled. There are a few remaining issues (adding shared folders / Vbox Kernel Service not running on boot), but all seems good.

I've been jotting down what I've done, and once complete will post it here for others to follow. It seems there have been many issues with Trusty 14.04, working with the repos, Oracle's VB downloads, plus the shift from VB 4.3 to 5.0. There is a lot in the mix here!

It is all good clean fun! And, no one has been hurt so far. LOL!

Adler
Down On The Jersey Shore.

---

### Post by JKyleOKC on 2015-09-20
> **Adler said:**
> Vbox Kernel Service not running on boot.

Do you have the build-essentials and DKMS packages, plus the linux header package, installed on your host system? These are needed in order to create the necessary kernel modules each time a kernel update occurs. "DKMS" originally stood for Dell Kernel Maintenance System if I recall its history correctly, but it now applies to all kinds of machines, not just those from Dell, and is needed to update several kinds of proprietary drivers and the driver modules for vbox. The build-essentials package provides the C compiler and associated utilities to enable compilation of new drivers.

---

### Post by Adler on 2015-09-21
JKyleOK,

All is well, and good here. Just to re-cap I am running UBUNTU 14.04 (Trusty) 64-Bit. Originally my difficulty was getting the *virtualbox-guest-additions *going with the new release of VB i.e. 5.0+.

Normally, I just did the whole VB install in Terminal - VB, Additions, and Externsion Pack. The problem I ran into was really understanding - I think - the changes with the latest VB.

So, I did this:

```
dpkg -l | grep virtualbox
sudo apt-get remove virtualbox --purge
sudo apt-get clean
dpkg -l | grep virtualbox 
```

Just to make sure that I had no repos lurking around I checked this:

```
gksudo gedit /etc/apt/sources.list
```

I did remove a VB repo. And, saved the file.

Moving along, I got the latest .deb version of VB from the Oracle Site [here]("https://www.virtualbox.org/wiki/Linux_Downloads"). I did not use the repo. I did the install with GDebi, and not the UBUNTU S/W Center. 

To get the virtualbox-guest additions: [http://download.virtualbox.org/virtualbox/5.0.4/](http://download.virtualbox.org/virtualbox/5.0.4/)

I installed a guest OS (M$ Win 10)

```
sudo apt-get install dkms gcc 
cd /home/adler/Downloads
sudo mount -o loop VBoxGuestAdditions_5.0.4.iso /mnt
cd /mnt
sudo ./VboxLinuxAdditions.run
```

That gave me an error, but at the same time I noticed that the Additions CD had been mounted in Win 10. So, I just did the install using M$. The guest-additions had been mounted, and I just did the install there.

Back @ [https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads), I downloaded **VirtualBox 5.0.4 Oracle VM VirtualBox Extension Pack. ****That is [http://download.virtualbox.org/virtualbox/5.0.4/Oracle_VM_VirtualBox_Extension_Pack-5.0.4.vbox-extpack](http://download.virtualbox.org/virtualbox/5.0.4/Oracle_VM_VirtualBox_Extension_Pack-5.0.4.vbox-extpack), not [http://download.virtualbox.org/virtualbox/5.0.4/Oracle_VM_VirtualBox_Extension_Pack-5.0.4-102546.vbox-extpack](http://download.virtualbox.org/virtualbox/5.0.4/Oracle_VM_VirtualBox_Extension_Pack-5.0.4-102546.vbox-extpack)**

**In Terminal I did the install:**

```
cd/ home/adler/Downloads
```, then```
sudo VBoxManage extpack install Oracle_VM_VirtualBox_Extension_Pack-5.0.4-102546.vbox-extpack
```
Finally, I did a```
dpkg -l | grep virtualbox
```
But, in Terminal neither the *guest-additions*, or *extension pack* show:
```
ii  virtualbox-5.0                                        5.0.4-102546~Ubuntu~trusty                          amd64        Oracle VM VirtualBox

```
They do; however, show up in my Guest OS (Win 10). I think this has been the point that confused me.

So, unless otherwise contradicted, I think that I am good to go. It all works for me here.

Thanks to all for jumping in here.

Adler
*Down On The Jersey Shore*

---

### Post by slickymaster on 2015-09-21
I'm glad you got it solved Adler.

I've edit your last post to correct the font size and to replace all quote tags for code tags. In the future please use the default font color and properties unless you need to highlight or draw attention to a part of your post. Funky non-uniform font size/color is difficult for those who are visually impaired and always use code tags, not quote tags, because output posted as plain text loses its formatting and parts of it sometimes turn into smileys making it difficult to read and understand. The [use of code tags]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") makes the post clean, compact and more appealing, thus getting more attention from readers.

Finally can you please [mark the thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") so other people searching the forums know that it provides a working solution.

---

### Post by Adler on 2015-09-21
slickymaster,

I do apologise for the housekeeping that you had to do in cleaning up my posts.

I will mark the thread as solved, and I do hope it helps others in getting Virtualbox 5.0+ going. 

Adler
*On The Jersey Shore*

---

### Post by slickymaster on 2015-09-21
> **Adler said:**
> slickymaster,

I do apologise for the housekeeping that you had to do in cleaning up my posts.

I will mark the thread as solved, and I do hope it helps others in getting Virtualbox 5.0+ going. 

Adler
*On The Jersey Shore*

Sure, no problem.

---

### Post by JKyleOKC on 2015-09-21
> **Adler said:**
> 
So, unless otherwise contradicted, I think that I am good to go. It all works for me here.

Just one minor point. You'll have fewer problems down the way if you go to the link I posted and follow its directions for adding the Oracle repository to your updating settings. (The directions are headed as being for Debian but they also apply to all Debian derivatives.) Once you do this, your automatic updating schedule will also notify you of updates to the vbox software, and they should show up when you check in the terminal of the host system but possibly not until after the first actual update.

I've found it best to NOT install vbox updates immediately, but rather to wait a few weeks and monitor the forums both here and at Oracle to be sure no serious bugs made their way into the system. I've also learned to make sure that all VMs are "powered down" rather than "saved" when doing updates to vbox. As often as not, the update turns out to not be compatible with "saved" VMs. I've always recovered by "discarding" the saved snapshot, but it's safer and simpler not to risk the problem in the first place.

Thus my "production" vbox system on this machine is still at version 4, while my "test" system on another machine is happily running version 5. Being a bit lazy these days, I just haven't taken the trouble to do the update here yet.

---

### Post by Adler on 2015-09-21
JKyleOKC,

Thanks for those words of advice!

Adler
*Down On The Jersey Shore*

---

