---
title: "Can't run Windows 10 at 1080p with Virtualbox"
date: 2016-05-21
forum: Virtualisation
---

### Post by osaekomi on 2016-05-21
Hi there.

Apologies if this is a stupid question, but I'm stumped.

I'm trying to run Windows 10 on a Virtualbox VM. I've got it up and running, but I can't get it to display at 1080p. I've tried:

[LIST]
[*]Switching to fullscreen mode - the VB window goes fullscreen but the Windows display remains the same size
[*]Switching to scaled mode and enlarging the Virtualbox window
[*]Running with the display in "hinted" mode and giving it 1080p parameters, which I now read doesn't work with Windows VMs
[/LIST]

I'm running Virtualbox 5.0.18, which I downloaded from the Ubuntu software centre. Previous threads on this subject suggest installing "guest additions," but there's no option to do that in this version of Virtualbox as far as I can see.

In the display settings on Windows 10 there is no option to set the display to 1080p.

Any help you can give me is massively appreciated, thanks!

---

### Post by QIII on 2016-05-21
Hello!

The version of VBox available in the repos is often an older version and is missing some bits by default.  But installing the guest additions is actually done from inside the guest, so that is probably where you are having difficulty.

Actually, if you have installed from the Canonical repo, I would recommend un-installing it.

Then go to VirtualBox's Linux [download page]("https://www.virtualbox.org/wiki/Linux_Downloads").  Follow the instructions in the section "Debian-based Linux distributions".

Then go back to the main [downloads page]("https://www.virtualbox.org/wiki/Downloads") to find and add the VirtualBox 5.0.20 Oracle VM VirtualBox Extension Pack.

Create a new VM with your current Windows virtual disk, then install the Guest Additions by opening your Windows VM, opening the VBox menu bar, clicking "Devices" and then selecting "Insert Guest Additions CD image".

Now, I'm not going to leave you to finish a quiz on your own!  You are very welcome to come back and ask any questions you need to in order to get this done.  There are a lot of us who use VBox, so there will be no shortage of help available.

---

### Post by MAFoElffen on 2016-05-22
Sort of... If you are still on Ubuntu 14.04, your Ubuntu packaged VirtualBox version is only upgradable to version 4.3.36 But if you are release upgraded to Xenial (16.04 LTS), then the Ubuntu Packaged VirtualBox version is at Version 5.0.18.

Whereas with 4.3.36, it used the old Guest Editions. With Ubuntu packaged 5.0.18, you install package virtualbox-ext-pack... albiet that the extension pack is a one time install to the main (host's) Virtualbox program.

So yes, you have to uninstall the old version before installing a new version, but with Ubuntu (as long as you are on a current version of Ubuntu), you still have the option of going with the upstream vendors binary (Oracle VirtualBox) or packages from Ubuntu main.

---

### Post by QIII on 2016-05-22
Oracle has already released 5.0.20, to which one will be upgraded if they have chosen to install from the Oracle download site.   As Oracle does new releases, installing via the virtualbox.org website will keep up.

User preference, of course, but there is no wait for updates when installing via the virtualbox.org repo.

---

### Post by MAFoElffen on 2016-05-22
+1 with Qlll

Truth be told, that is where and how I have mine installed.

---

