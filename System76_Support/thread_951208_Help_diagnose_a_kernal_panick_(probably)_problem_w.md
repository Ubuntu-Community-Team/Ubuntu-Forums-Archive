---
title: "Help diagnose a kernal panick (probably) problem with my Serval P"
date: 2008-10-17
forum: System76 Support
---

### Post by Replicon on 2008-10-17
Hey all,

So I must have picked up a bad change this morning, because I seem to have had two crashes in the space of a few minutes. I was just listening to music on Audacious and web browsing.

I imagine I need to:

1) Find whatever kernel dump was generated (if any)

2) Figure out what the last-downloaded set of packages was (I imagine there are logs somewhere)

3) Figure out whether it reproduces while I'm just letting it idle as is.


I'll re-run the system76 driver as well, just in case some driver issues came up, but I don't remember there being a driver-related download this morning.

I'm currently running:

Linux ubuntu 2.6.24-21-generic #1 SMP x86_64, fwiw.


Any random tips, in case this problem doesn't go away? The box has been 100% solid for the 6 months or so that I've had it.

---

### Post by Replicon on 2008-10-17
Well, running the System76 driver didn't fix it, and the answer to 3 is, "yup!" So then... what's the next step?

EDIT: It's the variety where caps lock and those lights start blinking... Maybe I can just leave it on but leave it open to TTY1 so that I can get a kernel panic dump...

---

### Post by Replicon on 2008-10-17
Looking at /var/log/apt, I can see lots of KDE stuff from this morning...

---

### Post by Replicon on 2008-10-17
[http://picasaweb.google.com/replicon/KernelPanic?authkey=f8bbdrDMuM0#5258329305056247250](http://picasaweb.google.com/replicon/KernelPanic?authkey=f8bbdrDMuM0#5258329305056247250)

There we go. So looks like Compiz. The laptop was quite happy sitting on my TTY1. I went over to TTY7 (X), turned on a browser, turned on some music, and quickly switched back to TTY1, and the kernel panic came along like clockwork.

---

### Post by Replicon on 2008-10-18
Ok, this is bothering me even more now: I lose the keyboard and trackpad right after grub loads up the OS and starts booting ubuntu. I can hit caps lock on and off during the grub "countdown" but it just stops working after that. The USB mouse works fine, though, so I can basically shut down hehe.

The keyboard works fine when I load up the bios at startup. Running memtest now, and will boot up with the partedmagic CD I have from earlier to make sure things are looking okay, hardwarewise.

---

### Post by Replicon on 2008-10-18
Hmm even when I boot into partedmagic with my boot CD, I lose the keyboard. But the keyboard works fine before. So like the boot menu for partedmagic is fine, and while running memtest, it was fine. This is quite worrisome.....

EDIT: But when I boot partedmagic right into shell, the keyboard is fine!!! Fhut the Wuck?

I don't get it... It's not a hardware failure of the keyboard, because it's fine when I boot into shell... but it's not just my ubuntu getting corrupted due to bad updates recently, since the keyboard also gets lost when I boot into X in partedmagic. Explain THAT hehehe.

I don't even know if this keyboard business is in any way related to the random kernel panic from before.... *sigh*

ok ok i'll stop self-replying now, I know it's annoying. Let's see what you guys think :)

cheers

---

### Post by thomasaaron on 2008-10-20
Does everything work OK if you boot into a previous kernel?
It might be a good idea to look in /var/log/messages to see if it gives a hint as to why the kernel panic is happening.

---

### Post by Replicon on 2008-10-20
How do I boot into a previous kernel? Do I need to change what's commented out on menu.lst, or can I do it through GRUB somehow? I'll try that if it still fails on me.

Both kernel panics I've "captured" (they're in the picasa album linked) revolve around iwlcore, and while Google isn't very useful here, it seems that's related to wireless stuff. I've managed to muster some stability by turning off the wireless. I hope it sticks (I'm wired at home, so I can ride this out until it gets resolved). That being said, I have NO idea what was up with the keyboard. I seem to have fixed it "Nintendo Style", but it's just weird that booting into something completely irrelevant would make it shut down, but only *after* the boot menu. The two seem to be unrelated, but it's weird that they would occur at the same time.

I'll have a look at /var/messages tonight. I looked at all the other logs, and haven't really found anything useful.

---

### Post by thomasaaron on 2008-10-20
When you start the computer and see the grub countdown (grub...3...2...1...), press the "Esc" key.

This will bring you to a boot menu, and you can select the kernel you want to boot into. Arrow down to the first non-recovery mode option and press enter.

---

### Post by Replicon on 2008-10-21
Doesn't seem to be a whole lot in /var/log/messages and messages.0. for example, I found one instance where it crashed while I was doing some heavy youtubing, and while the last entry for that timeframe is an npviewer.bin segfault, there are lots of those entries several minutes before (I guess mostly because flash support is still not quite up to par).

Otherwise, I see some stuff like this just before other crashes, which is also suspicious:

```

Oct 17 19:56:45 ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Oct 17 19:56:45 ubuntu kernel: [   43.889414] tg3: eth0: Link is up at 100 Mbps, full duplex.
Oct 17 19:56:45 ubuntu kernel: [   43.889416] tg3: eth0: Flow control is off for TX and off for RX.
Oct 17 19:56:45 ubuntu kernel: [   43.893733] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Oct 17 19:56:48 ubuntu kernel: [   46.091060] NET: Registered protocol family 17
Oct 17 19:56:52 ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Oct 17 19:56:52 ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.domain_name
Oct 17 19:56:52 ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Oct 17 19:56:52 ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Oct 17 19:56:52 ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu

```

---

### Post by thomasaaron on 2008-10-21
Without looking at your log, it is difficult to say. But if you have a bunch of npviewer segfaults crashes, that explains a lot.

That is a flash-based crash.

Try removing and reinstalling the flash plugin.

```
sudo apt-get --purge remove flashplugin-nonfree
sudo apt-get install flashplugin-nonfree
```

---

### Post by Replicon on 2008-10-21
Did that, though not sure if it made a difference. My big flash complaint is that if I'm watching a youtube video, and then I middle click on a link to another one to open in a new tab, it will grey out/kill the currently-playing video (note: it might be one of my plugins, like flashblock, but I doubt it, since it worked fine before the 8.04 update to the latest FF3).

Things are looking much more stable now that I've shut down the wireless. I'll turn it back on with the next kernel release and see what comes of it hehe. Thanks for the support.

---

