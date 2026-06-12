---
title: "Still no systemd or delta-debs..."
date: 2011-10-30
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Starks on 2011-10-30
I'm tired of sighing each cycle.

---

### Post by alphacrucis2 on 2011-10-30
> **Starks said:**
> I'm tired of sighing each cycle.

Why would you expect such changes to be introduced with an LTS version?

---

### Post by gsmanners on 2011-10-30
[http://brainstorm.ubuntu.com/idea/13/](http://brainstorm.ubuntu.com/idea/13/)

Marked as "in development." I'd call it progress, at least.

---

### Post by cariboo on 2011-10-31
Including systemd in any release was discussed at the start of Oneiric development, it was decided then to wait until after 12.04 was released, before any thing would be done. I personally can't see it being included in a default install considering how much Canonical has invested in  upstart, but it will be optional. just like btrfs support.

---

### Post by MacUntu on 2011-10-31
Today at UDS: 

15:00 Systemd/Packagekit Integration in Antigua 3.

---

### Post by MadCow108 on 2011-10-31
is there another delta deb meeting?
I sure hope it finally lands this cycle. its working so great in debian.

systemd will obviously not be in 12.04 its far too new for such a large archive but delta debs are isolated from the regular channels and its working well since ages.

---

### Post by crdlb on 2011-11-01
> **MacUntu said:**
> Today at UDS: 

15:00 Systemd/Packagekit Integration in Antigua 3.

I don't think that has anything to do with actually switching to systemd or PackageKit. It is about implementing their dbus interfaces so that Ubuntu won't have to patch GNOME software to use some other interface. In the case of systemd, the interfaces are implemented by separate helper daemons which could be shipped by Ubuntu without using the rest of systemd.

[https://blueprints.launchpad.net/ubuntu/+spec/desktop-p-systemd-packagekit](https://blueprints.launchpad.net/ubuntu/+spec/desktop-p-systemd-packagekit)

---

### Post by MacUntu on 2011-11-01
Right, should have read the blueprint. :)

---

### Post by madjr on 2011-11-01
> **cariboo907 said:**
> Including systemd in any release was discussed at the start of Oneiric development, it was decided then to wait until after 12.04 was released, before any thing would be done. I personally can't see it being included in a default install considering how much Canonical has invested in  upstart, but it will be optional. just like btrfs support.

btrfs will be default at some point once it's stable, but not sure yet about systemd... but it would be a good thing that distros had this in common instead of trying to duplicate efforts yet again.

---

### Post by cariboo on 2011-11-01
Isn't that what systemd is? a duplication of effort? We already have upstart instead of creating a second (or third, or fourth) init system why not work on improving what is already in place.

The only reason I can see behind this, is that upstart wasn't created by RedHat, and they seem to be the big push behind most of the changes we are seeing, even if they don't come out and say it.

---

### Post by crdlb on 2011-11-01
> **cariboo907 said:**
> Isn't that what systemd is? a duplication of effort? We already have upstart instead of creating a second (or third, or fourth) init system why not work on improving what is already in place.

The only reason I can see behind this, is that upstart wasn't created by RedHat, and they seem to be the big push behind most of the changes we are seeing, even if they don't come out and say it.
Systemd and upstart are not similar. You are free to disagree with systemd's design, but it is not reasonable to suggest that its goals could have been met by working on upstart.

---

### Post by dext on 2011-11-01
[http://freedesktop.org/wiki/Software/systemd](http://freedesktop.org/wiki/Software/systemd)  [http://en.wikipedia.org/wiki/Systemd](http://en.wikipedia.org/wiki/Systemd)  [https://fedoraproject.org/wiki/Systemd](https://fedoraproject.org/wiki/Systemd) . i take it people dont know what google is here

---

### Post by cariboo on 2011-11-01
> **crdlb said:**
> Systemd and upstart are not similar. You are free to disagree with systemd's design, but it is not reasonable to suggest that its goals could have been met by working on upstart.

I know they are different, but they accomplish the same thing. To the end user what difference will it make, will my system play a tune and a movie while it's booting? Will it boot 3 times faster? Forget the technical details. Tell what it will do for me. What difference if any will I see?

---

### Post by effenberg0x0 on 2011-11-01
> **dext said:**
> [http://freedesktop.org/wiki/Software/systemd](http://freedesktop.org/wiki/Software/systemd)  [http://en.wikipedia.org/wiki/Systemd](http://en.wikipedia.org/wiki/Systemd)  [https://fedoraproject.org/wiki/Systemd](https://fedoraproject.org/wiki/Systemd) . i take it people dont know what google is here

During Oneiric Alpha process, Firefox constantly reseted search engine to ask.com. We made an agreement to only use ask.com, from then on.

---

### Post by madjr on 2011-11-02
systemd has many more features, so the one doing catch up is upstart, so we are behind and still trying to duplicate efforts for only one distro.

and fedora had upstart and they contributed, but am sure they had good reasons for starting something that would be better in many ways from scratch.

not saying ubuntu needs to drop upstart in this or next cycle, but they need to start testing ubuntu with systemd, filling bugs early to upstream, etc..

in time upstart may become like an old xorg, while everyone else would had moved on to wayland.

but thank God canonical is not the one that will be trying to keep X alive at least..

---

### Post by BwackNinja on 2011-11-02
> **cariboo907 said:**
> I know they are different, but they accomplish the same thing. To the end user what difference will it make, will my system play a tune and a movie while it's booting? Will it boot 3 times faster? Forget the technical details. Tell what it will do for me. What difference if any will I see?

It *can* play a tune while booting :P
[http://lists.freedesktop.org/archives/systemd-devel/2011-February/001252.html](http://lists.freedesktop.org/archives/systemd-devel/2011-February/001252.html)

---

### Post by madjr on 2011-11-02
> **BwackNinja said:**
> It *can* play a tune while booting :P
[http://lists.freedesktop.org/archives/systemd-devel/2011-February/001252.html](http://lists.freedesktop.org/archives/systemd-devel/2011-February/001252.html)

now that ubuntu will be on multiple types of devices some of those features will fit it better

---

### Post by cariboo on 2011-11-03
It's been a day since I asked what benefits the end user will see from using systemd, the only answer I got was about startup and shutdown sounds.

Does anyone personally run systemd on any distribution, or is this one of things that looks cool, but nobody has actually tried it yet?

---

### Post by gsmanners on 2011-11-03
> **cariboo907 said:**
> ... is this one of things that looks cool, but nobody has actually tried it yet?

I haven't tried it, but it primarily seems to have the technical advantage of [cgroups]("http://en.wikipedia.org/wiki/Cgroups"). That was something added to the kernel after upstart was implemented, so it's not surprising that upstart wouldn't have that yet.

---

### Post by effenberg0x0 on 2011-11-03
I haven't researched the current implementation status, if any, but I think cgroups is in upstart roadmap:
[http://www.mail-archive.com/upstart-devel@lists.ubuntu.com/msg01493.html](http://www.mail-archive.com/upstart-devel@lists.ubuntu.com/msg01493.html)

As far as I could see until now, systemd would make it easier for managing servers, but would make small difference to desktop use? 

And there's a lot of change to be done to Ubuntu to adopt it. Some files are standardized to different locations than those adopted by Ubuntu/Debian, which will break a lot of scripts and general shell code out there.

---

### Post by seeker5528 on 2011-11-03
> **effenberg0x0 said:**
> As far as I could see until now, systemd would make it easier for managing servers, but would make small difference to desktop use?

There seem to be conflicting opinions about it's usefulness on servers....

[http://monolight.cc/2011/05/the-systemd-fallacy/](http://monolight.cc/2011/05/the-systemd-fallacy/)

[http://phoronix.com/forums/showthread.php?49777-Systemd-Is-Now-One-Year-Old-Why-You-Should-Use-It/page3](http://phoronix.com/forums/showthread.php?49777-Systemd-Is-Now-One-Year-Old-Why-You-Should-Use-It/page3)

Later, Seeker

---

### Post by gsmanners on 2011-11-03
The only thing I care about is maturity, and systemd is still about five years away in that respect. With all the features it claims to have, I suspect they'll be mostly bug-free by then.

---

### Post by ranch hand on 2011-11-03
> **seeker5528 said:**
> There seem to be conflicting opinions about it's usefulness on servers....

[http://monolight.cc/2011/05/the-systemd-fallacy/](http://monolight.cc/2011/05/the-systemd-fallacy/)

[http://phoronix.com/forums/showthread.php?49777-Systemd-Is-Now-One-Year-Old-Why-You-Should-Use-It/page3](http://phoronix.com/forums/showthread.php?49777-Systemd-Is-Now-One-Year-Old-Why-You-Should-Use-It/page3)

Later, Seeker
That made some really interesting reading.

I haven't tried systemd yet, too busy.  Going to just to see what the noise is about.  Reading the 2 links made this more urgent.  The noise level is incredible.

I am with gsmanners on the maturity issue.  If this bugger is going to do what it claims it will do it is going to be a good ways down the road.

---

