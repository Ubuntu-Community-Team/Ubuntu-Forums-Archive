---
title: "Virtualbox guest can't see shared folders"
date: 2017-07-13
forum: Virtualisation
---

### Post by John Jason Jordan on 2017-07-13
The host is Xubuntu 14.04 (up to date). The guest is Xubuntu 16.04. Guest additions are installed on both machines. My username is jjj (both machines) and I need to share ~/jjj on the host to the guest OS. On the guest the share appears under Devices > Shared folders, but I can't see the files on the host from the guest. I should add that under Devices > USB Devices on the guest I can see flash drives on the host and mount them on the guest. From what I have read this seems to be proof that Guest additions are installed. I should also add that the host has two Windows virtual machines, and ~/jjj on the host appears and can be accessed in both of them. It's just the 16.04 guest that can't see the share.

I've spent hours reading instructions here and from Oracle and elsewhere, and so far no luck. I need more clues!

---

### Post by slickymaster on 2017-07-13
*Thread moved to **Virtualisation**.*

---

### Post by efflandt on 2017-07-13
A user needs to be in **vboxusers** group in order to see or work with vbox shared files. The reason that may have not been apparent with Windows virtual machine is that Windows does not have *nix like user/group permissions, so maybe there is a (less secure) workaround to get around that in Windows.

---

### Post by &amp;KyT$0P# on 2017-07-13
efflandt's post applies to the host machine.  Additionally, inside the guest you need to be in the [FONT=Courier New]vboxsf[/FONT] group.

(Log out and back in for changes to groups to take effect.)

---

### Post by John Jason Jordan on 2017-07-13
> **halogen2 said:**
> efflandt's post applies to the host machine.  Additionally, inside the guest you need to be in the [FONT=Courier New]vboxsf[/FONT] group.
(Log out and back in for changes to groups to take effect.)

Thanks for the suggestion. Indeed, on the guest I was in vboxusers group, but not in the vboxsf group. I added myself to the vboxsf group, then on the host I verified that I was in the vboxusers group. Then I shut down and restarted the guest, but I still can't see the host share from the guest. 

