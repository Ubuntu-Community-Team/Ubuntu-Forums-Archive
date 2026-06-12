---
title: "USB autorun attacks against Linux"
date: 2011-02-07
forum: Security
---

### Post by Linuxer12345 on 2011-02-07
[http://www.net-security.org/secworld.php?id=10544](http://www.net-security.org/secworld.php?id=10544)

How do I protect myself against this?

---

### Post by *uu on 2011-02-07
I haven't watched the video, but the article you linked to states that «the talk concludes with steps that [...] end-users can take to protect systems from this threat». Sounds to me like a pretty good start. ;-)

---

### Post by uRock on 2011-02-07
Autoruns don't automatically run in Ubuntu.

---

### Post by The Cog on 2011-02-07
> **uRock said:**
> Autoruns don't automatically run in Ubuntu.
No, but in the video he shows how to achieve the same effect. He uses a vulnerability in the Evince PDF viewer which is used by nautilus while generating thumbnail previews of the files on a USB stick. The vuln is triggered merely by inserting the stick. He advises disabling the use of previews on removable media. It's an interesting video.

---

### Post by movieman on 2011-02-07
> **The Cog said:**
> He advises disabling the use of previews on removable media. It's an interesting video.

Previews are a huge security hole given the number of bugs in various codecs. 

Any thumbnail generator should be run inside an apparmor sandbox that minimises opportunity for exploits of this kind; the only thing the thumbnail generator should be doing is generating a thumbnail, so it shouldn't be allowed to write to any other files on the system, read files it doesn't need, or access the network.

Given that Windows has already been hit by similar exploits, I'm amazed that Linux developers will still allow the file browser to call random programs to which they pass random data without user intervention and without any extra security.

---

### Post by uRock on 2011-02-07
> **movieman said:**
> Any thumbnail generator should be run inside an apparmor sandbox that minimises opportunity for exploits of this kind; the only thing the thumbnail generator should be doing is generating a thumbnail, so it shouldn't be allowed to write to any other files on the system, read files it doesn't need, or access the network.

Has there been an AppArmor definition for this or does one need to be written?

@The Cog, thanks for pointing that out. I hadn't watched the video. The good thing on my end is the fact that the only PDFs I open via the thumb drive are ones I have created.

Does this same vulnerability have an effect with downloaded PDFs which gnome automatically creates the mini-PDF thumbnail?

---

### Post by movieman on 2011-02-07
> **uRock said:**
> Has there been an AppArmor definition for this or does one need to be written?

I presume it would need to be written: I don't know which programs are being called to generate the thumbnails or how they are generated.

---

### Post by The Cog on 2011-02-07
He did it with AppArmor disabled. He said that it took too long with app-armor enabled for his live demo, but claimed it could still be done. 

He also said that evince was one of the few preview generator utilities that was protected by AppArmor by default, and he would probably have been better off using a different file type.

---

### Post by psusi on 2011-02-07
Anyone want to guess how many hours until we get an evince update to patch that bug? ;)

---

### Post by uRock on 2011-02-07
I just ran updates my updates AppArmor has some new profiles,```
The following packages will be upgraded:
  apparmor apparmor-profiles apparmor-utils google-chrome-stable
  indicator-sound libapparmor-perl libapparmor1
7 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 22.1MB of archives.

``` And, mine are set to enforce, so I feel comfy.```
35 profiles are loaded.
13 profiles are in enforce mode.
   /sbin/dhclient3
   /usr/bin/evince
   /usr/bin/evince-previewer
   /usr/bin/evince-thumbnailer
   /usr/bin/freshclam
   /usr/lib/NetworkManager/nm-dhcp-client.action
   /usr/lib/chromium-browser/chromium-browser//browser_java
   /usr/lib/chromium-browser/chromium-browser//browser_openjdk
   /usr/lib/connman/scripts/dhclient-script
   /usr/lib/cups/backend/cups-pdf
   /usr/sbin/cupsd
   /usr/sbin/tcpdump
   /usr/share/gdm/guest-session/Xsession

```

---

### Post by psusi on 2011-02-07
Nevermind, was already fixed a few days ago:

evince (2.32.0-0ubuntu1.1) maverick-security; urgency=low

  * SECURITY UPDATE: arbitrary code execution via multiple dvi backend
    overflows
    - debian/patches/02_CVE-2010-264x.patch: add bounds checking in
      backend/dvi/mdvi-lib/{afmparse,dviread,pk,tfmfile,vf}.c.
    - CVE-2010-2640
    - CVE-2010-2641
    - CVE-2010-2642
    - CVE-2010-2643
 -- Marc Deslauriers <marc.deslauriers@ubuntu.com>   Mon, 03 Jan 2011 11:38:25 -0500

---

### Post by sammiev on 2011-02-07
Thanks for the update folks. This is what makes Lunix and Ubuntu great! :)

---

### Post by The Cog on 2011-02-08
> **psusi said:**
> Nevermind, was already fixed a few days ago:
Sweet!

---

