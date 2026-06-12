---
title: "AC adapter not properly detected"
date: 2009-07-15
forum: System76 Support
---

### Post by jtappin on 2009-07-15
I've just got a nice shiny new Pangolin laptop,and installed the kubuntu-desktop on it. However I'm finding that the KDE power management tool isn't fully detecting the AC adapter. When the adapter is connected it says it isn't, but reports the battery not discharging. It does report correctly when the adapter is not connected.

The unfortunate effect of this is that the laptop is in powersaving mode, rather than performance. The detection does work with Gnome.

Does anybody have any idea what's going on, and better still how to fix it.

---

### Post by thomasaaron on 2009-07-15
We don't support Kubuntu, but I know there are a lot of 76ers out there with Kubuntu on their Pangolins.

76ers! Have any of you solved this one?

---

### Post by wrender on 2009-07-15
I noticed the same thing in 9.04... though 8.10 was fine....curious.

Hopefully when kde 4.3 is released it may correct that.

---

### Post by jtappin on 2009-07-15
I should just add that I think it is specific to the machine (or to a subset of machines) as I don't have a similar problem with my HP2133 miniNote

---

### Post by Derath on 2009-07-15
The issue is the same on both KDE and Gnome... seems there are a decent amount of power-management issues

---

### Post by thomasaaron on 2009-07-16
> The unfortunate effect of this is that the laptop is in powersaving mode, rather than performance. The detection does work with Gnome.

This is consistent with what I see on our shop Pangolin.

---

### Post by jtappin on 2009-07-16
I do notice that /proc/acpi/ac_adapter is an empty directory, while on my HP machine, there is a subdirectory AC0 which contains a file called state, which contains a line saying whether the adapter is plugged in or not.

---

### Post by gila_monster on 2009-07-25
Okay, I installed kubuntu[1] today, and I too am seeing the "not detecting adapter" problem. Interesting. Drove me nuts for a while trying to figure out why the system kept suspending when I hadn't turned power management on. (I haven't used KDE since about 3.1.)

In the interim, when I power on the pangolin, I just click the battery icon and set it to "performance." We'll see if that sticks, and helps. It may be okay as a workaround.

I went digging in /proc/acpi, and yep, the ac_adapter directory is empty. Shouldn't be, if I recall correctly. Can one of you with GNOME still installed check there and let us know if you have files when plugged in?

Incidentally, I'm running with the 2.6.29 kernel, so if it's a kernel issue of some sort, it's not fixed.

Thanks.

gila

[1] Tom's going to start making fun of me for all the installing I'm doing lately. :)

---

### Post by gila_monster on 2009-07-26
I found some more information on the problem. I haven't tried any of this yet, and probably won't get time to until Thursday. Link goodness:


[http://forum.kde.org/viewtopic.php?f=16&t=30878]("http://forum.kde.org/viewtopic.php?f=16&t=30878")
[http://forum.sabayonlinux.org/viewtopic.php?f=56&t=15873]("http://forum.sabayonlinux.org/viewtopic.php?f=56&t=15873")
[http://kubuntuforums.net/forums/index.php?topic=3102690.0]("http://kubuntuforums.net/forums/index.php?topic=3102690.0")
[Launchpad bugs with long URL]("https://bugs.launchpad.net/bugs/+bugs?field.searchtext=kubuntu+ac+power&orderby=-importance&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=")

One interesting item is that booting from a Kubuntu live CD results in the AC adapter being detected. So something very odd is up with the actual installation. The gist of most responses I saw was to report this as a bug to the Kubuntu team, but it looks as if it's been reported to Launchpad. The folks there had a workaround for the HAL shells that I haven't tried.

The folks at #kubuntu on irc thought it would be fixed with 4.3 in August, and it might be best to wait.

---

### Post by jtappin on 2009-07-27
In response to Gila_monster's last 2 posts.

I do still have gnome on my pangolin. On gnome the battery monitor there gives different wrong information -- it always says there is AC power. It does however switch operating modes according to whether the battery is discharging or not. (i.e. the reason it does what is expected is because it toggles on a different flag).

I'm running KDE 4.3 RC3 and the behaviour is the same as 4.2.4.

---

### Post by jtappin on 2009-07-30
It looks as if this is fundamentally the same problem as that described in [http://ubuntuforums.org/showthread.php?t=1155641]("http://ubuntuforums.org/showthread.php?t=1155641"). With the different behaviours stemming from the Gnome & KDE power managers using different fields and/or making different assumptions in the absence of information.

---

### Post by gila_monster on 2009-07-30
Yep. As mentioned in another post, I tried XFCE, and the power management appears to be working there. Reacts to AC being pulled or added, and flags it accordingly in the appropriate indicators.

---

### Post by 3Miro on 2009-11-15
I have the same problem with Panp4n + Kubuntu 9.10.

KDE 4.3 has a nice widget for manually selecting the power mode, however, it never recognizes the AC adapter as "in." The manual way would be a workaround for now until I can figure it out. Intrepid did not have this problem.

---

### Post by ninezero9 on 2009-12-02
FYI: It may have something to do with the ACPI kerenl module and how it is compiled in.

If it is the same problem: Recompiling the kernel fixed it for me on my laptop in 9.04, I haven't retried yet in 9.10

See here for details:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/412499]("http://bugs.launchpad.net/ubuntu/+source/linux/+bug/412499")

---

### Post by mfraser on 2010-12-04
I'm seeing this with Kubuntu 10.10 and a Toshiba Satellite L300 laptop, but only if the ac adaptor is plugged in after the laptop is running.

If I plug the adaptor in and then turn the laptop on, it detects that it is plugged in.

---

### Post by jtappin on 2010-12-06
> **mfraser said:**
> I'm seeing this with Kubuntu 10.10 and a Toshiba Satellite L300 laptop, but only if the ac adaptor is plugged in after the laptop is running.

If I plug the adaptor in and then turn the laptop on, it detects that it is plugged in.

I think this could be a slightly different issue, on my PanP5, the problem has gone away with the Maverick update.

---

