---
title: "Ubuntu messed up after failed upgrade to 14.04 final beta, help appreciated"
date: 2014-03-31
forum: Ubuntu Development Version
---

### Post by ohremd on 2014-03-31
Dear forum members,

I tried upgrading to 14.04 a few hours ago but at some point my laptop only displayed a black screen and got stuck. After a hard reset, I couldn't boot Ubuntu anymore, but I somehow managed to solve this by repairing packages in recovery mode. I can boot Ubuntu now, but Unity is completely messed up and only displays the wallpaper and a cursor. Not even CTRL+ALT+T works. Gnome, however, seems to work for the most part and I already tried "sudo apt-get -f dist-upgrade". However, this didn't solve the problem, Unity is still completely broken.

I'd consider myself a beginner, but I know how to use the terminal a little bit. Can you tell me what to do to find out where the problem lies? I was very happy with my system and hope I can restore it to the way it was before (Why did I upgrade? So stupid ](*,):evil:)

Thanks a lot!
Dom

---

### Post by grahammechanical on 2014-03-31
A lot of us recommend a fresh install and your case is one reason why we do that.

At the Grub boot menu select Recovery mode. At the Recovery menu select Network. Then select Root. Now you can run commands. Let us see if the upgrade completed.

```
do-release-upgrade
```

These reset Compiz and Unity. May need to run them from a TTY. Ctrl+Alt+F2 when at that broken desktop. 

```
dconf reset -f /org/compiz
```
```
setsid unity
```

By the way, when at the desktop with the wallpaper we can right click the wallpaper and if we select Change Desktop Background. That will open System Settings. We can then open Software and Updates>Additional Drivers tab. Then, if it was me, I would activate the Nouveau open source driver. 

I have come to the opinion that when upgrading to a newer version of Ubuntu we should get the system as default as possible and that includes replacing a proprietary video driver with Nouveau.

Regards.

---

### Post by ohremd on 2014-04-01
Thanks for the help, much appreciated.

Unfortunately, I could not get networking enabled in recovery mode. I believe for some reason it tries to activate my mobile broadband instead of the wireless device and fails. However, I entered the "do-release-upgrade" command in the GNOME terminal and it says "No new release found". Maybe that information helps?

As for the other commands, those didn't work. In the broken Unity I can't do anything, not even a right-click and neither does any sort of keyboard shortcut work.

