---
title: "My adventure with Fedora 11"
date: 2009-04-22
forum: The Cafe
---

### Post by Kazade on 2009-04-22
Hi all, I'm an avid Ubuntu user, however sometimes I try other distros to see what's going on outside the world of Ubuntu. On Monday after running Jaunty since Alpha 3, I thought I'd try out the beta of Fedora 11 (specifically coz I wanted to see KMS in action)... which is where my adventure begins :)

DISCLAIMER: I'm well aware that pre-releases have bugs, I hardly ever run stable releases of Ubuntu (my upgrade process is to move my main desktop to the next release at Alpha 3). 

OK. So the first thing I did was Google "Fedora 11 beta" and download via the torrent (I was unaware at this point that there had been a later "snap1" release). I downloaded the LiveCD ISO, burnt it to disk and booted into the LiveCD. All was fine.

My partition set up is pretty normal, I have Windows on the Primary partition (not that I use it much, if ever, but it refused to install to any other partition) then an extended partition laid out like so:
> 
/dev/sda5 -> /home
/dev/sda6 -> /
/dev/sda7 -> swap

Anyway, I digress, my point is that the partitions were ready, I just wanted to replace my Ubuntu 9.04 install with a Fedora install, leaving everything else untouched.

So I get to the partitioning screen in the installer, choose "custom" and select the / partition, I decided to try ext4 (I use it on my laptop and aside from a few zero-length files when it's been hard reset it's been pretty good). So I format the / partition as ext4, and just because I'm used to Ubuntu's installer doing it for me, I also explicitly format the swap partition. All is well, until I click "next". At which point I'm greeted by this message (or something like this):
> 
"Cannot boot from an ext4 partition"

Hmm, weird, Ubuntu does it fine... oh well. So I go back, change it to ext3 and continue the install. Everything progresses fine until the very last stage when I hit this (again from memory):
> 
"Fatal error. Cannot mount /dev/sda6 as /"

Bugger. 

I tried the install twice more, once after a reboot. Same problem every time. Also weirdly, the / partition was displayed as ext4.. I chose ext3(!?). After some Googling I did find a bug report, but there was no workaround. So I went back to the Fedora download page and find that there is a "snap1" release which is a bit later than the beta. "Surely they must have fixed such a show stopper pretty quickly", I thought.

So I download, burn and boot the snap1 release. Start the installer get to the partitioning screen, try ext4 once more just in case and again get the "Cannot boot from ext4" error. So I switch back to ext3 as before and attempt to continue... except I can't, this time I get (from memory):
> 
"This livecd image must be installed to an ext4 partition"

Huh? So, I can't boot from an ext4 partition, but I must install to one? Now, at this stage I *could* have deleted the / partition completely, created a /boot partition as ext3 and then a / parition as ext4. But I really didn't want to mess around creating and deleting partitions when I have data on the /home partition, formatting partitions is quite dangerous enough for me (yes I should have backed up etc. etc.).

So, I remember reading in the bug report that the Alpha version didn't suffer the same bug. So after some browsing of mirrors I found, downloaded, burned and booted the Alpha. I kept the partition as ext3 and the installation went without a hitch (yay!).

So I reboot, log in, check my home folder... ah.

So that particular time through the installation I'd forgotten to mount the /home partition. No problem, I just edit /etc/fstab, set my home partition to be mounted at /home and reboot.

30 seconds later I realize that Fedora's UIDs don't start at 1000 like Ubuntu... they start at 500. Rendering my home folder unreadable by my user. I've seen this before, I just need to switch to a terminal (CTRL+ALT+F2) and run chown on the home folder. So I press CTRL+ALT+F2 (bear in mind I can't log in graphically at this point.. Gnome just hangs).

Interestingly I'm not dropped to the terminal. Instead I'm given an "Out of range" error by my monitor. Side effect of KMS perhaps? The only way for me to fix the error is to reboot, alter Grub to boot into runlevel 3, and then run the chown command, then reboot again and tada, I'm in to Fedora with all my files. 

