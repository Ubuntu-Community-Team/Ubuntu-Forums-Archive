---
title: "Snaps"
date: 2020-01-25
forum: Ubuntu, Linux and OS Chat
---

### Post by jglen4902 on 2020-01-25
I just want to understand how the snap packages will fit into future versions of an *buntu.  

Specifically, will snaps be installed by default or will there be an opt-out process?

Personally, I am of the opinion that apt using .deb packaging is a superior method of installing software and updates.  I truly have no problem with having snap versions of packages available to users - including me - but I think that being required to use a snap package would be problematic.

---

### Post by jglen4902 on 2020-01-25
So pre-emptive strike "sudo apt autoremove --purge snapd"

When I install 20.04LTS, I'll do that again, until Kubuntu 20.04 (in my case) no longer works.  Then I'll just move on :KS

---

### Post by mörgæs on 2020-01-26
Yes, and if you after that inspect what ```
sudo apt install <packagename>
``` is going to do you will be warned before snapd is reintroduced.

---

### Post by yaminb on 2020-01-26
Obviously people have their preferences, but from what I've read the plan is for 'applications' not part of the 'core' to be distributed by SNAPs.

I am a fairly new Ubuntu user, and so far I have nothing but good experiences with SNAPs (19.10).
One of my most recent was when LibreOffice updated via apt and suddenly I had all these errors. I tried debugging it for a bit, but couldn't get it fixed. I just removed libreoffice and installed it via a SNAP. Everything fixed and the libreoffice SNAP seems to work fine. Where possible, I've removed the apt versions and installed the SNAP ones (that have official SNAPs)

