---
title: "Touchpad on Daru2"
date: 2007-11-14
forum: System76 Support
---

### Post by shingalated on 2007-11-14
Has anyone else had problems with the touchpad on their Darter 2?  Mine will sometimes move only up and down, or lose its double tap to drag and scrolling abilities, or sometimes it will stop working completely.  It is usually fixed by a reboot.

---

### Post by ackey on 2007-11-14
I've never had a problem with it, though the "Touchpad" menu in preferences doesn't work (issue in Gutsy).

I never had problems with it running in Feisty, either.

---

### Post by palintheus on 2007-11-14
I have had the issue with the tapping coming and going and with the touchpad not working all together requiring a reboot.

---

### Post by thomasaaron on 2007-11-14
Try reloading the module:

sudo modprobe -r psmouse
sudo modprobe psmouse

---

### Post by shingalated on 2007-11-14
I just tried it, it did not fix the double tap to drag or the scrolling.  I have yet to try it when it stops working completely, luckly that problem only happens a couple times a week.

---

### Post by shingalated on 2007-12-07
Its being mean to me again.  A lot.  I have to reload the module every 5 minutes, and rebooting doesn't really help.  Do you think it is the touchpad itself?:guitar:

---

### Post by thomasaaron on 2007-12-07
I've heard of this with a couple of other people -- on various computers, not just the DarU2.

I've had a grand total of 1 bad touchpad so far, so I'm thinking that's not it. I wonder if it is a Gutsy thing. Possibly a freeze. It would be helpful to have a look at /var/log/messages just after a freeze. (Record the time of the freeze on your LCD clock to make it easier for me to identify the freeze.)

---

### Post by shingalated on 2007-12-09
```
Dec  6 18:07:26 lucy kernel: [76229.736000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
Dec  6 18:07:26 lucy last message repeated 3 times
Dec  6 18:07:26 lucy kernel: [76229.740000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
Dec  6 18:07:26 lucy kernel: [76229.740000] psmouse.c: issuing reconnect request
Dec  6 18:07:27 lucy kernel: [76230.388000] atkbd.c: Unknown key pressed (translated set 2, code 0xf2 on isa0060/serio0).
Dec  6 18:07:27 lucy kernel: [76230.388000] atkbd.c: Use 'setkeycodes e072 <keycode>' to make it known.
Dec  6 18:07:27 lucy kernel: [76230.908000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0xa5a0b1, caps: 0xa04713/0x0
Dec  6 18:07:27 lucy kernel: [76230.936000] input: SynPS/2 Synaptics TouchPad as /class/input/input11
Dec  6 18:07:27 lucy kernel: [76230.940000] atkbd.c: Unknown key released (translated set 2, code 0xf2 on isa0060/serio0).
Dec  6 18:07:27 lucy kernel: [76230.940000] atkbd.c: Use 'setkeycodes e072 <keycode>' to make it known.
Dec  6 18:07:27 lucy kernel: [76231.100000] r8169: eth0: link down
Dec  6 18:07:28 lucy dhcdbd:  dhclient 15714 down (9) but si_code == 0 and releasing==0 !
Dec  6 18:07:29 lucy kernel: [76232.760000] usb 3-1: USB disconnect, address 2
Dec  6 18:07:29 lucy kernel: [76232.760000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: usblp0: removed
Dec  6 18:07:29 lucy kernel: [76233.092000] usb 6-1: USB disconnect, address 3
Dec  6 18:07:30 lucy kernel: [76233.576000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
Dec  6 18:07:30 lucy last message repeated 2 times
Dec  6 18:07:30 lucy kernel: [76233.580000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
Dec  6 18:07:30 lucy kernel: [76233.580000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
Dec  6 18:07:30 lucy kernel: [76233.580000] psmouse.c: issuing reconnect request
Dec  6 18:07:32 lucy kernel: [76235.384000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0xa5a0b1, caps: 0xa04713/0x0
Dec  6 18:07:32 lucy kernel: [76235.412000] input: SynPS/2 Synaptics TouchPad as /class/input/input12
Dec  6 18:09:07 lucy kernel: [76330.768000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
Dec  6 18:09:07 lucy kernel: [76330.772000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
Dec  6 18:09:07 lucy last message repeated 3 times
Dec  6 18:09:07 lucy kernel: [76330.772000] psmouse.c: issuing reconnect request
Dec  6 18:09:08 lucy kernel: [76331.900000] psmouse.c: Failed to reset mouse on isa0060/serio4
Dec  6 18:09:09 lucy kernel: [76333.096000] atkbd.c: Spurious ACK on isa0060/serio0. Some program might be trying access hardware directly.
Dec  6 18:09:10 lucy kernel: [76333.296000] atkbd.c: Spurious ACK on isa0060/serio0. Some program might be trying access hardware directly.
Dec  6 18:09:10 lucy kernel: [76334.176000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0xa5a0b1, caps: 0xa04713/0x0
Dec  6 18:09:10 lucy kernel: [76334.204000] input: SynPS/2 Synaptics TouchPad as /class/input/input13
Dec  6 18:09:40 lucy kernel: [76364.176000] nfsd: last server has exited
Dec  6 18:09:40 lucy kernel: [76364.176000] nfsd: unexporting all filesystems
Dec  6 18:09:41 lucy exiting on signal 15
Dec  6 18:10:30 lucy syslogd 1.4.1#21ubuntu3: restart.
```

TODAY:

