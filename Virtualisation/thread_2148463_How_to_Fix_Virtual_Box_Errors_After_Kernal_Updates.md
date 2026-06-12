---
title: "How to Fix Virtual Box Errors After Kernal Updates"
date: 2013-05-25
forum: Virtualisation
---

### Post by gwm on 2013-05-25
Since I upgraded to 13.04 we have had 3 kernal updates (I think).
After each update, vbox refused to run the client OS because the headers no longer matched. I read somewhere that DKMS would automatically sort things out if it is installed. AFAIK I have installed it but each update I have to spend an hour or so combing through the forums till I find the following magic-three-command fix which has worked every time.
```
sudo apt-get install linux-headers-$(uname -r)
sudo apt-get remove virtualbox-dkms
sudo apt-get install virtualbox-dkms
```
I found these in this thread: [http://ubuntuforums.org/showthread.php?t=2145757&highlight=virtual+box+kernel+modules](http://ubuntuforums.org/showthread.php?t=2145757&highlight=virtual+box+kernel+modules)

I don't know what these commands are doing or why they work but work they do.
Please can someone explain them for us?

I think the update runs as a superuser and should be able to take care of such things. So, it would also be good to know why they can't be automated.

As explained later in this thread, the above code should be modified to the following, after which things should happen automagically:
```
sudo apt-get install linux-headers-generic
sudo apt-get install --reinstall virtualbox-dkms
```
Spceial thanks go to TheFu, Jim Kyle and SeijiSensei for their help!

---

### Post by wsv on 2013-05-27
Same with me.
Very annoying, feels like Windows-box.
Why does the update undo our installs, over and over?

---

### Post by gwm on 2013-08-21
When I take time out to think about it, it is actually quite impressive that so little is required.
If things still work the way they did 1000 years ago in the days of steam engines, when I was coding this sort of thing, a change in headers might well move entry points in the kernel's jump tables (if it uses such things) and calls to subroutines might require changed parameters. These things can result in code jumping into the middle of code blocks with serious stack issues and system crashes.

So why does vbox need to be so close to the kernel? I can't vouch for it but I am assuming it is. Performance issues would dictate close coupling of this sort.

My gripe is that to find out what to do, one has to go googling and stuff. I'm not so sure it would be too difficult for the error detection routine that detected the header mismatch in the first place to be programmed to execute the fix automatically.

Wow! I can't believe it was me that said that! It looks like I too am becoming a dumbed down "app" consumer.

---

### Post by JKyleOKC on 2013-08-22
The problem doesn't exist under 12.04 LTS, so it has to be something introduced in the later version. To answer your original question about what the three magic commands do:

1. First command installs the header package for the currently running kernel. Once it's in place, it should update automagically when the kernel itself does. Check with "synaptic" (or apt-get if you prefer that) to verify that the "generic" header package is installed on your system. That's the package that automates header updating as you request.

2 and 3. These commands first remove, then reinstall, the DKMS package. They ought not be necessary since it doesn't change greatly from one kernel version to the next, but they do assure that any potential corruption in DKMS itself is gone before you re-try creating the drivers.

General point: All virtualization programs have to snuggle down very intimately with the kernel itself, in order to steer input and output away from the host system and feed it over to the guest via the virtualizer itself. That's what these modules do, for vbox. Because of this, things such as unexpected loss of power can create real havoc if a VM is running at the time. I just went through two weeks of serious troubleshooting because of exactly such an event. The VM was destroyed. The host system went crazy. Finally, after updates including a new kernel AND a new video driver came through, the host regained its sanity. If you run VMs, be sure to keep your host system **totally** backed up, so that such a disaster can have an easy recovery!

---

### Post by gwm on 2013-08-31
Thanks Jim,
I seem to be missing something here. Perhaps you and I are on different pages or something.

> 1. First command installs the header package for the currently running kernel. Once it's in place, it should update automagically when the kernel itself does.
Since I execute the first command each time, doesn't that mean that the header is then installed? Yet the automagic isn't happening??

> Check with "synaptic" (or apt-get if you prefer that) to verify that the "generic" header package is installed on your system. That's the package that automates header updating as you request.
Long ago, I used command lines and line editors all day, every day. Then the GUI came along and I hardly ever use the command line anylonger. I therefore don't know how to do this.

I take it that the key concept there was that the package must be the **generic** one (whatever that means). Is that the point I have missed?

---

### Post by JKyleOKC on 2013-08-31
I think your conclusion is correct. I too use the GUI most of the time; your best friend in the GUI is the Synaptic package. It can show you what is installed, and what isn't, much more easily than anything else I've tried.

The "deb" package concept attempts (and usually succeeds) in avoiding the "DDL Hell" situation experienced so often elsewhere, by including a list of dependencies in each package. Most of the package manager programs read this list, and automagically download any listed dependencies that aren't already present, right along with the desired package, so that you have all you need before anything begins to actually install.

The "generic" packages that are listed for kernel images and kermel headers do not actually have **ANY** executable code in them. Instead, they list the most recent specific package as a dependency, so that the automagic downloading will grab the right package from the repository. Once you have the generic package installed, it will be updated each time the real package to which it refers gets an update, so that "installing" it will grab the correct version for you.

There's no need to install the current version via that first command more than once, either. If your kernel model then fails to build, it's probably something entirely different causing it. The dkms package (dynamic kernel module system) requires that the build-essential package be installed, to give it the tools with which it works, and it's possible you might not have this. Again, Synaptic can show you whether you do or not.

Hope this helps! Back in the 90s I was one of the most vocal opponents of the GUI, and even chaired a panel discussion at Software Development '90 titled "GUI? Phooey!" which was loaded against the GUI approach -- but over the years I've learned its value, and use it much more than the command line (which, however, continues to be my go-to tool when things get really serious).

---

### Post by SeijiSensei on 2013-08-31
All these problems would be resolved by using the official VirtualBox release, adding the repository to /etc/apt/sources.list, and installing the Oracle key.  If you have not read [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads), I suggest you take a look at the section on "Debian-based" downloads.

---

### Post by JKyleOKC on 2013-08-31
> **SeijiSensei said:**
> **All these problems would be resolved** by using the official VirtualBox release, adding the repository to /etc/apt/sources.list, and installing the Oracle key.  If you have not read [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads), I suggest you take a look at the section on "Debian-based" downloads.I strongly disagree with the statement that I've emphasized; adding the vbox PPA to sources.lst **will** assure that the OP gets timely updates to vbox, and it's something that every vbox user needs to do, but it won't assure that he also gets needed updates to the kernel headers, or to anything else that needs DKMS to stay current (such as Nvidia vidro drivers).

The Oracle packages have **never** included kernel modules that match the *buntu kernels, in the six years that I've been using them. DKMS always includes a line in the log to that effect.

---

### Post by SeijiSensei on 2013-08-31
I guess I never noticed that since I almost always have the kernel headers, build-essential, and the dkms package installed.  Intriguingly they are listed as "recommended" by the Oracle VB package rather than being a strict dependency.

```

$ dpkg -s virtualbox-4.2
Package: virtualbox-4.2
Status: install ok installed
Priority: optional
Section: contrib/misc
Installed-Size: 135720
Maintainer: Oracle Corporation <info@virtualbox.org>
Architecture: amd64
Version: 4.2.16-86992~Ubuntu~raring
Replaces: virtualbox
Provides: virtualbox
Depends: libc6 (>= 2.15), libcurl3 (>= 7.16.2), libdevmapper1.02.1 (>= 2:1.02.20), libgcc1 (>= 1:4.1.1), libgl1-mesa-glx | libgl1, libpng12-0 (>= 1.2.13-4), libpython2.7 (>= 2.7), libqt4-network (>= 4:4.5.3), libqt4-opengl (>= 4:4.7.2), libqtcore4 (>= 4:4.8.0), libqtgui4 (>= 4:4.8.0), libsdl1.2debian (>= 1.2.11), libssl1.0.0 (>= 1.0.0), libstdc++6 (>= 4.6), libx11-6, libxcursor1 (>> 1.1.2), libxext6, libxinerama1, libxml2 (>= 2.7.4), libxmu6, libxt6, zlib1g (>= 1:1.1.4), psmisc, adduser
Pre-Depends: debconf (>= 1.1) | debconf-2.0
Recommends: libasound2, libpulse0, libsdl-ttf2.0-0, dkms, linux-headers, gcc, make, binutils, pdf-viewer, libgl1, python-central
Conflicts: virtualbox, virtualbox-guest-additions-iso, virtualbox-ose
Conffiles:
 /etc/init.d/vboxdrv 2b0d27a8b51dae83b8ac7dc30de531d7
 /etc/init.d/vboxautostart-service 13913287468da586ef47e7c9cae4161d
 /etc/init.d/vboxweb-service 7d3ec328e82e986c612678736730e899
 /etc/init.d/vboxballoonctrl-service fbb712caf488eb8860c4fc20301e7075
Description: Oracle VM VirtualBox
 VirtualBox is a powerful PC virtualization solution allowing you to run a
 wide range of PC operating systems on your Linux system. This includes
 Windows, Linux, FreeBSD, DOS, OpenBSD and others. VirtualBox comes with a broad
 feature set and excellent performance, making it the premier virtualization
 software solution on the market.
Python-Version: >= 2.4

```

---

### Post by JKyleOKC on 2013-08-31
Mine reads about the same: ```
jk@mehitabel:~$ dpkg -s virtualbox-4.2
Package: virtualbox-4.2
Status: install ok installed
Priority: optional
Section: contrib/misc
Installed-Size: 136546
Maintainer: Oracle Corporation <info@virtualbox.org>
Architecture: i386
Version: 4.2.16-86992~Ubuntu~precise
Replaces: virtualbox
Provides: virtualbox
Depends: libc6 (>= 2.15), libcurl3 (>= 7.16.2-1), libdevmapper1.02.1 (>= 2:1.02.20), libgcc1 (>= 1:4.1.1), libgl1-mesa-glx | libgl1, libpng12-0 (>= 1.2.13-4), libpython2.7 (>= 2.7), libqt4-network (>= 4:4.5.3), libqt4-opengl (>= 4:4.7.2), libqtcore4 (>= 4:4.8.0), libqtgui4 (>= 4:4.8.0), libsdl1.2debian (>= 1.2.10-1), libssl1.0.0 (>= 1.0.0), libstdc++6 (>= 4.6), libx11-6, libxcursor1 (>> 1.1.2), libxext6, libxinerama1, libxml2 (>= 2.7.4), libxmu6, libxt6, zlib1g (>= 1:1.1.4), psmisc, adduser
Pre-Depends: debconf (>= 1.1) | debconf-2.0
Recommends: libasound2, libpulse0, libsdl-ttf2.0-0, dkms, linux-headers, gcc, make, binutils, pdf-viewer, libgl1, python-central
Conflicts: virtualbox, virtualbox-guest-additions-iso, virtualbox-ose
Conffiles:
 /etc/init.d/vboxdrv 2b0d27a8b51dae83b8ac7dc30de531d7
 /etc/init.d/vboxautostart-service 13913287468da586ef47e7c9cae4161d
 /etc/init.d/vboxweb-service 7d3ec328e82e986c612678736730e899
 /etc/init.d/vboxballoonctrl-service fbb712caf488eb8860c4fc20301e7075
Description: Oracle VM VirtualBox
 VirtualBox is a powerful PC virtualization solution allowing you to run a
 wide range of PC operating systems on your Linux system. This includes
 Windows, Linux, FreeBSD, DOS, OpenBSD and others. VirtualBox comes with a broad
 feature set and excellent performance, making it the premier virtualization
 software solution on the market.
Python-Version: >= 2.4
jk@mehitabel:~$ 

```I never noticed the "recommends" entries; I installed build-essential a long time ago and of course that put all the compiler tools in place so they would not show up in the update notices.

I suspect our listings of the package may help the OP grok the way deb files handle dependency issues. Hope so, anyway.

gwm: You can configure the Update Manager not to show "recommends" packages, which are not absolutely required in every case, but it's best to let them show up because sometimes they **are** essential. Note, too, that the package name isn't always exactly what you might expect it to be. The command "dpkg -l" (lower-case L) at the command line will give you a list of all packages installed on your system.

---

### Post by gwm on 2013-09-02
I tried > dpkg -l build-essential, dkms, linux-headers-3.8.0-29, linuc-headers-3.8.0-29-generic all seem to be installed.
I also found the following virtual box items. Perhaps the problem is here somehow.
> ii  virtualbox                          4.2.10-dfsg-0ubuntu2.1 amd64                  x86 virtualization solution - base binaries
rc  virtualbox-4.2                      4.2.12-84980~Ubuntu~ra amd64                  Oracle VM VirtualBox
ii  virtualbox-dkms                     4.2.10-dfsg-0ubuntu2.1 all                    x86 virtualization solution - kernel module sources for dkms
ii  virtualbox-qt                       4.2.10-dfsg-0ubuntu2.1 amd64                  x86 virtualization solution - Qt based user interface
I don't know what the significance of the prefixes ii and rc are but I was wondering if maybe I've somehow double installed or somehow created a clash when I was originally trying to work this all out.

Next I copied your dpkg -s command with the following result
> $ dpkg -s virtualbox-4.2
Package: virtualbox-4.2
Status: deinstall ok config-files
Priority: optional
Section: contrib/misc
Installed-Size: 136062
Maintainer: Oracle Corporation <info@virtualbox.org>
Architecture: amd64
Version: 4.2.12-84980~Ubuntu~raring
Config-Version: 4.2.12-84980~Ubuntu~raring
Replaces: virtualbox
Provides: virtualbox
Depends: libc6 (>= 2.15), libcurl3 (>= 7.16.2), libdevmapper1.02.1 (>= 2:1.02.20), libgcc1 (>= 1:4.1.1), libgl1-mesa-glx | libgl1, libpng12-0 (>= 1.2.13-4), libpython2.7 (>= 2.7), libqt4-network (>= 4:4.5.3), libqt4-opengl (>= 4:4.7.2), libqtcore4 (>= 4:4.8.0), libqtgui4 (>= 4:4.8.0), libsdl1.2debian (>= 1.2.11), libssl1.0.0 (>= 1.0.0), libstdc++6 (>= 4.6), libx11-6, libxcursor1 (>> 1.1.2), libxext6, libxinerama1, libxml2 (>= 2.7.4), libxmu6, libxt6, zlib1g (>= 1:1.1.4), psmisc, adduser
Pre-Depends: debconf (>= 1.1) | debconf-2.0
Recommends: libasound2, libpulse0, libsdl-ttf2.0-0, dkms, linux-headers, gcc, make, binutils, pdf-viewer, libgl1, python-central
Conflicts: virtualbox, virtualbox-guest-additions-iso, virtualbox-ose
Conffiles:
 /etc/init.d/vboxdrv 91e092513c1ca096e16cd5b74f358b2a
 /etc/init.d/vboxautostart-service 13913287468da586ef47e7c9cae4161d
 /etc/init.d/vboxweb-service 7d3ec328e82e986c612678736730e899
 /etc/init.d/vboxballoonctrl-service fbb712caf488eb8860c4fc20301e7075
Description: Oracle VM VirtualBox
 VirtualBox is a powerful PC virtualization solution allowing you to run a
 wide range of PC operating systems on your Linux system. This includes
 Windows, Linux, FreeBSD, DOS, OpenBSD and others. VirtualBox comes with a broad
 feature set and excellent performance, making it the premier virtualization
 software solution on the market.
Python-Version: >= 2.4

---

### Post by JKyleOKC on 2013-09-02
It appears that you've removed the latest build of vbox (4.2.12) and replaced it with an older version, probably from the Ubuntu repositories. At this point, I would use Synaptic to "completely remove" the existing copies of vbox and its accessories, then add the PPA from Oracle's site (which would make their updates feed into the update manager) and finally re-install vbox from the new entry in Synaptic. This ought to pull them all to the same revision level.

Since vbox normally stores its virtual machines in your home directory, they shouldn't be affected by all this; I've replaced vbox several times over the years with no change to any of my VMs. However to be safe it would be a good idea to copy them to an externam drive if you have enough space available on one (my external backup is more than 200 GB but that's for 14 VMs).

Those "ii" and "rc" prefixes are explained (rather cryptically) at the top of the "dpkg -l" report; the first letter is desired action, where i means install and r means remove; the second is current status, with i meaning installed and c meaning configuration file only. Thus "ii" means that the package is installed while "rc" means that it was removed but configuration files remain. Doing a "purge" or "completely remove" will get rid of those configuration files.

You might be able to fix things by simply adding the Oracle PPA to your sources, doing a "Check" in Synaptic to be sure it's added to your local status database, then selecting the new entry for 4.2 that it put into your Synaptic listing and choosing "reinstall" for it. If this does the trick, it's certainly a simpler way to solve the problem.

Keep us posted!

---

### Post by gwm on 2013-09-02
Thanks to both of you for your input. It has got me thinking along the right lines.
Then, in another thread relating to problematic behaviour of my client OS
[http://ubuntuforums.org/showthread.php?t=2166924&p=12777110#post12777110]("http://ubuntuforums.org/showthread.php?t=2166924&p=12777110#post12777110")
TheFu gave me a link showing me how to specify the headers so that dkms would pick it up correctly.
I feel quite exited that this problem will now perhaps be behind me.
Thank you once again.
I have yet to prove that it works of course but I'm quite confident it will.

I have since had a kernel update.
Everything ran smoothly and the client starts up correctly, thus indicating that the kernel modules updated correctly.
:guitar:

---

