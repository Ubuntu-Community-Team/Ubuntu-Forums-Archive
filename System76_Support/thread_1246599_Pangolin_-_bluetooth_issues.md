---
title: "Pangolin - bluetooth issues"
date: 2009-08-21
forum: System76 Support
---

### Post by SiberianBear on 2009-08-21
seems like there are some bluetooth issues with my pangolin:

root@hades:/etc/bluetooth# hcitool dev
Devices:
root@hades:/etc/bluetooth# hidd --search
Searching ...
root@hades:/etc/bluetooth# 

so.. no wonder I can't see my bluetooth phone.
it seems I have no bluetooth hardware in the laptop! or at least it's not working, for whatever reason.

a little help, please?

---

### Post by gila_monster on 2009-08-21
On the Pangolin, it always boots with Bluetooth off. Did you turn it on with Fn-F12? If not, that's likely your problem.

There isn't a way to get it to boot with the Bluetooth on. You always have to do this manually.

---

### Post by SiberianBear on 2009-08-21
fn-f12 seems to have turned bluetooth on.

however, there are still issues.

root@hades:~# hciconfig
hci0:   Type: USB
        BD Address: 00:10:60:96:ED:49 ACL MTU: 310:10 SCO MTU: 64:8
        UP RUNNING PSCAN 
        RX bytes:3528 acl:0 sco:0 events:249 errors:0
        TX bytes:3059 acl:0 sco:0 commands:94 errors:0

root@hades:~# hcitool dev
Devices:
        hci0    00:10:60:96:ED:49
root@hades:~#

this indicates the laptop's hardware is working.

however, I still can't connect to my phone (samsung sch-r420)

if I launch the bluetooth-wizard, it sees the phone and tries to connect.

I see a "such and such would like to pair, allow?" and I allow.

then it (the phone) asks for some sort of passphrase (I didnt set any passphrases anywhere for bluetooth), and it fails to connect no matter what I enter there.

hrm.

any ideas?

---

### Post by SiberianBear on 2009-08-22
bump

---

### Post by gila_monster on 2009-08-22
Bear,

first, please remember that the System76 forum is pretty quiet on weekends. You might want to wait a full 24 hours before bumping a thread -- might not be anyone around much until Monday.

Second, I haven't used my Bluetooth for a while, but I do recall that there is a passphrase/code to set somewhere in the system, possibly when you ask the Bluetooth applet to try pairing, or maybe in the phone. (In fact, what you are seeing might be when you are supposed to do that! Did you try entering some code just to see what would happen?) When I get some time, I will see if I can work it out and report back to you.

Udacha, Medved! (I think I got that right. I haven't tried speaking Russian for almost 30 years....)

---

