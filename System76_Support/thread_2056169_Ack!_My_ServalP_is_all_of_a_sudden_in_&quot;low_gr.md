---
title: "Ack! My ServalP is all of a sudden in &quot;low graphics mode&quot;"
date: 2012-09-10
forum: System76 Support
---

### Post by Replicon on 2012-09-10
Hello,

I'm running an older model (Serval P), and still on a fairly old distro (Hardy haha).

Anyway, I was making preparations for an upgrade, and thought that, for good measure, I should run the System76 update (install driver, etc.) Actually, this was mainly because of stuff I read about when Xorg takes up CPU while browsing the web...

Anyway, when I rebooted, to my horror, I'm in low graphics mode and can't get out! I figured doing the "restore" from the same System76 driver would do the trick and undo whatever I did, but to no avail.

What should I do? I'm sure there's a really easy "undo this nonsense" incantation I just need to figure out...

Also, when I watch the boot screen now, it repeatedly fails to run the boot scripts (/etc/rc.0 or something like that - not sure which one it was - I can go check again).

thanks!

---

### Post by Replicon on 2012-09-10
I ran the following, from other threads:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

And my video looks good.

However, it seems to have lost:

1) Desktop configurations (I had the "3d cube" animation, etc.)

2) Audio (it isn't finding a sound card)

---

### Post by Replicon on 2012-09-10
For audio, looks like the m-a stuff worked:

```

sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa

```

Totally lame that it wiped out the other thing, but I won't bother with it. It's just collateral eye candy damage hehe... unless there's an easy recovery for it. I should just upgrade, really. :)

---

