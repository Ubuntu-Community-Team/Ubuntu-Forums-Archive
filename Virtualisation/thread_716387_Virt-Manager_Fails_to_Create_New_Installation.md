---
title: "Virt-Manager Fails to Create New Installation"
date: 2008-03-05
forum: Virtualisation
---

### Post by otta56 on 2008-03-05
Virt-manager returns the following message when attempting to create a new Windows XP install under Hardy Heron

Unable to complete install '<class 'libvirt.libvirtError'> virDomainCreateLinux() failed 
Traceback (most recent call last):
  File "/usr/share/virt-manager/virtManager/create.py", line 617, in do_install
    dom = guest.start_install(False, meter = meter)
  File "/usr/lib/python2.5/site-packages/virtinst/Guest.py", line 813, in start_install
    return self._do_install(consolecb, meter)
  File "/usr/lib/python2.5/site-packages/virtinst/Guest.py", line 834, in _do_install
    self.domain = self.conn.createLinux(install_xml, 0)
  File "/usr/lib/python2.5/site-packages/libvirt.py", line 585, in createLinux
    if ret is None:raise libvirtError('virDomainCreateLinux() failed', conn=self)
libvirtError: virDomainCreateLinux() failed 
'
Has anyone experienced this problem? Virt-manager is patched to March 5th (today)

Thx

A. Ott

---

### Post by zorglab on 2008-03-22
Same problem here using QEMU and KVM with hardy.
Anyone got an idea?

---

### Post by kaivalagi on 2008-03-23
Same problem here too

System fully updated at time of post

---

### Post by kaivalagi on 2008-03-23
Got it working!

It was a simple case of user group permissions, I added my user to the following groups:

kvm
libvirtd

You need to log out and log in for it to take affect.

Give it  a try and if solved for you please mark the thread as solved.

Cheers

---

### Post by wcorey on 2008-03-23
You added yourself to the pre-existing groups:

kvm and libvirtd?

I do not even show those groups. Did you create those two groups and add yourself to them?

---

### Post by pchap123456 on 2008-03-23
the tip provided by Kaivalagi works perfectly.

You can add yourself the the groups mentioned through System->Administration->Users and Groups. Logging out and logging in is indeed (!) required.

Thanks!

---

### Post by melser.anton on 2008-03-23
worked perfectly! I wanted to try kubuntu 8.04 and tried to install into a win2008 hyper-v. That didn't work, so I tried the other way round (upgraded my 7.10 to 8.04 beta). That didn't work either but now it's all good.
Thanks for the tip.
A

---

### Post by kaivalagi on 2008-03-23
> **wcorey said:**
> You added yourself to the pre-existing groups:

kvm and libvirtd?

I do not even show those groups. Did you create those two groups and add yourself to them?

wcorey, in 8.04 the groups are there once kvm and virt-manager are installed. They are disabled to start with in the 'users and groups' dialog, needing the user to 'unlock' editing, could this be why you have problems? This unlock feature is new to 8.04 I think...

To add yourself to the groups do the following:
1) Open Menu->System->Administration->Users and Groups
2) Click unlock and enter your password
3) Click manage groups
4) Find each group in turn and go to it's properties
5) Tick the box next to your username for that groups permissions and click okay
6) Logout and login

Hope that helps

---

### Post by pchap123456 on 2008-03-23
While i can now create a VM using an iso image, the VM creation wizard has apparently no access to the CD drive meaning that it cannot find my Windows install disk thus keeps asking me to put the CD in. Installing Linux with an iso file works fine though but the VM has no CD drive listed in its config either... Any tip to get around this?

thanks!
Phil

---

### Post by kaivalagi on 2008-03-23
No cdrom access, strange...

The root account by default has no access to the cdrom, at a guess you could try ticking the box against the "Use CD-ROM drives" privilege? Although I would expect that the permissions should come from your own user...which you'd expect to have the rights.

I haven't tried to reproduce your problem so I am only guessing here :)

Let us know the outcome...

---

### Post by pchap123456 on 2008-03-23
Thanks for the fast feedback. I had the necessary privs to use the CD drive and I gave the same to root. Same [lack of] result though...

Guess I will reinstall once Hardy Heron goes live...

Phil

---

### Post by wcorey on 2008-03-23
thanks for all the previous replies. i do not have groups for kvm or libvirtd. i do not see any kvm services running nor do i see any downloadable packages for either. i assumed that meant when they say it is part of the kernel it is not a separate package. yes, that was somewhat weak i suppose but where you all at least have the packages installed you presumably manually installed the packages. i do understand about unlock and user/group manager, those groups are not listed.  please advise. of course tonight the symantic package manager and add/remove packages have both decided to crash on invocation so i will have to wait before i quadruple check. any further thoughts would be appreciated1

