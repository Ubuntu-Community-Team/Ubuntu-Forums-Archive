---
title: "Wireless does not work"
date: 2011-05-19
forum: System76 Support
---

### Post by bradshaw on 2011-05-19
Other computers can connect wirelessly just fine, and my star5 netbook connected just fine too until this morning. I tried restoring, I tried installing drivers. I don't know what else I can do.

---

### Post by isantop on 2011-05-19
What is the status of the indicator lights on the front, left edge of the laptop? Specifically, have a look at the third one from the left. It should be on and solid green.

---

### Post by bradshaw on 2011-05-19
thank you for your response.

from left to right..
yellow, green, off, occasionally blinks yellow

I have daltonism color blindness so yellow may be "red".

---

### Post by isantop on 2011-05-19
Nope, those are just about correct colors. :)

I've also found the problem. Your wireless card is turned off. Press Fn+F11 to turn it back on, then try connecting again. Did that fix it?

---

### Post by bradshaw on 2011-05-19
yes, thank you very much. I owe you a coke.

---

### Post by bradshaw on 2011-05-20
one thing i like to add, while it worked, I had to eventually restart and in doing so networking got disabled, but these two commands worked

sudo rm /var/lib/NetworkManager/NetworkManager.state
service network-manager start

and rebooting

---

