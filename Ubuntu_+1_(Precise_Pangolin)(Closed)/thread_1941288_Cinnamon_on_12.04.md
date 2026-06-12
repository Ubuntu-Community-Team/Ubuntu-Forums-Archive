---
title: "Cinnamon on 12.04"
date: 2012-03-15
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by neu5eeCh on 2012-03-15
I've been installing different sessions alongside Unity just to experiment. 

**Gnome-Shell:** Works, although the selection of extensions is minimal. Is this because it's a newer version? On my 64bit laptop, using 11.10, there are almost 12 pages of extensions. I find Gnome Shell, without a hefty does of extensions, _completely_ unusable. 

**Cairo Session:** Also seems to work, though the way Cairo spawns libre-office icons makes Unity's launcher preferable.

**Cinnamon:** I get a desktop but no panel. I have to CTRL-ALT-DELETE to logout. Any ideas?

---

### Post by macstevejb on 2012-03-15
I am having exactly the same problem with the latest version of Cinnamon (1.4)

The desktop appears when selected at login but there is no panel. The only way to get out of it is to press ALT+CTRL+Delete and return to the login screen.

Tried deleting cinnamon applets to get back to vanilla cinnamon but to no avail.

A bug with the Ubuntu precise version methinks?

---

### Post by ricotz on 2012-03-15
Cinnamon/Muffin won't work with cogl/clutter 1.9.x until their forked code-base will catch up with the current gnome-shell/mutter upstream.

---

### Post by grahammechanical on 2012-03-15
Why not a bug with

> with the latest version of Cinnamon (1.4)?

Why do you assume Ubuntu is at fault? Cinnamon is even more under development than Ubuntu Precise Pangolin.

I can get several different desktop environments and User Interfaces from the Precise Software Centre but not Cinnamon. Is this because it is meant to be on Linux Mint and not Ubuntu Precise?

This says nothing about Cinnamon being ready for Ubuntu 12.04

[http://blog.linuxmint.com/?p=1910]("http://blog.linuxmint.com/?p=1910")

How could it be ready, when 12.04 is still under development?

Regards.

---

### Post by sgage on 2012-03-15
> **VTPoet said:**
> I've been installing different sessions alongside Unity just to experiment. 

**Gnome-Shell:** Works, although the selection of extensions is minimal. Is this because it's a newer version? On my 64bit laptop, using 11.10, there are almost 12 pages of extensions. I find Gnome Shell, without a hefty does of extensions, _completely_ unusable. 

**Cairo Session:** Also seems to work, though the way Cairo spawns libre-office icons makes Unity's launcher preferable.

**Cinnamon:** I get a desktop but no panel. I have to CTRL-ALT-DELETE to logout. Any ideas?

Yes, the selection of extensions for the new GS is minimal for now. I agree that it is extensions that make GS usable. 

I don't care for Cinnamon - it is buggy, fragile, and ugly IMO. I find that Gnome Classic works well these days.

Haven't messed with Cairo, so no opinion.

---

### Post by neu5eeCh on 2012-03-15
> **grahammechanical said:**
> I can get several different desktop environments and User Interfaces from the Precise Software Centre but not Cinnamon. Is this because it is meant to be on Linux Mint and not Ubuntu Precise?

Well... I for one am **not** going to go there. :-\" (I've always wanted to use that smily.) I was just curious if anyone else was having this problem. Ricotz's explanation sounds good *to me*. This is BETA. I'm not complaining. Just observing.

About the Gnome Extensions page. Am I right in guessing that the number of available extensions is version dependent? **Edit:*** Never mind, I see that sgage just answered this question.*

---

### Post by toobuntu on 2012-03-15
I suppose you're compiling Cinnamon 1.4 yourself? I'm using 1.2 from the PPA with no problems. I like it, and it works great for me.

```
$ apt-cache policy cinnamon
cinnamon:
  Installed: 1.2.0-2ubuntu1~precise
  Candidate: 1.2.0-2ubuntu1~precise
  Version table:
 *** 1.2.0-2ubuntu1~precise 0
        500 http://ppa.launchpad.net/merlwiz79/cinnamon-ppa/ubuntu/ precise/main amd64 Packages
        100 /var/lib/dpkg/status
```

In general, I have run into issues with multiple desktop environments (or sessions) installed at the same time. Currently, I have gnome-shell, cinnamon, and openbox/lubuntu, but I've almost exclusively been using cinnamon.

---

### Post by neu5eeCh on 2012-03-15
> **toobuntu said:**
> I suppose you're compiling Cinnamon 1.4 yourself? I'm using 1.2 from the PPA with no problems.

No, didn't compile it. I'm using the gwendal-lebihan PPA, is that what you're using?

> ppa:gwendal-lebihan-dev/cinnamon-stable
Installed it from [here]("http://www.webupd8.org/2012/03/cinnamon-14-released-with-new-hot.html"). I'm surprised you're still using 1.2, being that 1.3 has been out for a while?

**Edit: **Oh, never mind. Just saw that you're using a different PPA.

---

### Post by macstevejb on 2012-03-15
grahammechanical:

I never said Ubuntu was at fault!

I simply said that the cinnamon 1.4 version (that I installed from the developer's ppa) must have a bug.

Do not be so quick to get on the defensive.

It is that attitude that turns many people away from Ubuntu.

Yes I use Ubuntu )and am very impressed by Precise) and yes I am happy with Unity.

