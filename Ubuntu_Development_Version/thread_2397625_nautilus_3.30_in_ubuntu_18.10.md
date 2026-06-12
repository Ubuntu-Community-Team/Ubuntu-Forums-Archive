---
title: "nautilus 3.30 in ubuntu 18.10"
date: 2018-08-01
forum: Ubuntu Development Version
---

### Post by ya-paulle on 2018-08-01
Will nautilus 3.30 be available in ubuntu 18.10 ?

---

### Post by PaulW2U on 2018-08-01
> **ya-paulle said:**
> Will nautilus 3.30 be available in ubuntu 18.10 ?
As of late June, the version of Nautilus to ship with 18.10 hadn't been decided on by the Ubuntu Desktop team. 

I haven't read anything since to suggest that a decision has now been made.

---

### Post by harry332 on 2018-08-02
At least the Gnome 3.30 is beginning to show.
There is gnome-desktop3 and mutter version 3.29.90 in proposed repo now.

---

### Post by amano on 2018-08-03
Gnome Shell 3.29.90 should be in there soon as well. Still based on mozjs52 as I see.

The new glib2.0 seems to be packaged as well, incorporating the per-desktop-overrides patch for the first time.

I wonder if there are plans to ship pipewire: If not by default then perhaps in the archive at least?

---

### Post by jbicha on 2018-08-03
pipewire is blocked by [this issue]("https://github.com/PipeWire/pipewire/issues/60").

---

