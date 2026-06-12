---
title: "Linux distros without any GUI"
date: 2015-01-20
forum: Ubuntu, Linux and OS Chat
---

### Post by flaymond on 2015-01-20
Hello, I'm here looking for a Linux distribution that only use CLI (and text editor for scripting maybe). I wanna practice 'bashing' in it, instead Ubuntu that I use for most task (mainly learn to programming). Is there any 'CLI' distro that can I use? I wanna see an OS without any GUI (I've never seen it though!). 


# - I don't have any CD's, just a USB. Is there any OS that only provide CLI and can use USB to install it?

Thanks for your help! :KS

---

### Post by buzzingrobot on 2015-01-20
Any Linux can be started without a GUI. In fact, they all boot that way, and then start the GUI.  Learn about init levels and grub to get a handle on that.

But... Bash is Bash whether running in a terminal on Ubuntu or in Ubuntu or any other Linux booted without a GUI. No real need to stand up a separate machine just to get started with Bash scripting.

---

### Post by kpatz on 2015-01-20
Ubuntu Server installs without a GUI.  I've never tried making a USB installer for it, but I imagine it can be done.

You can boot any of the Ubuntu live CDs in CLI mode by adding "text" to the boot options.

But like buzzingrobot said, you can do bash scripting and programming in CLI from a terminal window just the same, and even better, you can easily have several open and can copy/paste between them.

---

### Post by flaymond on 2015-01-20
How can I boot without GUI though? I don't know. Is there any guide to do that safely? (actually...I wanna a separate OS that can 'quarantine' my 'bashing' section...practicing bash in Ubuntu is very dangerous and i accidentally deleted boot folder and need to reinstall it every time)

---

### Post by sudodus on 2015-01-20
Learn how to use ***Ubuntu mini.iso***. If you add no extras at all, you will get a very minimal system (which boots into a text screen). From that system you can add lubuntu-desktop to get Lubuntu, xubuntu-desktop to get Xubuntu etc. You can add several server alternatives or you can build your own system 'almost' from scratch, well at least your desktop environment and set of application programs. ***bash*** will be there from right after rebooting into the very minimal system.

[TABLE]
[TR]
[TD] 14.04 Trusty Tahr[/TD]
[TD] [32 bit mini ISO]("http://archive.ubuntu.com/ubuntu/dists/trusty/main/installer-i386/current/images/netboot/mini.iso")[/TD]
[TD][64 bit mini ISO]("http://archive.ubuntu.com/ubuntu/dists/trusty/main/installer-amd64/current/images/netboot/mini.iso")[/TD]
[/TR]
[/TABLE]

If these mini.iso files no longer work, I think you can find better versions at

