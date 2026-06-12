---
title: "unsnap: Has anyone used it successfully?"
date: 2022-08-14
forum: The Cafe
---

### Post by TheFu on 2022-08-14
[https://news.itsfoss.com/unsnap-migrate-snap-to-flatpak/](https://news.itsfoss.com/unsnap-migrate-snap-to-flatpak/)
>  Ex-Snap Advocate at Ubuntu Creates a Tool to Help You Migrate from Snap to Flatpak
Canonical’s former Snap advocate develops a tool to help you quickly ditch Snap and use Flatpaks. Interesting… 

There are warnings which scare me a bit. Particularly the warning about data loss, since I'd like to convert lxd from snap.  Flatpaks provide more local control which will likely reduce all the problems I'm having with snap packages refusing to work.

I can see where firefox and chromium users might prefer this too.

I know I could just try it, but I need to setup a new system for lxd to trial unsnap with it to see if the lxd managed containers are removed or not.

---

### Post by Paddy Landau on 2022-08-24
I've not used unsnap, but I have installed flatpak and mostly removed snap.

As an experiment, I even removed snap completely. Everything seemed to work, but I reverted the changes because I'm not anti-snap, and I see no good reason to remove it. (Indeed, there is the occasional app that's available on snap, not flatpak, and seriously out of date on the standard repositories.)

If you are interested in doing the same, I already [posted instructions]("https://ubuntuforums.org/showthread.php?t=2478275&p=14109328&viewfull=1#post14109328") elsewhere.

---

### Post by TheFu on 2022-08-24
unsnap doesn't go into the snap package and make a deb package. 
It just looks for flatpaks of the same name.  Yawn.  At least that's what it seems to do.

The only snap that I want is lxd.  That's it.  Canonical has only released that as a snap since v2.2 ... I think they are on v5.4.x now, so going back really isn't an option.
Fortunately, most of my systems don't need lxd, so the snap subsystem has been removed ... but it comes back from time to time through dependencies, which makes little sense since snap packages don't play well with others.

I miss the days when users had control over their systems.

---

### Post by Paddy Landau on 2022-08-24
> **TheFu said:**
> I miss the days when users had control over their systems.
I think that someone who needs or wants full control needs to go for a distribution targeted at a different demographic. Ubuntu is targeted squarely at those who need systems to "just work" and don't want to tinker — businesspeople, government organisations, non-IT workers, casual users, etc. In other words, "normal" users. Ubuntu suits me fine, but many people chafe at the restrictions.

