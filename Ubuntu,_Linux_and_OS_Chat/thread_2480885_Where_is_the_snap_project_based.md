---
title: "Where is the snap project based?"
date: 2022-11-13
forum: Ubuntu, Linux and OS Chat
---

### Post by bitrat2 on 2022-11-13
Hi,

every day, I'm tempted to run debian or even slackware, just to escape from the endless mill of desktop 'innovation' that characterises the Linux experience.  I've learned to fine tune a lot of systems over the years, from VMS and Solaris to Raspbian.  It's no longer something that engages me.  I don't have a lot of experience with linux window managers, but I think I'll look at icewm or maybe awesome.  I want a system I can understand and modify to suit my needs, not one that looks pretty and does everything for me, until it doesn't.

***But***, it's nice to just install ubuntu and have everything working out of the box.  

The problem is, the more bundled things are, the more difficult it is to figure out how they work and how to fix them when they break.

Snap seems like just another level of irritation.  Every time I ask my system about disks, I have to *[FONT=courier new]grep -v loop[/FONT]* to get rid of snap cruft.  I keep finding my personal data in the snap directories.  Why?  Sometimes snap apps take forever to launch...  

Obviously I'm impatient and unwilling to learn new concepts.  So I decided maybe I should at least learn how to use snap, before being too critical.  But googling 'snap' is like googling 'brown'.  Where is the project based, and what is the best introduction to it's inner workings?

Also, can I install Ubuntu without installing snap?  For that matter, can I install a bare bones Ubuntu, with no default apps, but with devices?  Sometimes it feels like setting up a new phone, removing the OEM apps and installing better ones.

UPDATE: Found some [info]("https://phoenixnap.com/kb/install-snap-ubuntu") here, and [this]("https://ubuntu.com/blog/whats-in-a-snap") page has some good stuff, but I'm still interested in responses to my rant.  :)  Basically, I'd like to install any snaps on my system myself, not have it done for me, by default, behind my back.

Ok, I've found snapcraft.io

I'm still interested to know, for example, the best way back up config info for snap apps.  Is it necessary to examine each snap individually for this kind of stuff?

Potential benefits of using snap:
- high resolution software updates.
- shared libraries can actually be shared

Are there any other benefits of snap, or reasons not to use AppImages instead?  

To avoid 'dll hell' on Windows, I usually statically linked my own programs and copied 3rd party/runtime dll's into a program directory along with the main binary.  That made the AppImage approach instantly appealing.  However, maintaining updates  was one downside.  For non network connnected apps (*very* unfortunately a rarity these days) constant updates are of limited interest most of the time.

---

### Post by MAFoElffen on 2022-11-13
Snap was developed by Canonical. 

I've learned to live with the Snap Store and also with Flatpak. (In supporting them to my customers, and with most of my own machines.)

I know how to uninstall Snap... But if you are running Ubuntu or one of it's flavors, it is harder and harder to ignore Snap, and keep it at bay. More and more applications are being moved off apt. Some of those might seem like they are there, are Snaps under-the-covers.

I have an Ubuntu derivative flavor project, the Ama-Gi Project, where I had to really look for application's that I wanted, that were no longer in the Apt repositories. I originally put it together for Ubuntu 12.04 LTS and started updating it for 20.04 and 22.04 LTS. Some of the applications I had were no longer available in Apt. Some were no longer available at all, and I had to look for replacements. I can say that this affected the default apps that I chosen for my distribution, even though it is just a Live Image Environment (L.I.E.). For that, I don't want the Snap Store. It's purpose is to diagnose and rescue an Installed Linux System that may already be on compromise hardware... I wanted it to be lightweight and fast. So some app's that were no longer in Apt and I wanted them to still be there, I had to compile from source. 

If you like to live on the edge and don't mind a challenge, entertainment abounds to keep people busy.

---

### Post by grahammechanical on 2022-11-13
I guess that snapcraft.io is the official home for snaps. Look beyond snapcraft being the snap store.

