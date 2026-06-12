---
title: "Ubuntu needs some kind of package revisor."
date: 2009-11-02
forum: The Cafe
---

### Post by liquidbee on 2009-11-02
**Example:** [http://revisor.fedoraunity.org/]("http://ubuntuforums.org/Revisor%20from%20Fedora")

There's no universal set of packages, which would be as good for me as for others. Why doesn't Ubuntu LiveCD / DVD contain some kind of package revisor (  so I could choose, what to install and what not ) ?

What would such a feature mean to devs ? Would it require them to change the CD structure and make other modifications, which might lead into other problems ?

---

### Post by FuturePilot on 2009-11-02
The thing is, Ubuntu tries to target the largest possible user base. In this case that's usually new users. Most new Linux users probably won't care what gets installed by default or become confused by such option in the installer. The goal of Ubuntu's installer is to ask as few questions as possible. This would add unnecessary steps to the installer.

---

### Post by liquidbee on 2009-11-02
> **FuturePilot said:**
> The thing is, Ubuntu tries to target the largest possible user base. In this case that's usually new users. Most new Linux users probably won't care what gets installed by default or become confused by such option in the installer. The goal of Ubuntu's installer is to ask as few questions as possible. This would add unnecessary steps to the installer.

As an example, when you install Fedora, you don't see it unless you know where it is. I mean, no one forces you to choose what to install and what not - it just includes such a feature, which can be used in cases if you need it ( and I think many of use would find it useful ).

---

### Post by Crunchy the Headcrab on 2009-11-02
> **liquidbee said:**
> As an example, when you install Fedora, you don't see it unless you know where it is. I mean, no one forces you to choose what to install and what not - it just includes such a feature, which can be used in cases if you need it ( and I think many of use would find it useful ).

I absolutely love the Fedora installer.  I can live without it, so I wouldn't say Ubuntu NEEDS a feature like that, but it would be nice.

---

### Post by xuCGC002 on 2009-11-02
maybe they could add a ubiquity-revisor, that is not visible in the main menu/desktop, only used by pressing Alt-F4 or similar methods of launching software.

---

### Post by slakkie on 2009-11-03
They have such a thing. The minimal installation CD has it and if not mistaken, the alternate CD also.

The LiveCD just installs a workable desktop. If you don't want it, use different ways of installing Ubuntu or just upgrade :)

---

### Post by liquidbee on 2009-11-03
> **slakkie said:**
> They have such a thing. The minimal installation CD has it and if not mistaken, the alternate CD also.

The LiveCD just installs a workable desktop. If you don't want it, use different ways of installing Ubuntu or just upgrade :)

If it's true, how do I access it ( eg., from the alternate cd ) ?

---

### Post by earthpigg on 2009-11-03
> **liquidbee said:**
> If it's true, how do I access it ( eg., from the alternate cd ) ?

its written somewhere on the first screen you see after picking language. 'modes' i think... press f4 or somesuch. i dont have it memorized because... well, i guess i just read whats on the screen lol. then pick command line install.

PANIC: you will have to type one command in a terminal and then reboot once to get away from the terminal.

```
sudo apt-get install xorg gdm gnome-core synaptic
```
(replace gnome-core with your DE of choice.)

but, i suspect people interested in super custom installs aren't afraid of the terminal anyways.

:D

---

### Post by FuturePilot on 2009-11-03
> **liquidbee said:**
> If it's true, how do I access it ( eg., from the alternate cd ) ?

During the installation it will bring up a selection of different groups of packages along with an option to manually select other packages to install.

---

### Post by liquidbee on 2009-11-03
> **earthpigg said:**
> its written somewhere on the first screen you see after picking language. 'modes' i think... press f4 or somesuch. i dont have it memorized because... well, i guess i just read whats on the screen lol. then pick command line install.

PANIC: you will have to type one command in a terminal and then reboot once to get away from the terminal.

```
sudo apt-get install xorg gdm gnome-core synaptic
```(replace gnome-core with your DE of choice.)

but, i suspect people interested in super custom installs aren't afraid of the terminal anyways.

:D

Check Revisor - Ubuntu doesn't have such a feature ( at least I haven't found one .. that's why I opened this thread ). All you can do is to perform a command-line installation and then install/configure everything manually, which isn't really what Revisor does. The idea is to have a set of default applications ( + a few additional ones, if they fit into the CD/DVD ) which can be customized ( eg., I don't need Transmission but I know that I need Ruby .. why not to give me a chance to have what I want by *default* ? ).

> **FuturePilot said:**
> During the installation it will bring up a selection of different groups of packages along with an option to manually select other packages to install.

[COLOR=Gray][ shutting down my PC and checking whether this function really exists ][/COLOR]

---

### Post by SaintDanBert on 2012-05-11
> **liquidbee said:**
> As an example, when you install Fedora, you don't see it unless you know where it is.
...


This is true for a lot of distributions including *-buntu.  However, like every disto, I get a lot of parts that I don't know that I have and may not ask for if I knew what they did.  There are others that I get that I have no use for.
[list]
[*]fonts for foreign languages
[*]fonts that are essentially identical to other fonts
[*]apps for detailed bit-picking
[*]apps for detailed music and video picking
[*]three or more apps that deliver similar features
[*]multiple desktop environments
[/list]

I've been a developer and server admin for 30+ years and understand the installer problem space. A quick-install with a load of parts makes sense for a lot of reasons.  Perhaps give us a better tool(s) to prune and tailor the distro once the initial install media stops spinning.

~~~ 8d;-/ Dan

---

### Post by cariboo on 2012-05-11
I'm closing this thread, as the last time the op accessed the forum, was a week after he created this thread.

---