I just like to try other DE's to compare functionality.

regards :D

---

### Post by wolf_3d on 2012-03-15
I'm having this problem too. Got to use CTRL + ALT + DELETE to log out.

Didn't use any extensions - just changed the panels to Classic so that theres one at the top and bottom.

1.3 was working fine until the 1.4 update arrived.

Can't report the bug through apport since its 3rd party and not a Canonical package.

---

### Post by swizZ8 on 2012-03-16
Clement Lefebvre:

"Whether people updated from 1.3 to 1.4 or kept 1.3 in Ubuntu 12.04, they  can no longer run Cinnamon if they updated Clutter or Gnome. In other  words.. it doesn’t matter whether Precise users updated Cinnamon to 1.4…  the minute they update Clutter/GNOME they can no longer run Cinnamon  (any version)."

---

### Post by neu5eeCh on 2012-03-16
> **swizZ8 said:**
> Clement Lefebvre:

"Whether people updated from 1.3 to 1.4 or kept 1.3 in Ubuntu 12.04, they  can no longer run Cinnamon if they updated Clutter or Gnome. In other  words.. it doesn’t matter whether Precise users updated Cinnamon to 1.4…  the minute they update Clutter/GNOME they can no longer run Cinnamon  (any version)."

Sheesh! Harsh!

Well then... I guess that's that.

---

### Post by swizZ8 on 2012-03-16
Well, it seems not.

Clement also said:

"You’ll need to wait for Gnome Shell 3.4 and a future release of Cinnamon for these desktops to work in Precise again."

---

### Post by jbicha on 2012-03-16
I did notice that muffin was accepted into Fedora (but not Cinnamon yet), and muffin was patched for cogl/clutter 1.9. Obviously Fedora's development release is going to track the development release of GNOME (and even Ubuntu does also).

But if the Cinnamon maintainers don't care and as long as it's not in the normal Ubuntu repositories, what can we do?

---

### Post by neu5eeCh on 2012-03-16
I'm working on a conspiracy theory. Just give me some time.

---

### Post by swizZ8 on 2012-03-16
> **VTPoet said:**
> I'm working on a conspiracy theory. Just give me some time.

:)

---

### Post by kc1di on 2012-03-16
> **VTPoet said:**
> I'm working on a conspiracy theory. Just give me some time.