[https://snapcraft.io/](https://snapcraft.io/)

The latest Ubuntu installer offers an minimal install with just a web browser and some utilities. 

Regards

---

### Post by ian-weisser on 2022-11-13
> **bitrat2 said:**
> I keep finding my personal data in the snap directories.

If you discover personal data is being stored in the /snap directory, please file a bug report. Personal data should be in /home/$USER/.snap/, where you have control over it.

> **bitrat2 said:**
> Sometimes snap apps take forever to launch...

Several bugs that caused lengthy launch times were recently fixed. If you discover a snap that demonstrably takes longer to launch than a corresponding deb, please file a bug report.

> **bitrat2 said:**
> Also, can I install Ubuntu without installing snap?

If you mean "not install snaps packages", then Ubuntu Server and its associated cloud images lack snap packages. That will change when the printing stack (CUPS) moves to a snap package in 23.04 or 23.10
If you mean "a desktop environment without snapd", then the answer is already No. The Firefox snap is included with Ubuntu Desktop starting in 22.04

> **bitrat2 said:**
> I'd like to install any snaps on my system myself, not have it done for me, by default, behind my back.

There's no intent to surprise people, nor to be secretive. 
Ubuntu remains exactly what it says on the tin.

Ubuntu has been making default changes since 2005. Numerous applications, desktop environments, etc. All changed. Multiple times.

Changes are clearly described in the Release Notes.
Most changes are discussed endlessly in Discourse and on the mailing lists for months (years!) before implementation.
Most changes occur in the interim (6-month) releases of Ubuntu, giving plenty of notice before the next LTS.

> **bitrat2 said:**
> the best way back up config info for snap apps

Your configs should be in /home/$USER/.snap/

> **bitrat2 said:**
> I'm still interested in responses to my rant.

Life = Change. Whether or not your actions in response to change are constructive is entirely up to you.
There will be more change tomorrow.

---

### Post by bitrat2 on 2022-11-13
Thanks everybody.  All good thoughts.

[This]("https://forum.snapcraft.io/t/snap-documentation/11127") forum topic looks promising, but I've yet to find any documents explaining the basic concepts and architecture of snap.

I'll register on that forum and ask some questions there, but I'm still happy to hear more ideas here.

---

### Post by ajgreeny on 2022-11-14
If you are totally anti-snap you could consider moving to Mint which as things stand has promised not to include and use snaps by default.

Some users consider Mint to be just an improved version of Ubuntu, not strictly true, but it does use Ubuntu repos.
I use Mint-Xfce sometimes but prefer Xubuntu, though I do remove all snaps and the whole snap infrastructure, installing chromium from a PPA and Firefox using the .tar.gz download from Mozilla.

Your choice! Thats the great thing about Ubuntu and Linux in general.

---

### Post by tessawong on 2022-11-14
> **grahammechanical said:**
> 
The latest Ubuntu installer offers an minimal install with just a web browser and some utilities. 

What's the URL to download it please? Thanks.

---

### Post by ajgreeny on 2022-11-14
> **tessawong said:**
> What's the URL to download it please? Thanks.

Same .iso file  as normal I believe; it is simply a choice at installation, though I've never gone down that road.

---

### Post by slickymaster on 2022-11-14
Not a support thread.

*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by bitrat2 on 2022-11-14
> **ajgreeny said:**
> If you are totally anti-snap

I'm not anti-snap, I'd just like it to be more opt-in.

> **ajgreeny said:**
> I do remove all snaps  and the whole snap infrastructure

Can I just disable snapd with systemctl?

---

### Post by #&amp;thj^% on 2022-11-14
> **bitrat2 said:**
> 
Can I just disable snapd with systemctl?

NO! This will break a working OS, I prefer to be snap-less.....but that's an individual choice

---

### Post by bitrat2 on 2022-11-15
> **ajgreeny said:**
> though I do remove all snaps and the whole snap infrastructure

How do you do this?

---

### Post by ajgreeny on 2022-11-15
I run command **snap list** then one by one remove all the snaps listed, ending with snapd.
Finally I remove the snapd deb package as well with **sudo apt purge snapd**.

---

### Post by zebra2 on 2022-11-15
I'm using Ubuntu 23.04 which is early in development. My system is running default "out of the box".  So far my system is running with snap and is flawless.  My deb apps install from the Snap Store "Ubuntu Software" without a problem.  Some apps have both the snap and deb installation choice. In this case I choose the Snap version. 

In the past those of us that wanted a sandboxed app had to use Firejail or something like it.  This was a very technical experience with many options and chances to be wrong.  It my case I just used the default Firejail setup which in some cases created problems.  

In any case, solutions to the security problem other than snap have been there whether the end user was aware or not.  Canonical in its journey to creating a mainstream linux distro had to provide security by default instead of by user choice. In this case the choice was Snap. I personally don't even think about it on a day to day basis with my current install.  It just works. 

It might be of interest to you that  Microsoft is tackling the same problem in much the same way. The default install on a Windows system is Windows 11S.  The S stands for Secure applications downloaded from the Microsoft App Store only. In my case I wanted a very cheap Windows computer to allow me to avoid a dual boot.  I just bought a new Windows 11S 15'" Laptop for $178.  I wanted to install all of my Foss apps on the system and hence deleted the MS clouded backup and all of the other crap that comes with Windows. It works just fine but the "S" disappeared since the Foss apps didn't install from the Windows Store.  Windows 11 didn't keep me from installing the apps but by going outside of the secure download store I assumed the S responsibility. 

Hence what Canonical is doing seems to me to be a needed industry standard.  We can cut Canonical out of the loop but at that point we are on our own. PS, and that is just fine with me.

---

### Post by iamjiwjr on 2022-11-15
> **bitrat2 said:**
> How do you do this?

1. Remove Snaps


sudo snap remove --purge firefox
sudo snap remove --purge snap-store
sudo snap remove --purge gnome-3-38-2004
sudo snap remove --purge gtk-common-themes
sudo snap remove --purge snapd-desktop-integration
sudo snap remove --purge bare
sudo snap remove --purge core20
sudo snap remove --purge snapd


sudo apt remove --autoremove snapd


2. Create an apt preference file in /etc/apt/preferences.d/ and create a new preference file to stop snap. Create a new file called nosnap.pref in /etc/apt/preferences.d/


sudo gnome-text-editor /etc/apt/preferences.d/nosnap.pref


And add the following lines, then save the file.
Package: snapd
Pin: release a=*
Pin-Priority: -10

3. Presumably one would follow with installing synaptic, gdebi, gnome-software, flatpak, and gnome-software-plugin-flatpak. Add flathub repo and reboot.

---

### Post by VMC on 2022-11-15
> **iamjiwjr said:**
> 1. Remove Snaps


sudo snap remove --purge firefox
sudo snap remove --purge snap-store
sudo snap remove --purge gnome-3-38-2004
sudo snap remove --purge gtk-common-themes
sudo snap remove --purge snapd-desktop-integration
sudo snap remove --purge bare
sudo snap remove --purge core20
sudo snap remove --purge snapd


sudo apt remove --autoremove snapd
...
What is your output of ```
[FONT=monospace][COLOR=#000000]systemctl status snapd[/COLOR][/FONT]
```

---

### Post by TheFu on 2022-11-15
> **ajgreeny said:**
> If you are totally anti-snap you could consider moving to Mint which as things stand has promised not to include and use snaps by default.
 

+1

Ubuntu Server 20.04 started including snap packages by default, even in the minimal install.  It is really sad.

---

### Post by iamjiwjr on 2022-11-15
&#9675; snapd.service
     Loaded: masked (Reason: Unit snapd.service is masked.)
     Active: inactive (dead)

---

### Post by poorguy on 2022-11-15
> **ajgreeny said:**
> Same .iso file  as normal I believe; it is simply a choice at installation, though I've never gone down that road.

That's exactly what it is a choice ***normal install*** or ***minimal install ***it's what I use because I don't want and need all of the software that is installed by default at the time of install and by the way Snap still gets installed regardless of your choice.

I have no problem with Snaps once I got used to them and learned a little bit about them can't say nothing bad about them like most stuff thats new or a change just gotta get used to them which ain't easy for some users.

---

### Post by bitrat2 on 2022-11-15
> **poorguy said:**
> I have no problem with Snaps once I got used to them and learned a little bit about them

Can you suggest something like a white paper that describes the basic concepts and motivations underlying the snap architecture?  I've searched but all I can find is specific instructions explaining how to do specific tasks.

---

### Post by #&amp;thj^% on 2022-11-15
> **iamjiwjr said:**
> 1. Remove Snaps


sudo snap remove --purge firefox
sudo snap remove --purge snap-store
sudo snap remove --purge gnome-3-38-2004
sudo snap remove --purge gtk-common-themes
sudo snap remove --purge snapd-desktop-integration
sudo snap remove --purge bare
sudo snap remove --purge core20
sudo snap remove --purge snapd


sudo apt remove --autoremove snapd


2. Create an apt preference file in /etc/apt/preferences.d/ and create a new preference file to stop snap. Create a new file called nosnap.pref in /etc/apt/preferences.d/


sudo gnome-text-editor /etc/apt/preferences.d/nosnap.pref


And add the following lines, then save the file.
Package: snapd
Pin: release a=*
Pin-Priority: -10

3. Presumably one would follow with installing synaptic, gdebi, gnome-software, flatpak, and gnome-software-plugin-flatpak. Add flathub repo and reboot.

+1
Also after you'll see:
```
systemctl status snapd
&#9675; snapd.service
     Loaded: masked (Reason: Unit snapd.service is masked.)
     Active: inactive (dead)

```
I find this the best method so far, and I use this.

---

### Post by bitrat2 on 2022-11-15
> **iamjiwjr said:**
> 1. Remove Snaps
.
.
.


Thank you.  I don't imagine this is the way I'll go, but it does add to my understanding.  

My current 'desktop' machine actually functions more like a server.   Since I have a spare NUC, I may use that as my desktop, with a nice new shrink wrapped Ubuntu 22.04 LTS, complete with snap.  The old 'desktop' can run debian, or maybe another distro.  This isn't anything against snap, it's just that it makes my system feel like a monolithic black box, and I like it to feel more like a toolbox.

---

### Post by #&amp;thj^% on 2022-11-15
> **bitrat2 said:**
> Can you suggest something like a white paper that describes the basic concepts and motivations underlying the snap architecture?  I've searched but all I can find is specific instructions explaining how to do specific tasks.

Well here is a good start: [https://www.techrepublic.com/article/why-canonical-views-the-snap-ecosystem-as-a-compelling-distribution-agnostic-solution/](https://www.techrepublic.com/article/why-canonical-views-the-snap-ecosystem-as-a-compelling-distribution-agnostic-solution/)

---

### Post by TheFu on 2022-11-15
> **bitrat2 said:**
> Thank you.  I don't imagine this is the way I'll go, but it does add to my understanding.  

My current 'desktop' machine actually functions more like a server.   Since I have a spare NUC, I may use that as my desktop, with a nice new shrink wrapped Ubuntu 22.04 LTS, complete with snap.  The old 'desktop' can run debian, or maybe another distro.  This isn't anything against snap, it's just that it makes my system feel like a monolithic black box, and I like it to feel more like a toolbox.

There are plenty of reasons to dislike snap packages, especially on servers.  For a desktop, snaps have a role for quickly changing security updates and keeping the distro team out of the way for those updates getting to many end-users.  The biggest issues with snaps are documented in these forums multiple times.  If you don't run into those issues, great.  There are a number of snap design choices that are incompatible with the Unix philosophy, which can make them incompatible for many situations.  My main issue is the complete lack of local controls over the containment that is mandated in snap packages.  

Flatpaks allow local control while still having constrained environments.  AppImages don't provide any constraints.
When the constraints of snaps or flatpaks get in the way of workflows, having local control to remove those is important.  With Snaps, only workflows that the specific snap package team decided to support might possibly work.  Unix is supposed to provide unlimited power to users, where it makes sense.  The OS isn't supposed to get in the way and completely prevent new, genius, workflows. Snaps get in the way, sadly.

---

### Post by bitrat2 on 2022-11-15
> **TheFu said:**
> There are plenty of reasons to dislike snap packages...

Thanks, I'm getting a better picture now.

How many snap packages that are based on open source software are themselves fully open source?  I mean, can I get the relevant projects and rebuild the snaps myself?  I'm happy for proprietary software to build and distribute closed source snaps, but I'd be less happy to see open source packages redistributed using a de facto closed source model.  Feels a bit Androidy...

---

### Post by TheFu on 2022-11-15
> **bitrat2 said:**
> Thanks, I'm getting a better picture now.

How many snap packages that are based on open source software are themselves fully open source?  I mean, can I get the relevant projects and rebuild the snaps myself?  I'm happy for proprietary software to build and distribute closed source snaps, but I'd be less happy to see open source packages redistributed using a de facto closed source model.  Feels a bit Androidy...

Unknown.  Every snap that I've seen is F/LOSS.  Most have alternative distribution/packages, like Mozilla has their own PPAs which work great for Ubuntu if you can live without the latest version.
OTOH, there are some F/LOSS projects that switched to snap-only distribution.  The lxd ( Canonical's Linux Container manager ) project is snap-only and gets installed on servers even when not requested.  I happen to use lxd/lxc, but really wish it wasn't a snap, since snaps don't work on many of my systems, unless I create local user accounts and only use HOME in /home/ for those users.

For example, these are run on the same system, from my HOME directory:
```
$ snap list
Name      Version      Rev    Tracking       Publisher     Notes
core18    20221027     2620   latest/stable  canonical&#10003;    base
core20    20221027     1695   latest/stable  canonical&#10003;    base
lxd       5.7-c62733b  23889  latest/stable  canonical&#10003;    -
snapd     2.57.4       17336  latest/stable  canonical&#10003;    snapd
wormhole  0.12.0       349    latest/stable  snapcrafters  -

$ lxc list
Command 'lxc' is available in '/snap/bin/lxc'
The command could not be located because '/snap/bin' is not included in the PATH environment variable.
lxc: command not found

$ /snap/bin/lxc list
Sorry, home directories outside of /home are not currently supported. 
See https://forum.snapcraft.io/t/11209 for details.

```
They provide a completely unworkable workaround.  This problem has been known since 2017, still they hard code /home/{username} which is completely unreasonable.

---