[http://archive.ubuntu.com/ubuntu/dists/trusty-updates/main/installer-i386/current/images/netboot/](http://archive.ubuntu.com/ubuntu/dists/trusty-updates/main/installer-i386/current/images/netboot/)

and

[http://archive.ubuntu.com/ubuntu/dists/trusty-updates/main/installer-amd64/current/images/netboot/](http://archive.ubuntu.com/ubuntu/dists/trusty-updates/main/installer-amd64/current/images/netboot/)

with the corresponding md5sums in each versions parent directory.

The following link may help you get started with the Ubuntu mini (it is about Lubuntu, but can be applied more generally to other flavours of Ubuntu)

[https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall](https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall)

---

### Post by kpatz on 2015-01-20
> **InterProg said:**
> How can I boot without GUI though? I don't know. Is there any guide to do that safely? (actually...I wanna a separate OS that can 'quarantine' my 'bashing' section...practicing bash in Ubuntu is very dangerous and i accidentally deleted boot folder and need to reinstall it every time)Do your practicing as a normal user and don't use sudo, then you won't trash your OS if you goof.  You may still trash your home folder but that's what backups are for.

If you're testing scripts that need to modify the system, you could install your test OS in a VM such as Virtualbox, and use the snapshot feature to restore the virtual machine if you trash it.

---

### Post by ian-weisser on 2015-01-20
> **InterProg said:**
> How can I boot without GUI though?
Exactly the same way you boot now. Booting and GUI are not related. 
 
> **InterProg said:**
> Is there any guide to do that safely? (actually...I wanna a separate OS that can 'quarantine' my 'bashing' section.

There are many,many ways. Personally, I think the EASIEST way is to create an LXC container, and play with that. No GUI, sandboxed from the rest of your system, and quite safe. See [http://www.stgraber.org/2013/12/20/lxc-1-0-your-first-ubuntu-container/](http://www.stgraber.org/2013/12/20/lxc-1-0-your-first-ubuntu-container/)

Easy way to create and login to a container named 'my-container':
```
sudo apt-get install lxc
sudo lxc-create -t ubuntu -n my-container  # Create a container
sudo lxc-start -n my-container -d          # Start (boot) the container
sudo lxc-console -n my-container           # Login to the container. username: ubuntu   password: ubuntu
```
There. You're logged into a separate, safe, text-only environment to play with.

---

### Post by Tadaen_Sylvermane on 2015-01-20
+1 on Virtualbox snapshots. Is most user friendly way. As pointed above though bash is bash regardless of gui or not. If anything you are making it harder on yourself by trying to learn it without a gui as you can't have a browser opened to google or whatever to search for answers to things you can't figure out.

---

### Post by sudodus on 2015-01-20
> **Tadaen_Sylvermane said:**
> +1 on Virtualbox snapshots. Is most user friendly way. As pointed above though bash is bash regardless of gui or not. If anything you are making it harder on yourself by trying to learn it without a gui as you can't have a browser opened to google or whatever to search for answers to things you can't figure out.

A big [SIZE=4]+1[/SIZE] :-)

---

### Post by flaymond on 2015-01-21
I wanna dual boot, that's why I wanna a separated OS...So I can 'play' with bash in it without afraid to damage the system...I'm looking for CLI because it's lightweight and don't take too much time to download. Talking about mini? Is that referred to the minimal ISO?...I never tried that (and that look so good to start with). and of course, I'll still use Ubuntu as my primary OS. What I'm looking is just for 'training ground'. or 'sandbox'.

---

### Post by sudodus on 2015-01-21
It is worthwhile to learn how to use the Ubuntu mini.iso alias minimal install alias netboot iso as described in post #5.

But it can also be worthwhile to learn bash in a system where you can use the convenient mark and paste with middleclick, and to have a web browser window open with a bash tutorial, so I recommend to use at least a window manager (jwm, fluxbox or openbox) if not a full desktop environment.

It is easy and light-weight to install for example **xinit fluxbox xterm** into a minimal text screen system (made from the mini.iso). See also this link showing the sizes of different systems

[https://help.ubuntu.com/community/9w/RAM_%26_disk_usage](https://help.ubuntu.com/community/9w/RAM_%26_disk_usage)

***9w*** is an installer that needs very low RAM and can make it convenient to install such minimal systems.

---

### Post by flaymond on 2015-01-21
Thanks for you advice guys! I really appreciate for your volunteering to answer this thread! :KS

---

### Post by sudodus on 2015-01-21
You are welcome and good luck :-)

And please come back and tell us what will be your choice in this case, maybe your choice will change with time ...

---

### Post by mastablasta on 2015-01-22
> **InterProg said:**
> I wanna dual boot, that's why I wanna a separated OS...So I can 'play' with bash in it without afraid to damage the system...I'm looking for CLI because it's lightweight and don't take too much time to download. Talking about mini? Is that referred to the minimal ISO?...I never tried that (and that look so good to start with). and of course, I'll still use Ubuntu as my primary OS. What I'm looking is just for 'training ground'. or 'sandbox'.

which is why exactly you DO NOT WANT to dualboot. use virtualbox or some container instead. it will provide a safe environment to experiment in. if anything goes wrong previous state in virtual computer is quickly restored with a click of a mouse. if you dualboot and mess it up there is nothing that prevents access for the mess to spill over to the other side of the boot. dual boot just means that a boot loader gives a choice on which system to boot at start. but both systems (tough independent) are still installed on same computer and have access to the rest of the hard disk(s) for example. you can easily format the other partition by accident.

in virtualbox (and similar) the OS is contained inside virtual computer. you can mess it up completely, delete format, test try and then restore it fast. been there, done that. I installed a different desktop manager. some didn't work quite right and messed up the os at boot. a quick restore of snapshot from previous time got me back to the start when things went wrong.

---

### Post by flaymond on 2015-01-22
Is virtualbox will require a lot of resources while launching it? I try to avoid it because it seems like it will do that. I just got 1GB ram, and 1.73 ghz celeron processor and 32-bit type.

---

### Post by Elfy on 2015-01-22
> **InterProg said:**
> Is virtualbox will require a lot of resources while launching it? I try to avoid it because it seems like it will do that. I just got 1GB ram, and 1.73 ghz celeron processor and 32-bit type.

I'd carry on ignoring it ...

---

### Post by sudodus on 2015-01-22
You can try with Virtualbox if you wish, but I would say you need more RAM (at least 2 GB) for it to work well.

One alternative might be to get more RAM, but another and maybe better  alternative is to get an old (and very cheap) second computer, where you can  run a very light-weight system and learn bash and various command line tools.

-o-

If you decide to dual boot, to have peace of mind, ***take regular backups*** of your personal files and your main operating system. Then you can dual boot into a second 'experimental' operating system, and the worst thing you can expect is that you would need to restore your personal files or the main operating system from the backup.

But probably you will 'only' break the second 'experimental' operating system, which should be easy to re-install.

---

### Post by mastablasta on 2015-01-22
> **InterProg said:**
>  I just got 1GB ram, and 1.73 ghz celeron processor and 32-bit type.

in that case ignore it indeed. unless you are currently using some light desktop environment, then you could get a CLI working. virtualbox itself needs some ram and then you need to dedicate some to it. but your CPU is also slow and won't handle virtualisation well.

---

### Post by Lars Noodén on 2015-01-22
> **InterProg said:**
> I try to avoid it because it seems like it will do that. I just got 1GB ram, and 1.73 ghz celeron processor and 32-bit type.

LXC was mentioned above.  I haven't tried it yet but it looks promising.  An even simpler route would be to create a target for chroot using debootstrap.  Then as long as you are chrooted inside the target, you can mess around to your heart's content.  There are some things you won't be able to do with chroot, but scripting and such will be just fine.

---

### Post by flaymond on 2015-01-22
Is lxc is just like VM? but without GUI? I really scare if I damaged my system and need to reinstalling again and again (that was pretty sad because of the slow speed internet when on updating).

---

### Post by sudodus on 2015-01-22
If you have an external drive, and backup your system, you need not download and update again. For example, you can make a compressed image with Clonezilla, and add some incremental backup on top of that.

(I don't know LXC, maybe you can find more details via the internet.)

---

### Post by Lars Noodén on 2015-01-22
> **InterProg said:**
> Is lxc is just like VM? but without GUI? I really scare if I damaged my system and need to reinstalling again and again (that was pretty sad because of the slow speed internet when on updating).

From what I read LXC is like virtualization but for the OS and not hardware, so it would use a lot less than Qemu or VirtualBox.  However, I've only read about it so far.  Others will have to answer with actual experience.

Using chroot with a filesystem created by debootstrap would use the least amount of system resources and work for scripting.  

+1 to making backups

---

### Post by ian-weisser on 2015-01-22
> **InterProg said:**
> Is lxc is just like VM?
No. It's a container (OS sort-of-but-not-really-emulator). Not a Virtual Machine (sort-of-but-not-really-hardware emulator).
However, for your purposes, it's a lightweight and safe sandbox to play in.
Anything you do in the container stays in the container. The container has a different filesystem, a different IP address, etc.

If it were not safe, and I had not tried it myself, I would not have suggested it.

If you are worried about preserving your data, that's a separate issue. Backups. Backups. Backups.

Lars Nooden is right (as usual): A chroot is also a very safe and even lighter-weight way to go.

Try them all. See which like best.

---

### Post by flaymond on 2015-01-23
Thanks for your help! Now I can experimenting bash because all of you guys help! I really appreciate it! :p:p:p

---

### Post by justingx2 on 2015-01-30
All of them? Just change your init level or Ctrl-alt-f-key (except 7 which will bring you into GUI).

---

### Post by first_last2 on 2015-03-28
Run Slackware on it.

CLI, not a bloated GUI "by default", faster CD/DVD boot time for install, faster boots, faster install, faster to get up and running.
You will actually learn Linux that way too.
:)

---

### Post by SurfaceUnits on 2015-04-14
Just open a tty session and go for it

[https://mostlylinux.wordpress.com/troubleshooting/ttysessions/](https://mostlylinux.wordpress.com/troubleshooting/ttysessions/)

---

### Post by syntaxerror74 on 2015-04-15
> **Tadaen_Sylvermane said:**
> If anything you are making it harder on yourself by trying to learn it without a gui as you can't have a browser opened to google or whatever to search for answers

Really not? ;)
You've already heard of **lynx**, haven't you? :D This needs no X11 environment to work.

---

