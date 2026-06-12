---
title: "wireless keyboard security"
date: 2008-09-24
forum: Security
---

### Post by appropri8 on 2008-09-24
I left my computer logged in for a while, when i came back to it there was a new document on my desktop, it was open and on screen with loads of weird writing in it.  First thoughts were i had been hacked or something so i pulled the network cable.  But then more writing appeared on screen, i was freakin out, what the hell's happening!  Turns out my wireless keyboard was picking up interference from next doors wireless keyboard while they were on msn or something.

I thought my system was pretty secure, but because i use a wireless keyboard everything i type, including my pin for online banking is up for grabs by anyone close by with similar equipment.

If your as security conscious and paranoid as me I'd stop using wireless devices until someone makes one with encryption.

---

### Post by Dr Small on 2008-09-24
No doubt. If you both have the same type of wireless keyboard, I can see this happening, but not over a long distance. Take precaution, and don't use wireless, like me. :) But yes, encryption from the device to the host would make it a great deal safer, unless they are using a WEP password for it...

---

### Post by cariboo on 2008-09-24
You didn't specify what make your wireless keyboard, but this page may help:

[http://www.ubuntu-unleashed.com/2007/08/howto-setup-and-install-bluetooth.html](http://www.ubuntu-unleashed.com/2007/08/howto-setup-and-install-bluetooth.html)

Jim

---

### Post by stmurray on 2008-09-25
That's very odd.  

Presumably your keyboard is bluetooth which most definitely has security issues.  Bluetooth is encrypted, but the keys are based on the PIN you enter when you first pair the device to the computer and the device's MAC address.  However, because it's easier to install, many keyboard/mouse vendors don't require the pin, or have a "built-in" pin that that is the same for all their devices. When you buy any bluetooth device, you may want to check how it gets paired. (the MS device in the link below does allow you to enter a PIN when pairing for the keyboard.)  However, these issues are with a motivated attacker (sniffing your PIN when your first pair, guessing your PIN, etc).  I'm not sure what could cause what you are describing.  

I wonder if 
1) It was radio interference (which would put random characters on the screen).  Bluetooth uses frequency hopping, which makes gives it a high immunity to interference

2) Your computer accepted the neighbor's keyboard traffic because it thought it was from your keyboard.  In standard bluetooth, it shouldn't be the case that two devices have the same MAC address and therefore would ever confuse a paired device with another. 

3) Your neighbors computer paired with your computer without any intervention needed from you. This is my guess as to what happened.  Your bluetooth settings may allow pairing with no PIN and no user intervention, and your computer accepted the pairing.

---

### Post by cariboo on 2008-09-25
If it is just a wireless keyboard and mouse it is entirely possible that he is picking up an RF signal from his neighbor's keybaord.

Jim

---

### Post by Dr Small on 2008-09-25
> **cariboo907 said:**
> If it is just a wireless keyboard and mouse it is entirely possible that he is picking up an RF signal from his neighbor's keybaord.

Jim
That also depends on how far 'the neigbor' lives away. If it looks like it would be pretty far, outta range, then maybe he was sitting under your window, with his wireless keyboard :)

---

### Post by NullHead on 2008-09-25
I have to admit, this would be extremely fun to do to a person such as my own neighbor :twisted:

---

### Post by taget on 2008-09-25
lol, reminds me of lan parties when wireless first came out, this kind of thing would happen all the time, but it was funny. i can see where this would be a security concern in areas that are more densely populated(apartment building).

---

### Post by sonofusion82 on 2008-09-25
this reminds me of an article about wireless keyboard security. apparently it is rather easy to hack their simple wireless security.

[http://www.zdnet.com.au/news/security/soa/Microsoft-wireless-keyboard-hacked-from-50-metres/0,130061744,339284328,00.htm](http://www.zdnet.com.au/news/security/soa/Microsoft-wireless-keyboard-hacked-from-50-metres/0,130061744,339284328,00.htm)

since then, i don't really trust wireless keyboards.

---

### Post by taget on 2008-09-25
I cant reallt see a need for a wireless keyboard unless you are using a Home Theater PC, if you are sitting at your desktop, and using a wireless keyboard your just wasting batteries. seems like the best way to be secure is to not use a wireless keyboard at this point.

---

### Post by NullHead on 2008-09-26
Looks like it's time for a new keyboard :)

---

### Post by WSDsmurf on 2009-03-02
thread mine...

Logitech wireless keyboards all come with security encryption these days... with encryption enabling pin pairing etc done though Logitech's Setpoint driver software.

Under Ubuntu 8.10 I cant find any (easy/gui/straighforward) way to enable the encryption on my wireless keyboards.

Being in a apartment complex with a squillion wifi signals viewable... this is kinda important to me.  Any ideas?

---

### Post by blueshiftoverwatch on 2009-03-05
I used to use a wireless keyboard. But a friend told me that the keyboard probably either didn't use a WEP key or if it did it used one which was short enough to be easily crackable. So I decided to play it safe and switch to an older wired keyboard.

---

### Post by WSDsmurf on 2009-03-06
yes, but wireless keyboards are everyday items now.
and corded just doesnt help for the home theater or couch.

logitech wireless keyboards are common items, so i was hoping that there was a fix to using the encryption out there.

---

### Post by cariboo on 2009-03-06
I have a Logitech ex110 keyboard/mouse and according to Logitech, the encryption software only works in Windows. I guess we will have to lobby Logitech to get encryption for Linux and OS X.

Jim

---

### Post by wsonar on 2009-03-06
> **cariboo907 said:**
> You didn't specify what make your wireless keyboard, but this page may help:

[http://www.ubuntu-unleashed.com/2007/08/howto-setup-and-install-bluetooth.html](http://www.ubuntu-unleashed.com/2007/08/howto-setup-and-install-bluetooth.html)

Jim


This should help me I got to get a new wireless keyboard/mouse my roomate just gave me a 40" tv/monitor I have to kinda sit back to see

---

### Post by NoBugs! on 2009-05-26
Is this Setpoint software a one-time setup to configure the device?
If you set up the keyboard's encryption with the Windows tool, will it stay that way if you reboot to Linux?

---

