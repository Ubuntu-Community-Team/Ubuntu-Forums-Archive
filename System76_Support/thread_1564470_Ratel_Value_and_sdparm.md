---
title: "Ratel Value and sdparm"
date: 2010-08-30
forum: System76 Support
---

### Post by ctsdownloads on 2010-08-30
Hi guys, 

Been hoping someone here can help me with my Ratel Value and the infamous hard drive spin down problem.

As you [can see here]("http://ubuntuforums.org/showpost.php?p=9785254&postcount=1"), I've tried everything I can think of to get my external (directly connected, no hub) USB hard drive to spin down.

Unfortunately like most things that are complex in General Help, it's got zero chance of being answered. Have any of you run into the issues described in that link?

Finally out of pure frustration, I ended up adding


> /dev/sdb {
    apm = 255
    apm_battery = 254
}


to my /etc/hdparm.conf

and then call it up at /etc/rc.local via

> # workaround for hdparm disk spindown in 10.04
(echo "\n$(date)" && for devname in $(cat /etc/hdparm.conf | grep -o "/dev/sd[a-z]"); do export DEVNAME="$devname" && (/lib/udev/hdparm || true); done) >> /var/log/hdparm_fix.log

as [described here]("https://bugs.launchpad.net/ubuntu/+source/hdparm/+bug/595138/comments/2").

I keep reading how this bug is no longer a problem, but my above linked thread would point out that this is clearly not the case. Really want my Ratel Value to continue acting as a media server, hate for it to spend all day running down my USB hard drive into dust though.... Ideas guys? :)
  Tom?

Thus far /var/log/hdparm_fix.log remains empty last time I did a cat /var/log/hdparm_fix.log

---

### Post by thomasaaron on 2010-09-01
I'm not sure I understand what you're wanting yet, but since the hard drive is powered by a machine that is always on AC power, I don't *think* there is a *need* to spin it down.

That said, I have an external USB drive that goes into a sort of sleep mode when it isn't being used. I've always considered *that* to be spinning down.

Let me know if I'm missing the boat.

---

### Post by ctsdownloads on 2010-09-01
> **thomasaaron said:**
> I'm not sure I understand what you're wanting yet, but since the hard drive is powered by a machine that is always on AC power, I don't *think* there is a *need* to spin it down.

That said, I have an external USB drive that goes into a sort of sleep mode when it isn't being used. I've always considered *that* to be spinning down.

Let me know if I'm missing the boat.

Hi Tom,

Yeah all I need is for my external drive to spin down when not in use. Like you said, a sleep like mode. On my wife's mac, this happens, but it's a different drive in that instance.

Last time I checked, external drives do go into a sleep/spin down kind of mode in which they are not just running all the time. If this is not the case, that's cool too, as it saves me lots of time. ;)

---