### Post by amano on 2018-08-04
GNOME are really shaking out their long standing issues with 3.30: GDM was just updated to not stay in the background and hog your memory: [https://github.com/GNOME/gdm/commit/c0188a7030f2e629eefc47eeae1aa8313b7fda1b](https://github.com/GNOME/gdm/commit/c0188a7030f2e629eefc47eeae1aa8313b7fda1b)

We are possibly going to see that in Ubuntu next week. The fix is already included in GNOME 3.29.90.

---

### Post by amano on 2018-08-14
The pipewire blocking bug seems to be fixed now. I hope that we we will see a Pipewire 0.2.3 version soonish (tm) now and having it migrate to the Debian/Ubuntu world...

---

### Post by jbicha on 2018-08-15
[Seb Bacher said]("https://trello.com/c/oD8wcMJO/97-desktop-icons-next-generation#comment-5b73f41d51d79879bea4951f") although progress is being made on a desktop icons replacement, nautilus 3.28 (or newer) is unlikely to land in Ubuntu before 19.04.

---

### Post by ya-paulle on 2018-08-16
> **jbicha said:**
> [Seb Bacher said]("https://trello.com/c/oD8wcMJO/97-desktop-icons-next-generation#comment-5b73f41d51d79879bea4951f") although progress is being made on a desktop icons replacement, nautilus 3.28 (or newer) is unlikely to land in Ubuntu before 19.04.

So I hope there will be an option to run ubuntu 18.10 with nautilus 3.30. I never liked the desktop icons (before I always used ubuntu-gnome).

---

### Post by MyMurry on 2018-08-23
> **jbicha said:**
> [Seb Bacher said]("https://trello.com/c/oD8wcMJO/97-desktop-icons-next-generation#comment-5b73f41d51d79879bea4951f") although progress is being made on a desktop icons replacement, nautilus 3.28 (or newer) is unlikely to land in Ubuntu before 19.04.

There is now a gnome extension:
[https://csorianognome.wordpress.com/2018/08/22/desktop-icons-goes-beta/](https://csorianognome.wordpress.com/2018/08/22/desktop-icons-goes-beta/)

---

### Post by ya-paulle on 2018-08-23
> **MyMurry said:**
> There is now a gnome extension:
[https://csorianognome.wordpress.com/2018/08/22/desktop-icons-goes-beta/](https://csorianognome.wordpress.com/2018/08/22/desktop-icons-goes-beta/)

Once this extension is ready, there should be no need for Ubuntu using an outdated version of nautilus.
Eveb&#324; better every has the choice to use desktop icons or not.

---

### Post by dino99 on 2018-09-28
@Jeremy

what's up ?  [https://github.com/PipeWire/pipewire/commit/60d4473e7b7fa016a95db3d39451ee525758a9c2](https://github.com/PipeWire/pipewire/commit/60d4473e7b7fa016a95db3d39451ee525758a9c2)

that should unlock the previous problem.

---

### Post by jbicha on 2018-09-28
Are you looking [for this]("https://launchpad.net/ubuntu/+source/pipewire")?

---

### Post by dino99 on 2018-09-28
> **jbicha said:**
> Are you looking [for this]("https://launchpad.net/ubuntu/+source/pipewire")?

Seems the same upgrade

So what stop the nautilus upgrade to 3.30 now ?

---

### Post by amano on 2018-09-29
I guess that the feature freeze is the main stopping point. The "desktop icon" extension would probably have the be "MIR"ed first before being merged to "main" as well.

The extension isn't fully featured yet either and in rather heavy flux currently (big thanks go to Sergio Costas). You still cannot rename files on the desktop and so on...

I guess that a "MIR" is going to be filed for it sooner or later.

Your only hope for nautilus 3.30/3.30.1 would probably be that you succeed in nagging Jeremy Bicha to compile and upload  a vanilla nautilus 3.30(.x) to the gnome3 staging PPA. If there is any hope at all ;)

---

### Post by jbicha on 2018-09-29
One big blocker is that Ubuntu Budgie is a supported Ubuntu flavor and they use Nautilus for desktop icons. We can't break other flavors this late in the release cycle.

---

### Post by ya-paulle on 2018-10-05
> **amano said:**
> I guess that the feature freeze is the main stopping point. The "desktop icon" extension would probably have the be "MIR"ed first before being merged to "main" as well.

The extension isn't fully featured yet either and in rather heavy flux currently (big thanks go to Sergio Costas). You still cannot rename files on the desktop and so on...

I guess that a "MIR" is going to be filed for it sooner or later.

Your only hope for nautilus 3.30/3.30.1 would probably be that you succeed in nagging Jeremy Bicha to compile and upload  a vanilla nautilus 3.30(.x) to the gnome3 staging PPA. If there is any hope at all ;)

There is nautilus 3.30 now in the gnome-staging-ppa. When cosmic is finally released I will try to replace nautilus 3.26 with 3.30.

---

### Post by ya-paulle on 2018-10-21
I replaced now nautilus 3.26 with 3.30 ( from gnome staging ppa) in ubuntu 18.10 (running gnome). No problems so far.

---

### Post by dino99 on 2018-10-21
Nautilus 3.30 works only if libtracker is not updated from that ppa. Otherwise i get a crash, with:

 Unable to find default domain ontology rule /usr/share/tracker/domain-ontologies/default.rule

Simply downgraded libtracker-spardl-2.0-0 to the cosmic archive version (2.0.3-3)

---

### Post by jbicha on 2018-10-21
@dino99, install the tracker binary package. See [LP: #1793550]("https://launchpad.net/bugs/1793550")

---

### Post by dino99 on 2018-10-21
Confirming that the installion of 'tracker' 2.1.3-1  and the other packages from the ppa let nautilus opening without warning/error.

---

### Post by amano on 2018-10-22
Thanks to Jeremy and Tim Lunn for providing the updated versions in the PPA!!

That works like a charm (at least after initial testing). I grabbed "Dekstop Icons" from the Gnome extensions website so that works too.

As I am using the Wayland session since Artful I think that nothing starts up X (or xwayland) anymore now if not explicitely needed (for eg Firefox, GIMP,...).

---

### Post by amano on 2018-10-22
@dino99: Out of curiosity: does your LibreOffice install still work? It's probably not related but I just noticed that Libreoffice always crashes now for me:

```
amano@amano-desktop:~$ libreoffice --norestore
Application Error


Fatal exception: Signal 6
Stack:
/usr/lib/libreoffice/program/libuno_sal.so.3(+0x3cfb3)[0x7f0a82c03fb3]
/usr/lib/libreoffice/program/libuno_sal.so.3(+0x3d1c3)[0x7f0a82c041c3]
/lib/x86_64-linux-gnu/libc.so.6(+0x41100)[0x7f0a829fe100]
/lib/x86_64-linux-gnu/libc.so.6(gsignal+0xc7)[0x7f0a829fe077]
/lib/x86_64-linux-gnu/libc.so.6(abort+0x121)[0x7f0a829df535]
/usr/lib/libreoffice/program/libmergedlo.so(+0x11ee372)[0x7f0a83e12372]
/usr/lib/libreoffice/program/libmergedlo.so(_ZN11Application5AbortERKN3rtl8OUStringE+0x90)[0x7f0a85a5cfe0]
/usr/lib/libreoffice/program/libmergedlo.so(+0x1efdc57)[0x7f0a84b21c57]
/usr/lib/libreoffice/program/libmergedlo.so(+0x2e3e59b)[0x7f0a85a6259b]
/usr/lib/libreoffice/program/libuno_sal.so.3(+0x17202)[0x7f0a82bde202]
/usr/lib/libreoffice/program/libuno_sal.so.3(+0x3d08f)[0x7f0a82c0408f]
/lib/x86_64-linux-gnu/libc.so.6(+0x41100)[0x7f0a829fe100]
/lib/x86_64-linux-gnu/libc.so.6(+0xad116)[0x7f0a82a6a116]
/usr/lib/x86_64-linux-gnu/libgio-2.0.so.0(g_dbus_node_info_new_for_xml+0x124)[0x7f0a817c55a4]
/usr/lib/libreoffice/program/libmergedlo.so(+0x2eb899f)[0x7f0a85adc99f]
/usr/lib/x86_64-linux-gnu/libgio-2.0.so.0(+0xc9996)[0x7f0a817ba996]
/usr/lib/x86_64-linux-gnu/libgio-2.0.so.0(+0xc9ba8)[0x7f0a817baba8]
/usr/lib/x86_64-linux-gnu/libgio-2.0.so.0(+0x8f203)[0x7f0a81780203]
/usr/lib/x86_64-linux-gnu/libgio-2.0.so.0(+0x8fad6)[0x7f0a81780ad6]
/usr/lib/x86_64-linux-gnu/libgio-2.0.so.0(+0xc1812)[0x7f0a817b2812]
/usr/lib/x86_64-linux-gnu/libgio-2.0.so.0(+0x8f203)[0x7f0a81780203]
/usr/lib/x86_64-linux-gnu/libgio-2.0.so.0(+0x8f239)[0x7f0a81780239]
/usr/lib/x86_64-linux-gnu/libglib-2.0.so.0(g_main_context_dispatch+0x158)[0x7f0a815cdae8]
/usr/lib/x86_64-linux-gnu/libglib-2.0.so.0(+0x4ded8)[0x7f0a815cded8]
/usr/lib/x86_64-linux-gnu/libglib-2.0.so.0(g_main_context_iteration+0x2c)[0x7f0a815cdf6c]
/usr/lib/libreoffice/program/libvclplug_gtk3lo.so(+0x89973)[0x7f0a769a8973]
/usr/lib/libreoffice/program/libmergedlo.so(_ZN11Application5YieldEv+0x2e)[0x7f0a85a5d4be]
/usr/lib/libreoffice/program/libmergedlo.so(_ZN11Application7ExecuteEv+0x45)[0x7f0a85a5ec35]
/usr/lib/libreoffice/program/libmergedlo.so(+0x1f035b6)[0x7f0a84b275b6]
/usr/lib/libreoffice/program/libmergedlo.so(+0x2e3fd26)[0x7f0a85a63d26]
/usr/lib/libreoffice/program/libmergedlo.so(_Z6SVMainv+0x30)[0x7f0a85a63e20]
/usr/lib/libreoffice/program/libmergedlo.so(soffice_main+0x91)[0x7f0a84b43c61]
/usr/lib/libreoffice/program/soffice.bin(+0x107b)[0x55a4c0b8e07b]
/lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xeb)[0x7f0a829e109b]
/usr/lib/libreoffice/program/soffice.bin(+0x10ba)[0x55a4c0b8e0ba]

```

---

### Post by dino99 on 2018-10-22
Does not get your issue, but an other one, non fatal as the app open

oem@oem-desktop:~$ libreoffice --norestore
javaldx: Could not find a Java Runtime Environment!
Please ensure that a JVM and the package libreoffice-java-common
is installed.
If it is already installed then try removing ~/.libreoffice/3/user/config/javasettings_Linux_*.xml
Warning: failed to read path from javaldx

Installing the libreoffice-java-common as proposed, and cant find the .libreoffice dir.
Getting the same error after installation.

[https://ask.libreoffice.org/en/question/28331/javaldx-could-not-find-a-java-runtime-environment/](https://ask.libreoffice.org/en/question/28331/javaldx-could-not-find-a-java-runtime-environment/)

In fact "~/.libreoffice/3/user/config/javasettings_Linux_*.xml" is now located inside .config/libreoffice/4/user/config/"

PS: after installing libreoffice-base, the previous error is gone now.

---

### Post by jbicha on 2018-10-22
Yes, my LibreOffice has been broken since at least last week, but you're way off topic now. ;)

---

### Post by cariboo on 2018-10-22
Thread closed. as Cosmic has been released.

---