Need more clues. :(

---

### Post by ajgreeny on 2017-07-13
I wonder if being in the vboxusers group in the guest is causing some conflict; there is no reason to add yourself to that group in the guest.
My guest Xubuntu 17.04 and Ubuntu-Gnome 17.04 both show me as being in groups:-
*username* adm cdrom sudo dip plugdev lpadmin sambashare vboxsf

I see no good reason why it should be a problem but that is the only difference that I can see between your setup and mine and sharing works fine for me.  Did you need to create the group vboxuserrs in the guest because it does not exist in my guests?
Do you have a shared clipboard setup as well in both directions, and if so, does it work for you?

---

### Post by John Jason Jordan on 2017-07-13
> **ajgreeny said:**
> I wonder if being in the vboxusers group in the guest is causing some conflict; there is no reason to add yourself to that group in the guest.
My guest Xubuntu 17.04 and Ubuntu-Gnome 17.04 both show me as being in groups:-
*username* adm cdrom sudo dip plugdev lpadmin sambashare vboxsf
I see no good reason why it should be a problem but that is the only difference that I can see between your setup and mine and sharing works fine for me.  Did you need to create the group vboxuserrs in the guest because it does not exist in my guests?
Do you have a shared clipboard setup as well in both directions, and if so, does it work for you?

I just removed myself from the vboxusers group, then shut down and restarted, but the share still does not appear. As for the vboxusers group on the guest, I don't think I created it, but I've been working on this for so long and I have tried so many things that I can't honestly be sure.

I just checked which groups I'm in on the guest: adm, cdrom, dip, lpadmin, plugdev, sambashare, sudo, vboxsf. That matches your list exactly.

Shared clipboard and drag and drop are both enabled bidirectionally, and neither works. That was a good question! There must be a connection; now all we have to do is figure out what it is!

---

### Post by John Jason Jordan on 2017-07-13
I have one more clue:

When I am in the Guest and I click on Devices > Shared Folders Settings I get an error message pop-up:

[IMG]https://app.box.com/s/bkmy3xfa9610osc85930avut1xlum3g5[/IMG]

OK, the screenshot isn't visible here. Oh well, here is what the error message says:

[INDENT]*The VirtualBox Guest Additions do not appear to be available on this virtual machine, and shared folders cannot be used without them. To use shared folders inside the virtual machine, please install the Guest Additions if they are not installed, or re-install them if they are not working correctly, by selecting Insert Guest Additions CD image from the Devices menu. If they are installed but the machine is not yet fully started then shared folders will be available once it is.*[/INDENT]

The strange thing is that if I click on the OK button the settings appear, showing the share.

---

### Post by &amp;KyT$0P# on 2017-07-13
How did you install Guest Additions?
What version of Guest Additions is installed?
What version of VirtualBox are you using and where did you get it?

---

### Post by John Jason Jordan on 2017-07-13
> **halogen2 said:**
> How did you install Guest Additions?
What version of Guest Additions is installed?
What version of VirtualBox are you using and where did you get it?

I installed the ISO from the default Xubuntu 16.04 repositories using Synaptic. It is version 5.0.40. Later, with the ISO mounted I followed the instructions here: [https://help.ubuntu.com/community/VirtualBox/GuestAdditions]("https://help.ubuntu.com/community/VirtualBox/GuestAdditions") . The installation went without error.

VirtualBox on the host (Xubuntu 14.04 is version 4.3.36. On the guest (Xubuntu 16.04) it is 5.0.40, the same as the guest additions on the guest.

Edit: I take it back! The installation did not go without error. Just now I repeated the installation, and there were lots of errors:

```
Verifying archive integrity... All good.
Uncompressing VirtualBox 4.3.36 Guest Additions for Linux............
VirtualBox Guest Additions installer
Removing installed version 4.3.36 of VirtualBox Guest Additions...
Copying additional installer modules ...
Installing additional modules ...
Removing existing VirtualBox DKMS kernel modules ...done.
Removing existing VirtualBox non-DKMS kernel modules ...done.
Building the VirtualBox Guest Additions kernel modules
The headers for the current running kernel were not found. If the following
module compilation fails then this could be the reason.

Building the main Guest Additions module ...fail!
(Look at /var/log/vboxadd-install.log to find out what went wrong)
Doing non-kernel setup of the Guest Additions ...done.
Installing the Window System drivers
Installing X.Org Server 1.18 modules ...done.
Setting up the Window System to use the Guest Additions ...done.
You may need to restart the the Window System (or just restart the guest system)
to enable the Guest Additions.
```

I looked at /var/log/vboxadd-install.log on the guest. It was also full of errors, none of which I understood. I would post it here but it is kind of long.

---

### Post by &amp;KyT$0P# on 2017-07-13
> **John Jason Jordan said:**
> On the guest (Xubuntu 16.04) it is 5.0.40, the same as the guest additions on the guest.
Wait, you have VirtualBox installed inside a VirtualBox VM?  Is this for the [XKCDE]("https://xkcd.com/1764/")? :D

Anyway,

1) Try using the Guest Additions 5.0.40 ISO to uninstall the 5.0.40 Guest Additions -
```
sudo ./VBoxLinuxAdditions.run uninstall
```

2) About Guest Additions 4.3.36 on Xubuntu 16.04, you might want to read [this]("https://ubuntuforums.org/showthread.php?t=2329454").

Or you could just uninstall the repository version of VirtualBox and replace it with the [latest version from Oracle]("https://www.virtualbox.org/wiki/Linux_Downloads").

---

### Post by John Jason Jordan on 2017-07-13
> **halogen2 said:**
> 
1) Try using the Guest Additions 5.0.40 ISO to uninstall the 5.0.40 Guest Additions -
```
sudo ./VBoxLinuxAdditions.run uninstall
```
2) About Guest Additions 4.3.36 on Xubuntu 16.04, you might want to read [this]("https://ubuntuforums.org/showthread.php?t=2329454").
Or you could just uninstall the repository version of VirtualBox and replace it with the [latest version from Oracle]("https://www.virtualbox.org/wiki/Linux_Downloads").