I also tried to reinstall ubuntu-desktop (I don't know if that makes any sense) with "sudo apt-get install --reinstall ubuntu-desktop" and this is the output:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 compiz-gnome : Depends: gnome-settings-daemon-schemas (>= 3.4.2-0ubuntu9) but it is not going to be installed
 ubuntu-desktop : Depends: ubuntu-session but it is not going to be installed
                  Recommends: aisleriot but it is not going to be installed
                  Recommends: empathy but it is not going to be installed
                  Recommends: firefox but it is not going to be installed
                  Recommends: gnome-mahjongg but it is not going to be installed
                  Recommends: gnome-orca but it is not going to be installed
                  Recommends: gnome-sudoku but it is not going to be installed
                  Recommends: gnomine but it is not going to be installed
                  Recommends: libreoffice-calc but it is not going to be installed
                  Recommends: libreoffice-gnome but it is not going to be installed
                  Recommends: libreoffice-impress but it is not going to be installed
                  Recommends: libreoffice-math but it is not going to be installed
                  Recommends: libreoffice-ogltrans but it is not going to be installed
                  Recommends: libreoffice-pdfimport but it is not going to be installed
                  Recommends: libreoffice-presentation-minimizer but it is not going to be installed
                  Recommends: libreoffice-writer but it is not going to be installed
                  Recommends: onboard but it is not going to be installed
                  Recommends: thunderbird but it is not going to be installed
                  Recommends: thunderbird-gnome-support but it is not going to be installed
                  Recommends: xul-ext-ubufox but it is not going to be installed
                  Recommends: xul-ext-unity but it is not going to be installed
                  Recommends: xul-ext-webaccounts but it is not going to be installed
 unity-settings-daemon : Depends: gnome-settings-daemon-schemas (>= 3.8) but it is not going to be installed
                         Depends: gnome-settings-daemon-schemas (< 3.10) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

When I try "apt-get -f install" this is the output:

```

Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  blt geoclue-2.0 libcpufreq0 libdb5.1:i386 libestr0 libgsoap4 libllvm3.3:i386 libmozjs-17.0-0
  libsasl2-modules:i386 libssl1.0.0:i386 libtasn1-3:i386 libtcl8.5 libtk8.5 tcl8.5
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  gnome-settings-daemon-schemas
The following NEW packages will be installed
  gnome-settings-daemon-schemas
0 upgraded, 1 newly installed, 0 to remove and 851 not upgraded.
5 not fully installed or removed.
Need to get 0 B/44,2 kB of archives.
After this operation, 189 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 245368 files and directories currently installed.)
Preparing to unpack .../gnome-settings-daemon-schemas_3.8.6.1-0ubuntu10_all.deb ...
Unpacking gnome-settings-daemon-schemas (3.8.6.1-0ubuntu10) ...
dpkg: error processing archive /var/cache/apt/archives/gnome-settings-daemon-schemas_3.8.6.1-0ubuntu10_all.deb (--unpack):
 trying to overwrite '/usr/share/GConf/gsettings/gnome-settings-daemon.convert', which is also in package gnome-settings-daemon 3.10.2-0ubuntu1~saucy6
Processing triggers for gconf2 (3.2.6-0ubuntu2) ...
Errors were encountered while processing:
 /var/cache/apt/archives/gnome-settings-daemon-schemas_3.8.6.1-0ubuntu10_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Do these information help in any way?

Thanks a lot!
Dom

---

### Post by Mark Phelps on 2014-04-01
> I'd consider myself a beginner,

Then ... you should not be running a Beta version of the OS.  

Primary purpose of using a pre-release version is to test for bugs -- which is not something a beginner should be doing.

Additionally, when you encounter problems with a pre-release version, as you have, you need to report them in the Ubuntu+1 section, not here.  This section is for Released versions of the OS.

---

### Post by Toz on 2014-04-01
*Since 14.04 is still in beta, moved to the **Ubuntu+1** subforum*.

---

### Post by Mateusz Stachowski on 2014-04-01
Looking at output of "apt-get install -f" command is obvious that you were using [GNOME3 Team PPA]("https://launchpad.net/~gnome3-team/+archive/gnome3") because gnome-settings-daemon 3.10.2-0ubuntu1~saucy6 is a package from this PPA for 13.10. This package is newer than the [version available]("http://packages.ubuntu.com/search?keywords=gnome-settings&searchon=names&suite=trusty&section=all") in Trusty repos and GNOME3 Team PPA doesn't even support Trusty.

Also this PPA should be purged before upgrading to a newer release it is in the description.

> PPA description

Before upgrading your system to a new Ubuntu release (i.e. from Ubuntu 13.04 to 13.10), you should probably run ppa-purge ppa:gnome3-team/gnome3 first.

It is probably to late to try ppa-purge now and you most likely have multiple GNOME 3 packages which aren't compatible with Trusty repository. Although it is your best bet. Enable the PPA you might need to change its sources to Saucy and then try purging.

---

### Post by ohremd on 2014-04-01
Thanks for your replies. After googling around a little bit and trying a few things I decided it's probably best to go with a fresh install. 
Mateusz, you're right, a few weeks ago I indeed messed around with the GNOME3 PPA and I didn't purge before upgrade. Will be more careful in the future - and no more Betas.

Thanks again,
Dom

---

### Post by monkeybrain20122 on 2014-04-01
> **ohremd said:**
> 
Mateusz, you're right, a few weeks ago I indeed messed around with the GNOME3 PPA and I didn't purge before upgrade. Will be more careful in the future - and no more Betas.

Thanks again,
Dom

And please, no more 'upgrade' especially if you use ppas (and do other optimization/customization), do a clean install instead.

---

