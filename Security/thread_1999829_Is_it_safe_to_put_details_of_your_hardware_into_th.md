---
title: "Is it safe to put details of your hardware into the public domain?"
date: 2012-06-08
forum: Security
---

### Post by yeehi on 2012-06-08
For example, would it be ok for me to publicise the output of the following command lines:

sudo lsusb
sudo lspci
sudo lshw
sudo dmidecode

sandyd says it might cause problems if my usb wireless is plugged in. I may have mac address restrictions on my wireless.

Thank you for your help!

---

### Post by sandyd on 2012-06-08
> **yeehi said:**
> For example, would it be ok for me to publicise the output of the following command lines:

sudo lsusb
sudo lspci
sudo lshw
sudo dmidecode

sandyd says it might cause problems if my usb wireless is plugged in. I may have mac address restrictions on my wireless.

Thank you for your help!
Unless someone knows exactly which house you are living in, AND your mac address (some of the above commands may show it), they will not be able to access your wifi.

---

### Post by yeehi on 2012-06-08
I would be very grateful if you could look at my sig and tell me which lines to remove so that my MAC address isn't an issue.

Thank you! :)

---

### Post by cariboo on 2012-06-08
It seems you have 3  network devices:

[LIST]
[*]serial: 00:90:f5:91:ae:c4
[*]serial: 00:01:38:fd:c8:ca
[*]serial: 02:24:36:40:9a:12
[/LIST]

Replace the above with all zeros should be good enough eg:

[LIST]
[*]serial: 00:90:f5:91:ae:c4
[*]serial:00:00:00:00:00:00
[/LIST]

---

### Post by yeehi on 2012-06-09
Thank you both very much sandyd and cariboo907!

---

### Post by yeehi on 2012-06-09
Thank you both very much sandyd and cariboo907!

How do I mark this thread as solved? I can't seem to edit the subject line of my original post to change the subject from Ubuntu to Solved.

---

### Post by Basher101 on 2012-06-09
> **yeehi said:**
> Thank you both very much sandyd and cariboo907!

How do I mark this thread as solved? I can't seem to edit the subject line of my original post to change the subject from Ubuntu to Solved.

at the top right of your thread are the "Forum Tools" click on them, and in the Drop-down menu there is "mark this Thread as SOLVED"


regards

---

