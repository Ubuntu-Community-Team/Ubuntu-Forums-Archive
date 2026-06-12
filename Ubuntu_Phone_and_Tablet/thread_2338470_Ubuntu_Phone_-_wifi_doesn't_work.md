---
title: "Ubuntu Phone - wifi doesn't work"
date: 2016-09-28
forum: Ubuntu Phone and Tablet
---

### Post by linuxgsm on 2016-09-28
Hello,

I have the Aquaris E5 HD Ubuntu Edition phone, it does not seem to be able to connect to any wifi network.

It scans for available networks and shows the list of available networks.  I choose mine, I enter the password.  There is no error message, no connection is established, and I am simply returned to the list of available networks.

It seems to be the same problem as that reported here:

[Won't connect to secure Wi-Fi]("https://ubuntuforums.org/showthread.php?t=2288904")

(Except that my wifi passphrase is much shorter than the 63-character one used by that guy).

Anyone else have this problem or know of a solution?

Regards,
Erik

---

### Post by linuxgsm on 2016-09-28
i seem to have found a workaround, which is to copy and paste in the password.  i got the idea at this link: [https://bugs.launchpad.net/canonical-devices-system-image/+bug/1445630](https://bugs.launchpad.net/canonical-devices-system-image/+bug/1445630)

my password is 12 characters long, a mixture of numbers and upper and lower case letters, no punctuation.  if i try to connect to my wifi network in the usual way, i enable the "show password" checkbox, i type in the password, the attempt fails silently.  i just tried typing the password in to the text editor and copying it from there and pasting it into the wifi connection screen and it seems to have worked.  yay.

---