```

Dec  9 12:01:09 lucy dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_servers
Dec  9 12:06:30 lucy kernel: [ 1321.096000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
Dec  9 12:06:30 lucy last message repeated 2 times
Dec  9 12:06:30 lucy kernel: [ 1321.100000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
Dec  9 12:06:30 lucy kernel: [ 1321.100000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
Dec  9 12:06:30 lucy kernel: [ 1321.100000] psmouse.c: issuing reconnect request
Dec  9 12:06:30 lucy kernel: [ 1321.824000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0xa5a0b1, caps: 0xa04713/0x0
Dec  9 12:06:30 lucy kernel: [ 1321.856000] input: SynPS/2 Synaptics TouchPad as /class/input/input13
Dec  9 12:17:47 lucy kernel: [ 1998.372000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
Dec  9 12:17:47 lucy last message repeated 4 times
Dec  9 12:17:47 lucy kernel: [ 1998.372000] psmouse.c: issuing reconnect request
Dec  9 12:17:48 lucy kernel: [ 1999.816000] input: PS/2 Synaptics TouchPad as /class/input/input14
Dec  9 12:18:09 lucy kernel: [ 2020.408000] psmouse.c: TouchPad at isa0060/serio4/input0 lost synchronization, throwing 2 bytes away.
Dec  9 12:36:12 lucy kernel: [ 3103.312000] atkbd.c: Unknown key pressed (translated set 2, code 0xf1 on isa0060/serio0).
Dec  9 12:36:12 lucy kernel: [ 3103.312000] atkbd.c: Use 'setkeycodes e071 <keycode>' to make it known.
Dec  9 12:36:12 lucy kernel: [ 3103.312000] atkbd.c: Unknown key released (translated set 2, code 0xf1 on isa0060/serio0).
Dec  9 12:36:12 lucy kernel: [ 3103.312000] atkbd.c: Use 'setkeycodes e071 <keycode>' to make it known.
Dec  9 12:43:03 lucy syslogd 1.4.1#21ubuntu3: restart.
Dec  9 12:50:24 lucy kernel: [ 3955.536000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Dec  9 12:50:25 lucy kernel: [ 3956.132000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Dec  9 12:50:33 lucy dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.host_name
Dec  9 12:50:33 lucy dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_domain
Dec  9 12:50:33 lucy dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_servers
Dec  9 13:04:53 lucy -- MARK --
Dec  9 13:24:53 lucy -- MARK --
Dec  9 13:44:53 lucy -- MARK --
Dec  9 14:04:53 lucy -- MARK --
Dec  9 14:14:24 lucy kernel: [ 8995.352000] psmouse.c: TouchPad at isa0060/serio4/input0 lost synchronization, throwing 1 bytes away.
Dec  9 14:16:27 lucy kernel: [ 9118.468000] psmouse.c: TouchPad at isa0060/serio4/input0 lost synchronization, throwing 2 bytes away.
Dec  9 14:16:44 lucy kernel: [ 9135.576000] psmouse.c: TouchPad at isa0060/serio4/input0 lost synchronization, throwing 2 bytes away.
Dec  9 14:16:59 lucy kernel: [ 9150.416000] psmouse.c: TouchPad at isa0060/serio4/input0 lost synchronization, throwing 2 bytes away.
Dec  9 14:17:06 lucy kernel: [ 9157.544000] psmouse.c: TouchPad at isa0060/serio4/input0 lost synchronization, throwing 2 bytes away.
Dec  9 14:17:09 lucy kernel: [ 9159.984000] psmouse.c: TouchPad at isa0060/serio4/input0 lost synchronization, throwing 2 bytes away.
Dec  9 14:23:08 lucy kernel: [ 9519.416000] psmouse.c: TouchPad at isa0060/serio4/input0 lost synchronization, throwing 2 bytes away.
```

Also, if it returns to a usable condition after acting up, a right click sometimes makes it go crazy again.

---

### Post by thomasaaron on 2007-12-10
Well, those errors definitely look like the ones I deemed a bad touchpad recently.

You'd better email me at support on this one.  I'll be testing a Darter in the next day or two. I'd like to try to replicate the problem just to make sure it is not a bug before bringing the unit in for repair.

Have you added any software that might be related to this problem?
Or have you made any keyboard or mouse configuration changes?

Best,
Tom

---

### Post by gaussian on 2007-12-30
Tom,

I have been having exactly the same issues lately Shingalated. Did you decide that it is likely to be hardware problem? I noticed that 

sudo modprobe -r psmouse
sudo modprobe psmouse 
and CTRL-ALT-Backspace

(updated: Also it seems that suspending and waking up from that cures the issue)

cures the issue. But anyway, it is annoying: the touchpad settings disappear constantly (and I am so clumsy that using computer without touchpad double-click disabled is really painful). 

Background: DARU2, using still Feisty (Gnome).

---

### Post by thomasaaron on 2007-12-31
I'm pretty convinced it is software problem, and I'm pretty sure I found a fix. The one person I tested with, though, has not reported back to me yet.  If you want to email me at support(at)... You can try the fix and let me know how it works.

Incidently, both people who have reported this problem have been running Kubuntu, I think? Are you?

---

### Post by palintheus on 2007-12-31
Ive had this issue with random loss of settings on the touchpad, and the touchpad not working at random times. I have been removing/inserting the psmouse module to fix it. I have not had to restart X though to get it working. I am running Ubuntu 7.10

---

### Post by gaussian on 2007-12-31
> **thomasaaron said:**
> I'm pretty convinced it is software problem, and I'm pretty sure I found a fix. The one person I tested with, though, has not reported back to me yet.  If you want to email me at support(at)... You can try the fix and let me know how it works.

Incidently, both people who have reported this problem have been running Kubuntu, I think? Are you?

Thomas, 

Email has been sent. And no, I am not using Kubuntu, just plain Ubuntu.

---

### Post by thomasaaron on 2007-12-31
OK, thanks for letting me know. It's good to know that kde is not a common denominator in this. Makes my job a lot harder when I have to deal with os-derivitive-specific stuff.

---

