---
title: "devinput + ir-keytable replays the previous IR remote control key used"
date: 2018-01-17
forum: Ubuntu/Debian BASED
---

### Post by oldgregg3 on 2018-01-17
I am running Mint (Cinnamon), so Ubuntu 16.04.

Previously I had just been running 'userspace' lirc 0.9.0 with my packard bell serial remote - using the lirc_serial module with kernel 4.8.0-53 and lirc tied to /dev/lirc0 

With the recent Mint 18.3 upgrade came kernel 4.10.0-38, which is where the fun began...

lirc_serial has been deprecated and replaced with the serial_ir module.
Not going to pretend i'm a programming guru, but looking at the source for both of them, there appears to me to be quite a lot of changes, far more than just a rename.

Anyway, when the above changes came along, repeat of any keys in my lirc setup stopped working.  
After a bit of digging, I came across the (now not-so-new) devinput 'in-kernel' method... so thought i'd give that a go. 


devinput with (or without) LIRC 'works' -- including the repeat events --, however  a lot of the time (~ %50) when you press a button, it first replays the previous key that you used, and then (usually) follows with the button you pressed.  (Sometimes it doesn't, and it just replays the previous key).  

I can see this behaviour not just in irw, but also mode2, evtest, and ir-keytable, so I assume the issue is nothing to do with LIRC and all to do with the kernel or serial_ir module.  (Indeed, stopping LIRC and running ir-keytable 'natively', you can still see the issue just running ir-keytable etc)

The only 'custom' changes i've had to make is to create a manual rc_keymaps file for my remote (as I couldn't find one for the gloriousness that is the packard bell), however that all looks to be working fine as all the key bindings come through OK.

I've also played around with the delay and period values for the repeats in ir-keytable, however i don't think these have anything to do with it, as the 'extra presses' don't appear to be 'repeats' they look to be 'new keypresses'

With regards to the "LIRC only" repeats not working, have also tried an upgrade of LIRC to 0.9.4 (full purge and clean install) but no difference on that side of things - with LIRC configured to use the serial device (ie 'default' driver and the serial device instead of devinput), repeats still don't work...  and I can see the repeat events using mode2, but irw shows no repeats.  Have also played with the .lircrc repeat values but to no avail.

example of the 'previous key replayed' issue with timings below:

ir-keytable -t :

<press enter on remote>
1516189405.623331: event type EV_MSC(0x04): scancode = 0x100e
1516189405.623331: event type EV_KEY(0x01) key_down: KEY_ENTER(0x001c)
1516189405.623331: event type EV_SYN(0x00).

1516189405.731042: event type EV_MSC(0x04): scancode = 0x100e
1516189405.731042: event type EV_SYN(0x00).
1516189405.733828: event type EV_MSC(0x04): scancode = 0x100e
1516189405.733828: event type EV_SYN(0x00).
1516189406.002108: event type EV_KEY(0x01) key_up: KEY_ENTER(0x001c)
1516189406.002108: event type EV_SYN(0x00).

<press volume down on remote>
1516189410.300155: event type EV_MSC(0x04): scancode = 0x100e
1516189410.300155: event type EV_KEY(0x01) key_down: KEY_ENTER(0x001c)
1516189410.300155: event type EV_SYN(0x00).

1516189410.578117: event type EV_KEY(0x01) key_up: KEY_ENTER(0x001c)
1516189410.578117: event type EV_SYN(0x00).



evtest:
<press enter on remote>
Event: time 1516185220.242097, type 1 (EV_KEY), code 28 (KEY_ENTER), value 0
Event: time 1516185220.242097, -------------- SYN_REPORT ------------
Event: time 1516185221.265088, type 4 (EV_MSC), code 4 (MSC_SCAN), value 100e
Event: time 1516185221.265088, type 1 (EV_KEY), code 28 (KEY_ENTER), value 1
Event: time 1516185221.265088, -------------- SYN_REPORT ------------

<press volume down on remote>
Event: time 1516185221.372809, type 1 (EV_KEY), code 28 (KEY_ENTER), value 0
Event: time 1516185221.372809, type 4 (EV_MSC), code 4 (MSC_SCAN), value 1013
Event: time 1516185221.372809, type 1 (EV_KEY), code 114 (KEY_VOLUMEDOWN), value 1
Event: time 1516185221.372809, -------------- SYN_REPORT ------------
Event: time 1516185221.375536, type 4 (EV_MSC), code 4 (MSC_SCAN), value 1013
Event: time 1516185221.375536, -------------- SYN_REPORT ------------
Event: time 1516185221.650107, type 1 (EV_KEY), code 114 (KEY_VOLUMEDOWN), value 0
Event: time 1516185221.650107, -------------- SYN_REPORT ------------


dmesg: 

[   66.958409] serial_ir serial_ir.0: auto-detected active high receiver
[   66.986398] Registered IR keymap rc-rc6-mce
[   66.986477] input: Serial IR type home-brew as /devices/platform/serial_ir.0/rc/rc0/input16
[   66.986562] rc rc0: Serial IR type home-brew as /devices/platform/serial_ir.0/rc/rc0
[   66.988487] IR RC6 protocol handler initialized
[   66.988703] lirc_dev: IR Remote Control driver registered, major 244
[   66.989890] rc rc0: lirc_dev: driver ir-lirc-codec (serial_ir) registered at minor = 0
[   66.989891] IR LIRC bridge handler initialized
[  105.897872] IR NEC protocol handler initialized


ir-keytable:

Found /sys/class/rc/rc0/ (/dev/input/event13) with:
    Driver serial_ir, table rc-rc6-mce
    Supported protocols: unknown other lirc rc-5 jvc sony nec sanyo mce-kbd rc-6 sharp xmp 
    Enabled protocols: lirc nec 
    Name: Serial IR type home-brew
    bus: 25, vendor/product: 0001:0001, version: 0x0100
    Repeat delay = 500 ms, repeat period = 125 ms

serial port is set using setserial:  (via /etc/serial.conf)  /dev/ttyS0 uart none

lsmod |grep lir:

ir_lirc_codec          16384  0
lirc_dev               20480  1 ir_lirc_codec
rc_core                28672  7 ir_rc6_decoder,ir_nec_decoder,rc_rc6_mce,ir_lirc_codec,lirc_dev,serial_ir

lircd.options.conf is the default dist file for the devinput setup, otherwise when running "LIRC only", the only changes are: driver = default and device = /dev/lirc0.


Have dug as far as I know how.. and googled/searched various forums etc but haven't found the answer...

Hoping someone out there has come across this or has some knowledge to point me in the right direction, thank you in advance!

 O:)

---

### Post by howefield on 2018-01-17
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