Only that's not the end of the story... I'll continue later, I should do some work... Stay tuned for part II :)

---

### Post by gnomeuser on 2009-04-22
Your ext4 problem is caused by Fedora not patching grub to support ext4 as /boot. You do not have a separate /boot thus.. boom.

I filed a bug with the patch Ubuntu uses for this [2 months ago](https://bugzilla.redhat.com/show_bug.cgi?id=486284). It is reported as working and yet they did not apply it and now it's to late for F11 before release. *sigh*

That being said the Anaconda installer should have barked at you for not having a separate /boot on non-ext4. If it did not that is a serious bug.

Lots of nice things in Fedora 11, I hope you have fun exploring it.

---

### Post by WalmartSniperLX on 2009-04-22
Just take your time to explore F11 beta. Fedora in general is one of the most bleeding edge distros that still keeps a fairly easy to use interface. Overall, Fedora has always been my favorite distribution. However, some stability issues I had in the past with my current hardware lead me back to Ubuntu. Hopefully F11 will have all your problems fixed by release, or at least 3 months in. I usually like to wait a few months before getting Fedora. They tend to release unsupported X server builds as well as other extremely early build software packages on release.

---

### Post by gnomeuser on 2009-04-22
> **WalmartSniperLX said:**
> They tend to release unsupported X server builds as well as other extremely early build software packages on release.

That is untrue. Fedora is the home of many X developers, the X stack we ship is very close to what can be found in upstreams release tarballs. If you mean Fedora ships an X stack that occasionally has an ABI that 3rd parties like nVidia doesn't support then yes but that is not Fedoras problem. Nvidia can see the development ongoing, they can see what goes into to which distro releases and they could if they wanted prepare a release that works with what is being shipped. They are even doing work upstream on X, and the last time ABI was broken in a way that was incompatible with the proprietary nvidia driver, those changes were in part commited by an nvidia employee.

Once the nouveau driver gets solid and the underlying stack such as gallium3d gets good this will never be a problem again.

On this front to me one of the most exciting changes in Fedora 11 is switching to the nouveau driver over the nv driver. This is step one in obsoleting the proprietary nvidia driver entirely. The guy Red Hat hired to do this work has been amazingly productive and the driver is in a fine state. It does not do 3d acceleration yet but the list of improvements is growing steadily and the desktop experience out of the box on pretty much any card now is quiet pleasant. I predict that in F12 all nvidia cards supported by nouveau will have KMS (currently only GeForce 8 series cards do with nouveau). 

Along with the work Red Hat and Fedora has been doing on ATI 3d support, DRI2 and MPX, the whole X stack is starting to look very good. I am personally excited to see where we will be a year from now.

---

### Post by Kazade on 2009-04-22
> **gnomeuser said:**
> 
That being said the Anaconda installer should have barked at you for not having a separate /boot on non-ext4. If it did not that is a serious bug.


But surely Fedora doesn't require a separate /boot partition? I installed the Alpha without one.

Part II

OK, so the story so far is I've finally got the Fedora 11 Alpha installed after failing with the beta and snap1 images. The next step is to update the system to the latest packages. We all know how easy this is with Ubuntu, and having some experience with CentOS I know a bit about Yum, anyway, I *shouldn't* need to use it because Fedora has its own graphical updater. A nice orange icon in the tray notified me of the updates (people at the Ubuntu DX team, pay attention! we want our notification icon back!), so I click it, it shows me the list of updates just like update-manager. So I click "Apply"... nothing. Click again and again and again. It does not a thing. Hmm, OK, back to the old way of doing it:
> 
$ su
$ yum -y upgrade

It starts to list stuff, and then I get something similar to this (I can't remember the version or the exact error)
> 
"Cannot resolve circular dependency: glibc-common depends glib-common"


*sigh*. It's just not apt is it? OK, so I do some digging, and found a bug report for this.. apparently an update to "rpm" (or something) caused certain packages to be uninstallable unless you install the upgraded rpm manually. I tried this, and it didn't work, because the upgraded rpm depended on packages I couldn't upgrade to (IIRC). After much more Googling I found some incantation to put in to /etc/yum.conf and finally I could upgrade.

All the 100s of packages downloaded and were installing so I thought I'd browse the Internet while I wait. About 15 mins later I decided to check how the upgrade was getting on so I clicked the terminal window in the window list... and nothing happened. In fact, the whole system had locked up except Firefox. I couldn't click any panels, ALT+F2 didn't work, ALT+Tab didn't work. I couldn't minimize or move the Firefox window. So I went to File->Quit (hoping the FF window would close and show me the terminal) but the desktop just wouldn't repaint. So, after watching the hard disc light not doing much for a while. I chose to hard reset and then boot back into runlevel 3 to complete the upgrade.

When I ran "yum -y upgrade" again yum nicely told me to run yum-complete-transaction. Which I did, it said it needed to run 1479 commands, but nothing seemed to happen... for AGES. After waiting 10 minutes I pressed "Enter" to see if I had been dropped to the prompt and the terminal just hadn't updated (happens sometimes) but it hadn't. After waiting a bit more, yum decided to scroll past 100s of packages at the very bottom it printed something like:
> 
"Continue y/N?"

Now... remember I pressed enter earlier.. and notice that the "n" is a capital. Guess what happened. My "enter" press which happened about 5 minutes before this prompt and suddenly taken effect and chosen the default option of NO. So after waiting 15-20 minutes, I had to go through the whole process again to wait for that prompt for me to say YES. Very irritating.

Finally, eventually, the upgrade completed, I rebooted into my nice shiny pretty Fedora. (Again Ubuntu DX team, pay attention!). Everything seems to work, the update manager is now working correctly, I'm a happy camper.

I scanned the menus and noticed that the LiveCD installed Abiword... not OOo Writer. That's fair enough, I decided to install OOo anyway as that's what I prefer. I installed Synaptic to get some familiarity back, and then searched for Openoffice... except it's not listed. I enabled all the sources in "Software Sources" and it's still not listed.

This is where I am now. I've had an insanely rough ride. I've probably had more pain and suffering installing Fedora than all my pre-release Ubuntu installs combined. 

Here are my learnings from the experience:

1. APT is just far far nicer and (apparently more reliable and faster) than YUM. This follows the experience I've had with other RPM based distros. I don't know the technical limitations and reasonings but why doesn't everyone unite around deb/apt which just seems to work better (for me at least, YMMV)? 

2. Fedora is prettier than Ubuntu. Sorry, it is.

3. Anaconder doesn't like me. I found the partitioning screen more confusing than the Ubuntu installer and 90% of my problems stemmed from bugs in it.

A few questions:
1. How come I can't find OOo in the default repos?
2. How come my KMS didn't work, is it supposed to? I'm using a recent ATI card (R600) I thought was supported (the open source ATI and RadeonHD drivers at least support Xrandr and 2D acceleration with it)
3. Why does my monitor refresh rate go crazy when I attempt to switch to a console (CTRL+ALT+Fx)?

P.S. I *think* I've just had a streak of bad luck with this. Don't let it put you off trying it, now that I have all the updates it seems pretty solid, it's a shame the installer was so broken though. I'll stick with Fedora on my desktop for the near future, it makes a nice change. I already miss apt-get though :(

---

### Post by gnomeuser on 2009-04-22
> **Kazade said:**
> But surely Fedora doesn't require a separate /boot partition? I installed the Alpha without one.


It does if you put /boot on a partition that is not supported by grub. You _cannot_ have /boot on ext4, if you have only a / (under which naturally fits /boot) on ext4 it will fail to boot on Fedora 11. It is the way it works thre because they do not patch grub.

---