Are there parts of SNAP that worry me?
Yes. I really don't understand why the developers is so insistent on not allowing users to choose not to update. I understand their desire to make sure people keep things up to date. I don't understand not giving advanced users the ability not to.
There's just going to be use cases where that's what people want to do and it just seems like they're driving more people away from SNAP when it's a just a good way to distribute apps.
This post really sums up a really good use case:
[https://forum.snapcraft.io/t/disabling-automatic-refresh-for-snap-from-store/707](https://forum.snapcraft.io/t/disabling-automatic-refresh-for-snap-from-store/707)
I posted there as well.
[https://forum.snapcraft.io/t/disabling-automatic-refresh-for-snap-from-store/707/256](https://forum.snapcraft.io/t/disabling-automatic-refresh-for-snap-from-store/707/256)

I also think it's a little too easy to install 'unofficial' snaps and there's a real danger there for things like malware...

But for me as a conscious home user, these issues don't really apply, so I'm fine with it for now. Worst case, I'll move on to flatpaks if SNAP's policies make things unbearable.

---

### Post by P-I H on 2020-01-26
I use both snaps and flatpaks on Ubuntu 20.04.
The first start of the snaps I use, gnome-calculator and gnome-log, have a little delay and the themes aren't correct. These are problems I can accept.
I'm using these flatpaks, Spotify, Steam, Handbrake, VLC and Kodi. All works very well, but the theme used in Kodi isn't OK.

---

### Post by deadflowr on 2020-01-26
Not support
*Thread moved to **Ubuntu, Linux and OS Chat***

---

### Post by jglen4902 on 2020-01-26
> **deadflowr said:**
> Not support
*Thread moved to **Ubuntu, Linux and OS Chat***
Thanks for moving this to the right forum.

---

### Post by jglen4902 on 2020-01-26
> **yaminb said:**
> Obviously people have their preferences, but from what I've read the plan is for 'applications' not part of the 'core' to be distributed by SNAPs.

I am a fairly new Ubuntu user, and so far I have nothing but good experiences with SNAPs (19.10).
One of my most recent was when LibreOffice updated via apt and suddenly I had all these errors. I tried debugging it for a bit, but couldn't get it fixed. I just removed libreoffice and installed it via a SNAP. Everything fixed and the libreoffice SNAP seems to work fine. Where possible, I've removed the apt versions and installed the SNAP ones (that have official SNAPs)

Are there parts of SNAP that worry me?
Yes. I really don't understand why the developers is so insistent on not allowing users to choose not to update. I understand their desire to make sure people keep things up to date. I don't understand not giving advanced users the ability not to.
There's just going to be use cases where that's what people want to do and it just seems like they're driving more people away from SNAP when it's a just a good way to distribute apps.
This post really sums up a really good use case:
[https://forum.snapcraft.io/t/disabling-automatic-refresh-for-snap-from-store/707](https://forum.snapcraft.io/t/disabling-automatic-refresh-for-snap-from-store/707)
I posted there as well.
[https://forum.snapcraft.io/t/disabling-automatic-refresh-for-snap-from-store/707/256](https://forum.snapcraft.io/t/disabling-automatic-refresh-for-snap-from-store/707/256)

I also think it's a little too easy to install 'unofficial' snaps and there's a real danger there for things like malware...

But for me as a conscious home user, these issues don't really apply, so I'm fine with it for now. Worst case, I'll move on to flatpaks if SNAP's policies make things unbearable.
I get it.  A snap is completely self-contained, and therefore does not require use of common Linux libraries and modules and may duplicate many of these with its own such files in its installed container.  On the plus side, the actual application could be a more advanced version than might be found in a .deb package.  On the minus side, a snap container is inefficient in terms of the space that could be taken up by the libraries and modules that duplicate common files and files found in other snap containers.

I can hear all the arguments about storage is cheap, and the advantages of "up to date" application versions.  What I suspect will happen is that either applications will be installed in the user's home or in /opt and that permissions could become - cloudy.  Or in the case of a multi-user Linux install a lot of duplication of application installations.

Maybe all that is being worked out, or maybe it already has.  In my use case, I am less concerned about the latest and greatest versions of applications.  I only install LTS versions of the distro, anyway.  And maybe the *buntus are on the way to becoming rolling update distros.  And maybe I'm just an old curmudgeon.

---

### Post by CatKiller on 2020-01-27
> **jglen4902 said:**
> Specifically, will snaps be installed by default or will there be an opt-out process?

They're already installed by default. Canonical really want them to succeed, which means they need real-life usage. It's an annoyance, but I can see why they did it. 

> **jglen4902 said:**
> Maybe all that is being worked out, or maybe it already has. 

They've already improved a lot since they were first introduced. Things like being able to write to other locations, for example, seems to be much better than it used to be. 

For the use case of a brand new user that wants all their software to be installed from the same place and kept up to date in one go - even if that software is proprietary or niche - they're already useful. There are some definite limitations and rough edges to them, and I don't use them because I'm comfortable adding PPAs or whatever to get standard packages. Not all users would be, and not all software will ever get a PPA.

---

### Post by Tadaen_Sylvermane on 2020-01-28
I don't use many snaps intentionally. Just the LXD container daemon is in a snap for me. I found this easiest to do as I was testing between Ubuntu & Debian for my server. They needed the same version so it worked out. I don't entirely like the idea of snaps, to much like Windows software for my tastes. But some kind of universal package is going to be required if people want big software on Linux and not "alternatives".

---

### Post by mastablasta on 2020-01-29
> **Tadaen_Sylvermane said:**
> But some kind of universal package is going to be required if people want big software on Linux and not "alternatives".

THIS! 

Number one argument for packaging software like snaps. you package once and you can use that software on any distro of choice. this is something that is much needed in Linux.

---

### Post by Shibblet on 2020-01-29
There are some packages that are only available as snaps.  "Caprine" is the first one that comes to mind...

---

### Post by jglen4902 on 2020-02-01
And this is my concern with snaps.  I understand the concept of containerizing applications in such a way that whatever modules are required for the the application to communicate with the kernel will also be incorporated into the container.  Thus, if multiple snap applications are installed and several of them require the same module, there will be duplication - and in my opinion needless duplication.  But the devs for each snap application will not coordinate module usage, so that problem is not resolvable.  There will likely also be UI presentation differences among them.  The differences may be subtle, they may not be subtle.  I'm hoping it won't be a disaster, and zero integration.

It's almost be more useful if the *buntus moved to a rolling release model - new(er) application software, but some degree of integration.

---

### Post by CatKiller on 2020-02-01
> **jglen4902 said:**
>  There will likely also be UI presentation differences among them.  The differences may be subtle, they may not be subtle.

The Gnome devs are determined to do that with regular packages anyway, so... there's that. :(

---

### Post by mastablasta on 2020-02-03
> **jglen4902 said:**
>  There will likely also be UI presentation differences among them.  The differences may be subtle, they may not be subtle.  I'm hoping it won't be a disaster, and zero integration.


not much of an issue. in windows you get Metro , then you use a GTK app and it will have completelly different UI (looks kind of like old Gnome in Ubuntu) and then you load some KDE4win and get QT apps, again with a different gui. but still it all works relatively well together.

---

### Post by rarial on 2020-02-03
My main worry is that snaps will become the default for everything. They have a time and place (looking at you Chromium) but are a very heavy solution which is needed only in special cases.

---