Xkcd ... LOL. :)

OK, I used the Guest Additions 5.0.40 ISO to uninstall the 5.0.40 Guest Addtions, then I searched on 'virtualbox' in Synaptic and uninstalled everything else. Then I took your last line of advice and installed 5.122 from Oracle, including the guest extensions. Then I shut down the guest OS and restarted it. Still can't see the share. And if I go to Devices > Shared folders settings I get the same error message pop-up.

---

### Post by ajgreeny on 2017-07-14
I believe you have been and maybe still are totally confused about what is needed to run VMs within VirtualBox.

On the host machine you need to install a supported version of VirtualBox and the easiest way in Ubuntu is to add the Oracle-VBox repository in the way shown at [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads) in the **Debian-based Linux distributions** section.  That will ensure you have the latest version. In the guest the only thing you might need to install from the repos is **dkms** to make sure the addition modules are built and installed properly; you do not need to install any virtualbox packages from the repos in the guest.

Personally, I then download the Extension Pack from [https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads) and once you have that package simply double click it and it will be run and installed in the existing version of VirtualBox.

Now start your guest VM of Xubuntu 16.04, go to the Devices menu and click on the **Insert Guest Additions CD Image**.  This should add the ISO of the guest additions to your guest, and it should now be seen as a Volume in the file manager left hand pane.  From here I open a terminal in the guest, run command ```
sudo -i
``` to get a root terminal and simply drag the VBoxLinuxAdditions.run file from the ISO into the terminal and hit Enter to install the additions.

From that point on whenever the VBox application in the host is updated to a new version you will get a message when you open it telling you a new version of the guest additions is also needed so follow the prompt and it will be installed automatically. Also when starting the guest you will get another message telling you the guest additions are outdated so you should rerun the updated VBoxLinuxAdditions.run file from the updated ISO.

I hope that helps you sort out this confusion, if that is what it was.

---

### Post by efflandt on 2017-07-14
Guest Additions need to be same version as virtualbox version on the host. For example when you install virtualbox on host, you also add Guest Additions package on host (which is a CD image for guests). To install those Guest Additions to guest, while **running the guest**, from **menus on host** select **Devices > Insert Guest Additions CD image...** and install Guest Additions on the guest from that virtual CD. That is easy if guest is Ubuntu because when you insert Guest Additions CD image from host, it will ask if you want to autorun it on the guest.

That is somewhat more difficult with a real Debian guest where Guest Additions virtual CD does not autorun and you have to manually run a specific file on that virtual CD from a root console or "su -" to switch to root.

So you you install vbox and Guest Additions packages on host, but then mount that Guest Additions with hosts's Devices menu and run the virtual CD on the guest.

---

### Post by John Jason Jordan on 2017-07-14
> **ajgreeny said:**
> I believe you have been and maybe still are totally confused about what is needed to run VMs within VirtualBox.

You are correct!

> **ajgreeny said:**
> On the host machine you need to install a supported version of VirtualBox and the easiest way in Ubuntu is to add the Oracle-VBox repository in the way shown at [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads) in the **Debian-based Linux distributions** section.  That will ensure you have the latest version. In the guest the only thing you might need to install from the repos is **dkms** to make sure the addition modules are built and installed properly; you do not need to install any virtualbox packages from the repos in the guest.
Personally, I then download the Extension Pack from [https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads) and once you have that package simply double click it and it will be run and installed in the existing version of VirtualBox.