For your needs, you might want to try a different distribution. Maybe an unofficial Ubuntu derivative such as Mint (many people sing its praises, though I personally don't like it), or steer altogether away from Debian, e.g. Fedora.

It's all about choosing which compromise you prefer. Mine is less control in return for greater stability and great support.

---

### Post by TheFu on 2022-08-24
I want the up-to-date infrastructure provided by Ubuntu Server, but don't care for any GUI in any distro today.  I bring fvwm.
Debian Stable is too old.
Debian Testing is too unstable.
Arch Breaks too much.
Gentoo doesn't actually perform better, even when compiling everything for the specific hardware.
There are really only 5 distros worth my time - they need to be mainstream enough.  I don't want to get updates that break stuff and I don't want a rolling release of any sort. If I wanted to be an alpha tester, I'd run Ubuntu-Next.   I did my time in the 1990s, constantly updating libraries to get new functionality. 

I've run lots of different distros over the decades.  Ended up with Ubuntu Server for most systems and the smallest (size) Ubuntu desktop, since I'm going to purge all the DE and GUI junk anyway.  I used to start with Ubuntu Server, then add a WM.  The problem with that is no wifi or odd-NIC drivers are part of the Server installation (or at least they weren't at the time).  Plus, by using a very light desktop, audio usually works, unlike with servers.

As a server person, I don't expect that distro to be for a non-technical Grandma. I expect to have options and not be forced into using alpha code.

I'm just getting tired of fighting with distros that think change without any improvement is a good thing.  Netplan is an example.  When it was thrown over the wall and included in new installs, it wasn't ready. Took almost 2 yrs to handle what the interfaces file had been handling cleanly for years.  Complaints that the interfaces file was non-standard and difficult for people to use/learn equally apply to yaml.  We still see malformed YAML.  Sometimes it is from the installer!

Why is lxd installed with every 22.04 install?  Makes no sense, except it is a toe hold on mandating snaps.

---

### Post by Paddy Landau on 2022-08-25
> **TheFu said:**
> I'm just getting tired of fighting with distros that think change without any improvement is a good thing.
I've heard this from a lot of people for different distributions. It seems to be a "thing" that some devs do.
> **TheFu said:**
> Why is lxd installed with every 22.04 install?
I've looked at my 22.04 system, and as far as I can tell, it isn't installed. I might be looking in the wrong place: How can I tell?

---

### Post by TheFu on 2022-08-25
> **Paddy Landau said:**
> I've looked at my 22.04 system, and as far as I can tell, it isn't installed. I might be looking in the wrong place: How can I tell?

```
$ snap list
```
Is this a trick question?

I can't provide it right now, since I probably removed lxd, but I have Xubuntu and Server 22.04 installs
Looks like it is part of the cloudinit dependencies on Xubuntu and cloudinit + bash completion on the server.

I remember being unhappy with the added bloat, but like a dog watching a squirrel, there was quickly something else to be unhappy about - the way that the x-buffer select-paste is broken now in 22.04, no doubt as a "security feature".

---

### Post by Paddy Landau on 2022-08-26
> **TheFu said:**
> Is this a trick question?
Ha ha, nope!

I don't have LXD.

[LIST]
[*]There's no command that begins with [FONT=courier new]lxd[/FONT]
[*]It's not listed in [FONT=courier new]apt list --installed 'lxd*'[/FONT]
[*]It's not shown in [FONT=courier new]snap list[/FONT]
[*]It's not shown in [FONT=courier new]flatpak list[/FONT]
[/LIST]
> **TheFu said:**
> I have Xubuntu
I wonder if this points to something? Xubuntu doesn't use LXD. But didn't it used to? Or maybe Lubuntu used to? Maybe you installed it way back, and forgot about it?

---

### Post by TheFu on 2022-08-26
> **Paddy Landau said:**
>  I wonder if this points to something? Xubuntu doesn't use LXD. But didn't it used to? Or maybe Lubuntu used to? Maybe you installed it way back, and forgot about it?

Since they are toy installs only, they were 100% fresh. Not any upgrade.  I haven't installed Lubuntu since they switched to Qt.

---

### Post by TheFu on 2022-08-26
> **Paddy Landau said:**
>  I wonder if this points to something? Xubuntu doesn't use LXD. But didn't it used to? Or maybe Lubuntu used to? Maybe you installed it way back, and forgot about it?

Since they are toy installs only, they were 100% fresh. Not any upgrade.  I haven't installed Lubuntu since they switched to Qt.

---

### Post by Paddy Landau on 2022-08-26
> **TheFu said:**
> Since they are toy installs only, they were 100% fresh. Not any upgrade.  I haven't installed Lubuntu since they switched to Qt.
I can think of two other possibilities. One: It's Xubuntu-specific, because it's not on Ubuntu. Two: You installed something in snap that pulled in LXD as a dependency.

---

### Post by kurt18947 on 2022-08-27
> **Paddy Landau said:**
> I think that someone who needs or wants full control needs to go for a distribution targeted at a different demographic. Ubuntu is targeted squarely at those who need systems to "just work" and don't want to tinker — businesspeople, government organisations, non-IT workers, casual users, etc. In other words, "normal" users. Ubuntu suits me fine, but many people chafe at the restrictions.
....................


This should be a sticky or something. AFAIK Canonical is a for-profit business. They want to appeal to people that use their products for business and might be willing to pay for support. I'm under the impression that Snap is really targeted toward IOT and Server applications, not desktops. I've read that FlatPak and Snap can coexist and my very limited experience supports that. I have a standard Ubuntu installation with Libre Office and Zoom Flatpaks. I have yet to see any problems or conflicts with those two apps.

I've read that proprietary software vendors tend to favor Snap over Flatpak. I would not be surprised if those proprietary vendors prefer a single source repository (like Snap) over Flatpak's support for multiple repositories. There aren't multiple Microsoft or Adobe software sources for example. I'm not in the business and can't cite any examples to support my statements, just "what I read in the papers".

---

### Post by Paddy Landau on 2022-08-27
> **kurt18947 said:**
> Canonical is a for-profit business.
That's correct. It's how Canonical pays for Ubuntu.
> **kurt18947 said:**
> FlatPak and Snap can coexist…
Again, that's correct. I've been using both for quite some time in both 20.04 and 22.04. Appimages are the same. Every snap, flatpak and appimage is entirely self-contained, so you can actually have the same program four times — snap, flatpak, appimage and deb — and they'll run independently of each other. (Disclaimer: I've not tested appimage, but I have tested the others.)
> **kurt18947 said:**
> I've read that proprietary software vendors tend to favor Snap over Flatpak.
I think that you'll find that some of them prefer one, some the other, and some neither. Zoom uses flatpak, not snap; Firefox snap, not flatpak; Skype both; GIMP both, although snap is usually a little out of date; Google Chrome neither. And so on.
 > **kurt18947 said:**
> Flatpak's support for multiple repositories.
It's true that flatpak supports multiple repositories (as does the DEB method), but so far I have used only flathub, as it seems to be the preferred repository, at least from what I can tell.

---

### Post by TheFu on 2022-08-27
I use AppImages.  They don't have any unwanted constraints that get in the way and they don't hate NFS or HOME directories outside /home/ like snap does.

---

### Post by Paddy Landau on 2022-08-27
> **TheFu said:**
> … they don't hate NFS or HOME directories outside /home/ like snap does.
This is my only gripe with snap: you can't change the security model at all. For example, snap gedit is unusable if you edit or even just view system files with it. I can't even edit my own scripts in [FONT=courier new]~/bin[/FONT].

flatpak, fortunately, does provide an override. You can reduce or increase the [security model]("https://docs.flatpak.org/en/latest/sandbox-permissions.html") to a fine level separately for every app. The GUI method is [Flatseal]("https://flathub.org/apps/details/com.github.tchx84.Flatseal"), but there's also a CLI for it.

---

### Post by agentl074 on 2022-08-28
... And with APT, you should be able to install anything by hand ;)

