---
title: "Daru2 wifi weirdness"
date: 2009-01-07
forum: System76 Support
---

### Post by greg_g on 2009-01-07
"Just the facts, ma'am."

1) Went to the Ubuntu Developer Summit. On day 2, the wireless stopped working on my Daru2.  lspci didn't even list the device.

2) I get home from UDS: before I take apart laptop I boot it just to make sure. wifi works (and obviously listed in lspci)

3) I go to Minneapolis for holidays.  Wifi doesn't work again, and no listing in lspci.

4) I got home Monday. Today I boot it to make sure one more time before I purchase a replacement wireless controller, and wouldn't you know it, it works again.

Does my laptop just get home sick?

If it is a dieing piece of hardware: what should I replace it with when it dies?  What type of device is this called?

Thanks.

---

### Post by thomasaaron on 2009-01-07
> If it is a dieing piece of hardware: what should I replace it with when it dies? What type of device is this called?

A wireless adapter. You probably want to stick with an Intel Pro Wireless 3945. 

Um... What kernel are you running (uname -r) and what did you try when it stopped working? Did you try the wireless button? If so, does the wireless LED seem to work OK?

---

### Post by greg_g on 2009-01-07
"minipci" is actually what I was looking for, name wise. but thanks!

kernel: 2.6.27-9 generic
When it stopped working I did in this order:
1) sudo /etc/init.d/NetworkManager restart
2) toggle wifi button (LED worked)
3) restart laptop
4) lspci (and saw it wasn't listed)
5) borrowed another laptop (thanks jcastro!)

But, when I sent this laptop in to have the screen replaced I did remove the wifi adapter: so it could be seated improperly.  I'll check that tonight (too busy actually using laptop now).  If there isn't anything obviously seated wrong, I'll probably just buy a spare adapter for when it dies again.

---

### Post by thomasaaron on 2009-01-07
Hey, Greg.

Send me an email. I've got one 3945 card left that I can send you.

Best,
Tom

---