Now start your guest VM of Xubuntu 16.04, go to the Devices menu and click on the **Insert Guest Additions CD Image**.  This should add the ISO of the guest additions to your guest, and it should now be seen as a Volume in the file manager left hand pane.  From here I open a terminal in the guest, run command ```
sudo -i
``` to get a root terminal and simply drag the VBoxLinuxAdditions.run file from the ISO into the terminal and hit Enter to install the additions.
From that point on whenever the VBox application in the host is updated to a new version you will get a message when you open it telling you a new version of the guest additions is also needed so follow the prompt and it will be installed automatically. Also when starting the guest you will get another message telling you the guest additions are outdated so you should rerun the updated VBoxLinuxAdditions.run file from the updated ISO.

I finally got it working!

This is the part that helped most: "you do not need to install any virtualbox packages from the repos in the guest." At various times I had installed all kinds of VirtualBox packages in the guest. I did so because of misunderstanding instructions from all over, including Ubuntu forums and wikis. The problem is that instructions will say something like "install <package>" without always being specific whether the package is to be installed in the guest or in the host. In all this time I never did anything to the host because it seemed to be working fine, at least with my two Windows machines. 

After reading the above I opened Synaptic on the host and uninstalled everything related to VirtualBox, and then restarted the guest. When it restarted I used the command line to run the script in the ISO, but again I got the error messages. However, this time I noticed that the errors related to dkms, so I used Synaptic to install virtualbox-guest-dkms in the guest (which required virtualbox-guest-utils). Having installed those two in the guest I re-ran the script, which finally ran without error. Et voilà! The shared folder finally appeared in the guest!

---

### Post by ajgreeny on 2017-07-14
Brilliant!

I am glad that you got it working at last.  Does the shared clipboard also now work as well as the shared folder?

PS:
I have never installed the **virtualbox-guest-dkms** package but just use **dkms** instead; that always works fine and I suspect the **virtualbox-guest-dkms** package you have from the repos is a different version to your 5.1.22 if that is the VBox version you are still using.

Also the only package you need to install in the host OS is the VirtualBox package itself, not the many other packages from the repos that you seem to have installed but which will probably be completely superfluous to your requirements.

---

### Post by John Jason Jordan on 2017-07-14
> **ajgreeny said:**
> Brilliant!
I am glad that you got it working at last.  Does the shared clipboard also now work as well as the shared folder?
PS:
I have never installed the **virtualbox-guest-dkms** package but just use **dkms** instead; that always works fine and I suspect the **virtualbox-guest-dkms** package you have from the repos is a different version to your 5.1.22 if that is the VBox version you are still using.
Also the only package you need to install in the host OS is the VirtualBox package itself, not the many other packages from the repos that you seem to have installed but which will probably be completely superfluous to your requirements.

Yes, right after I got the guest seeing the share I tried the shared clipboard feature and was pleased to see that it is now working as well. I conclude that shared folders and the shared clipboard must go together. Interestingly, under Devices there is also an option for drag and drop between the host and the guest, but that still doesn't work. It doesn't sound very useful anyway, so I don't care. Also, although USB devices were working from the beginning I read somewhere that you can use such a device on only one OS at a time, and that seems to be true.

As for the host (Xubuntu 14.04, up to date), during this entire process I never messed with it. It remains the VirtualBox from the 14.04 repos (4.3.36). When I briefly installed 5.1 from Oracle I did so on the guest, not on the host. Now, there is a slight problem with the VirtualBox from the repos on the host - every time the Ubuntu software updater gives me a new kernel VirtualBox fails to launch any of my guests. There is an error message with a command that supposedly will fix it, but when I run the command it always fails. Over time I discovered that I can solve the problem just by going into Synaptic and reinstalling VirtualBox. You would think that the software updater would do this for me, but oh well. 

As for the many other packages on the host from the repos, there are only four: virtualbox, virtualbox-qt, virtualbox-guest-additions.iso, and virtualbox-dkms. I'm not sure if any of them are superfluous, but leaving them alone seems to cause no harm. :)

Thanks for all your help and patience!

---