---

### Post by Paddy Landau on 2022-08-29
> **agentl074 said:**
> ... And with APT, you should be able to install anything by hand ;)
Well, yes, but they can be out of date.

---

### Post by TheFu on 2022-08-29
> **Paddy Landau said:**
> Well, yes, but they can be out of date.

The same applies to all packaged software, regardless of packaging.  There are lots of abandoned snaps and flatpaks and appimages and rpms too.  Plenty of old setup.exe on other platforms and the costly hardware people with the BSD-based OS are famous for not updating Unix/GNU stuff for years too.

Out of date usually means "unsupported", but with a supported, patched, release from Canonical, we know and trust that those packages get security updates, so they aren't exactly out of date, if if they are older versions.  A subtle, but critical difference.

I have a snap that hasn't been updated in nearly 2 yrs.  
```
$ snap info xyz-123-fake-package-to-protect-the-guilty
...
refresh-date: 2020-07-26
channels:
  latest/stable:    1.1.0-Beta-2 2019-07-12 (4) 165MB -
  latest/candidate: 1.1.0-Beta-2 2019-07-12 (4) 165MB -
  latest/beta:      1.1.0-Beta-2 2019-07-12 (4) 165MB -
  latest/edge:      1.1.0-Beta-2 2020-10-19 (5) 168MB -
installed:          1.1.0-Beta-2            (4) 165MB -

```
I think that makes the point.

---