---

### Post by pchap123456 on 2008-03-24
both virt-manager and kvm can be installed through System->Admin->Synaptic. Just do a search from Synaptic,  select the packages and apply the changes. This will create two corresponding groups available from the System->Admin->User and Groups menu. To assign your username to eacjh of the two groups, you will have first to press the "unlock" button. Then logout/login... (just repeating what I learned from Kaivalagi though).

phil

---

### Post by kaivalagi on 2008-03-24
> **wcorey said:**
> of course tonight the symantic package manager and add/remove packages have both decided to crash on invocation so i will have to wait before i quadruple check. any further thoughts would be appreciated1

You can bypass the synaptic GUI and get the packages installed via the console (Accessories->Terminal), just run the following commands, a line at a time. The first 2 will ensure what you have installed on your system is up-to-date, the third and fourth you should recognise, and the fifth is worth installing to provide further functionality if needed. 

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install kvm
sudo apt-get install virt-manager
sudo apt-get install qemu
```

I am sure there are more packages I may have installed for my kvm endeavours, but I am going off memory, as I'm in gutsy at the mo. virt-manager doesn't work in Gutsy :(...if you get prompted for anything with the above commands just answer yes.

Hope that helps

Mark

---

### Post by pchap123456 on 2008-03-27
Just FYI, I finally was able to access my CD drive thus complete the installation of Windows XP.

The trick is to launch virt-manager as root, i.e. gksu virt-manager. The program then allows you to set-up the network and, finally, access the CD drive...

For what this is worth...

Phil

---

### Post by kaivalagi on 2008-03-27
Thanks for the info Phil, at least there is a work around

However using the root account is not the answer...but at least we know it has something to do with permissions...

I would think looking at the permissions of /dev/dvd or /dev/cdrom would give you an idea...just a guess...

---

### Post by pchap123456 on 2008-04-01
Thanks for the hint.

 I did check and modified the permissions of /dev/cdrom, /dev/scd0 and /dev/cdrw to give full access to my account but sill the same alas, the CD/DVD option is grayed out in the VM creation wizard.

Never mind thanks for the assistance!

Phil

---

### Post by wcorey on 2008-04-06
> **pchap123456 said:**
> Thanks for the hint.

 I did check and modified the permissions of /dev/cdrom, /dev/scd0 and /dev/cdrw to give full access to my account but sill the same alas, the CD/DVD option is grayed out in the VM creation wizard.

Never mind thanks for the assistance!

Phil

I think that's a bug in the applet. The kvm cmd takes a -cdrom option. The web-site first looks on Hardy Heron showcased KVM and VirtManager and it too showed a grayed out cdrom option. You also can not specify a mac address with it either, as I recall.

---

### Post by kaivalagi on 2008-04-06
I had a look on launchpad to see whether any bugs etc had been logged for the shortcomings of virt-manager, but couldn't find any (probably because the features are not implemented at all yet).

I have however asked a question on launchpad which I hope will get a response

> [SIZE="3"]**cdrom & mac address support for kvm**[/SIZE]

There seems to be no support for either cdrom devices for guest OS installs or any allowance for mac address setup, when using kvm in Ubuntu Hardy 8.04?

There is a thread on Ubuntuforums here: [http://ubuntuforums.org/showthread.php?t=716387](http://ubuntuforums.org/showthread.php?t=716387) where questions are being asked.

Could you shed some light on these aspects of Virt Manager and maybe post a message in the thread above to clear things up a little?

An "if and when" would suffice if this is a known shortcoming of the UI.

Other than these issues I find your work to have simplified the use of kvm a great deal and I thank you for that!


[URL="https://answers.launchpad.net/virt-manager/+question/29093"]https://answers.launchpad.net/virt-manager/+question/29093
[/URL]

---

### Post by strigare on 2008-04-10
I'm having the same  problem here, the lack of the cdrom option, but it won't get  fixed even if I run virt manger as root.

---

### Post by boscorillium on 2008-04-27
I don't know if this helps, but I have the same exact problem. Adding myself to the two groups (kvm and libvirt) didn't help and I logged out and logged back in.

So I started to attempt tracking down where the breakdown was and I noticed in my user directory that all of the .img files existed for the images that I attempted to create when Virt-Manager failed. So, using kvm I successfully booted an img, using an ISO as the cdrom and it booted fine.

So it would seem things work great, it's just that something in the path isn't meshing well.

---

### Post by kaivalagi on 2008-05-06
There is a proposed patch for cdrom support in virt manager now, details here:

[https://bugs.launchpad.net/ubuntu/+source/virt-manager/+bug/196850]("https://bugs.launchpad.net/ubuntu/+source/virt-manager/+bug/196850")

---