:o:(

Can't make up my mind should we be scared or amazed

---

### Post by toobuntu on 2012-03-16
Is there a DM or DD out there willing to upload Cinnamon to Debian so a sync can be made and we can have it in the Ubuntu universe before the LTS release?

Edit: Hmm, I see there is an ITP bug for cinnamon filed on the Debian BTS by Carlos C Soto, but no indication he's made any progress getting it into the archive. [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=657395](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=657395)

Edit2: And here's the ITP bug filed for muffin on the Debian BTS by Bas van den Dikkenberg, again, with no indication of any progress getting it into the archive. [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=661270](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=661270)

---

### Post by jeremy on 2012-04-08
Cinnamon is now working again on 12.04:

sudo add-apt-repository ppa:gwendal-lebihan-dev/cinnamon-nightly
sudo apt-get update
sudo apt-get install cinnamon

---

### Post by philinux on 2012-04-08
> **VTPoet said:**
> I've been installing different sessions alongside Unity just to experiment. 

**Gnome-Shell:** Works, although the selection of extensions is minimal. Is this because it's a newer version? On my 64bit laptop, using 11.10, there are almost 12 pages of extensions. I find Gnome Shell, without a hefty does of extensions, _completely_ unusable. 

**Cairo Session:** Also seems to work, though the way Cairo spawns libre-office icons makes Unity's launcher preferable.

**Cinnamon:** I get a desktop but no panel. I have to CTRL-ALT-DELETE to logout. Any ideas?

This might add to the shell extensions.

 [http://ubuntuforums.org/showpost.php?p=11805154&postcount=86](http://ubuntuforums.org/showpost.php?p=11805154&postcount=86)

---

### Post by zika on 2012-04-08
> **jeremy said:**
> Cinnamon is now working again on 12.04:

sudo add-apt-repository ppa:gwendal-lebihan-dev/cinnamon-nightly
sudo apt-get update
sudo apt-get install cinnamonI'm hooked. The whole day I did not even think of getting out in other WM (FluxBox or OpenBox...)...
Great!
One bug: LogOut does not work. But, since I start it via startx it is not a problem...

---

### Post by neu5eeCh on 2012-04-08
OK, it's super cool that Cinnamon now works in 12.04.

However, one problem I have is how all the glass themes make the Mint Menu all but unreadable?

Question:

1.) Shade windows with mouse scroll button -- is it possible?

---

### Post by cariboo on 2012-04-08
> **wolf_3d said:**
> I'm having this problem too. Got to use CTRL + ALT + DELETE to log out.

Didn't use any extensions - just changed the panels to Classic so that theres one at the top and bottom.

1.3 was working fine until the 1.4 update arrived.

Can't report the bug through apport since its 3rd party and not a Canonical package.

Doesn't Mint have a bug reporting mechanism, because that's where the bug belongs.

---

### Post by buzzmandt on 2012-04-08
Indeed, Linux Mint
[https://bugs.launchpad.net/linuxmint](https://bugs.launchpad.net/linuxmint)

It seems Cinnamon is here though
[https://github.com/linuxmint/Cinnamon/issues](https://github.com/linuxmint/Cinnamon/issues)

---

### Post by jeremy on 2012-04-08
> **zika said:**
> I'm hooked. The whole day I did not even think of getting out in other WM (FluxBox or OpenBox...)...
Great!
One bug: LogOut does not work. But, since I start it via startx it is not a problem...

LogOut works fine for me, but I do start cinnamon from LightDM

---

### Post by zika on 2012-04-08
> **jeremy said:**
> LogOut works fine for me, but I do start cinnamon from LightDM
It does not work well with LighDM at all at my place. I'll try again once time permits...
Update: I tried it. I'm writing from Cinnamon session in LightDM. It is not vanilla Cinnamon session. It is Gnome-Cinnamon session if I choose Cinnamon in LightDM Menu. If I choose User defined I get just Cinnamon without Gnome layer. There is a difference. In this Gnome flavored Cinnamon session LogOut works since it is handled by Gnome... ;) In this Gnome flavored Cinnamon session all keyboard shortcuts from Gnome are honored and...
Not to mention that it is faster Cinnamon from startx than from LightDM... ;)
Yes, I have to admit, I'm mixing apples and oranges, to be honest. It seems that Cinnamon is meant to be addition to Gnome. I'm sort of accustomed to FluxBox and OpenBox being (sort of) self-sufficient...
Nevertheless it is a pleasant addition and I think I will spent much time working in it...

---

### Post by buzzmandt on 2012-04-08
just tried it here too, oh my that's nice.

---

### Post by xebian on 2012-04-08
Am using it now, and loving it.  Looks like a better gnome-shell interface.

---

### Post by jeremy on 2012-04-10
I have been using cinnamon again (intensively) for a couple of days now, and the only glitch I have found is minor. Some icons in the taskbar have a white line beside and below them, this does not affect them in any way, just not very pretty.

---

### Post by zika on 2012-04-10
> **jeremy said:**
> Some icons in the taskbar have a white line beside and below them, this does not affect them in any way, just not very pretty.At my place restarting such app resolves that problem.

---

### Post by Luffield on 2012-04-11
Cinnamon now works on 12.04 with the cinnamon-stable PPA, not just the cinnamon-nightly PPA.
Thanks to all involved in making this happen.

---

### Post by jeremy on 2012-04-24
> **Luffield said:**
> Cinnamon now works on 12.04 with the cinnamon-stable PPA, not just the cinnamon-nightly PPA.
Thanks to all involved in making this happen.

the command for this is:

sudo add-apt-repository ppa:gwendal-lebihan-dev/cinnamon-stable
sudo apt-get update
sudo apt-get install cinnamon

---