### Post by emarkay on 2011-02-09
Here's a direct link to the presentation (PDF Slidehow)
[URL="http://http://blogs.iss.net/archive/papers/ShmooCon2011-USB_Autorun_attacks_against_Linux.pdf"]
[/URL][http://blogs.iss.net/archive/papers/ShmooCon2011-USB_Autorun_attacks_against_Linux.pdf](http://blogs.iss.net/archive/papers/ShmooCon2011-USB_Autorun_attacks_against_Linux.pdf)

Note that some of the potential access points are not protected by PIE or AppArmor.  Of course the premise here is getting a USB or other autorun device mounted after the target systems is booted.

As I see it "Browse media when inserted, " is OK, but having "Never prompt or srart media when inserted..." enabled is a good thing too. 

Also, I disable thumbnailers by default anyway.  Just like the conclusion says.  :)

---

### Post by movieman on 2011-02-09
> **emarkay said:**
> Of course the premise here is getting a USB or other autorun device mounted after the target systems is booted.

Well, in a lot of cases you just have to get your corrupted file onto someone's USB stick so that when they plug it into the computer the thumbnailer will run and execute your exploit code. That's much easier than getting your own USB stick plugged into the computer as people often use them to transfer files, particularly to machines that aren't network or are on private networks.

---

### Post by raffen on 2011-02-10
> **movieman said:**
> 
Any thumbnail generator should be run inside an apparmor sandbox that minimises opportunity for exploits of this kind;

.. and that is indeed the default setting in Ubuntu 9.10 and later:

[http://www.ubuntu.com/usn/usn-1035-1](http://www.ubuntu.com/usn/usn-1035-1)

"In the default installation of Ubuntu 9.10 and later, attackers would be isolated by the Evince AppArmor profile. "

---

### Post by uRock on 2011-02-10
> **raffen said:**
> .. and that is indeed the default setting in Ubuntu 9.10 and later:

[http://www.ubuntu.com/usn/usn-1035-1](http://www.ubuntu.com/usn/usn-1035-1)

"In the default installation of Ubuntu 9.10 and later, attackers would be isolated by the Evince AppArmor profile. "
[s]Not possible. AppArmor is set to complain, not enforce, by default. Which means it wouldn't be protecting.[/s] /me was wrong :oops:

---

### Post by FuturePilot on 2011-02-10
> **uRock said:**
> Not possible. AppArmor is set to complain, not enforce, by default. Which means it wouldn't be protecting.

It's definitely set to enforce.
```
$ sudo apparmor_status
apparmor module is loaded.
10 profiles are loaded.
10 profiles are in enforce mode.
   /sbin/dhclient3
   /usr/bin/evince
   /usr/bin/evince-previewer
   /usr/bin/evince-thumbnailer
   /usr/lib/NetworkManager/nm-dhcp-client.action
   /usr/lib/connman/scripts/dhclient-script
   /usr/lib/cups/backend/cups-pdf
   /usr/sbin/cupsd
   /usr/sbin/ntpd
   /usr/sbin/tcpdump
0 profiles are in complain mode.
2 processes have profiles defined.
2 processes are in enforce mode :
   /sbin/dhclient3 (4424) 
   /usr/sbin/cupsd (1025) 
0 processes are in complain mode.
0 processes are unconfined but have a profile defined.
```

---

### Post by uRock on 2011-02-10
> **FuturePilot said:**
> It's definitely set to enforce.

I could've sworn I had to enable those on my first install. Learn something new every day.

Thanks,
uRock

---

### Post by newbie2 on 2011-02-10
> [B][COLOR="Red"]It was evince-thumbnailer that
was exploited[/COLOR][/B], not Nautilus and certainly not Linux. This feature in
Nautilus exposes other systems to potential attacks, but Nautilus
itself was not shown as vulnerable in the demonstration. Nautilus
also has a configuration option which lets you choose if you want
this behavior or not, although I personally believe it shouldn't do
this at all when the screen is locked.

This is a vulnerability in Ubuntu (and probably other GNOME-based
distros), but it is completely erroneous to say that it's a
vulnerability in Linux, for two reasons: 1) The applications that
were exploited are in use on non-Linux systems (and will be equally
exposed), and 2) many Linux-systems doesn't use these applications at
all. 
[http://www.h-online.com/open/news/forum/S-Not-Nautilus-and-certainly-not-Linux/forum-117073/msg-14371201/read/](http://www.h-online.com/open/news/forum/S-Not-Nautilus-and-certainly-not-Linux/forum-117073/msg-14371201/read/)

---

### Post by DZ* on 2011-02-10
It was still not a trivial thing to do. The demo worked with  Apparmor disabled and the stick had something like 400+ of payload files, each having a slim chance to correctly trigger the exploit.

---

### Post by tlu on 2011-02-11
See also [https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/698194](https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/698194) where the respective apparmor profiles have been fixed.

---

### Post by cariboo on 2011-02-11
Just to add something else to the discussion, I saw [this]("http://www.outflux.net/blog/archives/2011/02/11/shaping-the-direction-of-research/") on [the Planet]("http://planet.ubuntu.com/") this afternoon.

---

