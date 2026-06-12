---
title: "Hacker accessing my remote desk?!?!?"
date: 2010-08-21
forum: Security
---

### Post by locoHost on 2010-08-21
I had remote desk running on a machine and I went downstairs the other day, turned it on, and someone was controlling the machine. Of course that's partially my fault since there was -zero- rd password set. However, my question is how did this person figure out my IP and get past the router to the machine? I don't have any forwarding setup. My router admin password is (has always been) strong. I guess my question now is: Is there anyway to restrict rd access to the local network?

Thanks for helping :-)

---

### Post by CharlesA on 2010-08-21
If you clicked "configure the network automatically" and yer router has UPNP, you opened VNC up to the internet. With no password, you probably had a bot connect.

---

### Post by SoFl W on 2010-08-21
Just curious, how were they controlling it?   I am asking because I had a friend that put down his cell phone near his wireless mouse and the mouse would start to move across the screen.  The first time it happened he got nervous, but figured out what the problem was.

---

### Post by OpSecShellshock on 2010-08-21
> **CharlesA said:**
> If you clicked "configure the network automatically" and yer router has UPNP, you opened VNC up to the internet. With no password, you probably had a bot connect.

This is almost certainly what happened. I'd reinstall, disable UPnP in the router's administration page, and not enable remote desktop. Easy fix.

---

### Post by locoHost on 2010-08-22
Thanks for the replies guys! :-) However, no one is saying how to restrict access to local network. Is this impossible?

---

### Post by cariboo on 2010-08-22
Turn off upnp in your router, and don't forward port 5900 to the router.

---

### Post by locoHost on 2010-08-22
> **cariboo907 said:**
> Turn off upnp in your router, and don't forward port 5900 to the router.

Didn't see any setting in my Netgear router for UPnP. Also, when would I have forwarded port 5900 to my router? Is this something that RD does when it installs?

---

### Post by locoHost on 2010-08-22
Ok, just checked, my Netgear FVS318 *does not have UPnP*. Ok so no UPnP, no ports forwarded, so now how could someone get in to control my machine?

I do have a Belkin Wifi AP on the network. It has WPA2-AES with both a strong admin password and connect password.

I just don't see the vulnerablility :-/

Thanks again for sharing your expertise :-)

---

### Post by CharlesA on 2010-08-22
Use something like Shields UP! to scan yer external IP for open ports.

---

### Post by wacky_sung on 2010-08-22
> **locoHost said:**
> Ok, just checked, my Netgear FVS318 *does not have UPnP*. Ok so no UPnP, no ports forwarded, so now how could someone get in to control my machine?

I do have a Belkin Wifi AP on the network. It has WPA2-AES with both a strong admin password and connect password.

I just don't see the vulnerablility :-/

Thanks again for sharing your expertise :-)

How many characters & length of password did you create for your WPA2-AES?What type of password character did you include?If you have a weak password strength and it is still possible for a brute force attack off your wifi.Another thing is that you are using wifi and it is very prone to MTM(Man in The Middle) attack through it.I will strongly encourage you to get at least a password strength of 20 characters or more using big,small letters,number and special characters which made it much tougher for a brute force attack.Alternative,you can try to stop using wifi and get wired to verify if the hack continued.

---

### Post by OpSecShellshock on 2010-08-22
> **locoHost said:**
> Ok, just checked, my Netgear FVS318 *does not have UPnP*. Ok so no UPnP, no ports forwarded, so now how could someone get in to control my machine?

I do have a Belkin Wifi AP on the network. It has WPA2-AES with both a strong admin password and connect password.

I just don't see the vulnerablility :-/

Thanks again for sharing your expertise :-)

Is the router's administration page accessible from the open web, or only internally? Is it running the current firmware?

---

### Post by locoHost on 2010-08-22
> **wacky_sung said:**
> How many characters & length of password did you create for your WPA2-AES?

It's 8 characters and it's a totally random generated string. It's mixed letters, upper/lower and numbers.

What is man-in-the-middle?

---

### Post by locoHost on 2010-08-22
> **OpSecShellshock said:**
> Is the router's administration page accessible from the open web, or only internally? Is it running the current firmware?

The router has no web access. Never enabled that.

I did just run ShieldsUP scan. I did the 3 main tests. There are zero vulnerabilities. Everything came up 'stealth'.

I think after that test, I feel Ok. I rebuilt the machine (Lucid) and I now have a strong pass on the RD. I haven't seen any strange activity on the computer for more than a week. I guess I'm Ok.

I was just curious about security. I've always thought that routers were hard to bypass.

Followup question: If I -were- to open a port (I haven't yet, but I've been considering trying some secure ftp), would I then be vulnerable? I mean of course there would be rule to foward sftp traffic to the one machine, but I'm not gonna try this if it's too risky.

Thanks for the info guys. I learn so much here :-)

---

### Post by wacky_sung on 2010-08-22
> **locoHost said:**
> It's 8 characters and it's a totally random generated string. It's mixed letters, upper/lower and numbers.

What is man-in-the-middle?

See [here]("http://it.toolbox.com/wiki/index.php/Man-in-the-Middle_Attack") for Man in The Middle attack.Change your password to a minimum length of 20 characters and above.I have no doubt if your wifi getting brute force through [dictionary attack]("http://airheads.arubanetworks.com/article/security-note-wpa-and-wpa2-dictionary-attacks").Try to get wired and at the same time stop using Mac filtering in your router as well because Mac address can easily be spoof if you using wifi filtering.

---

### Post by uRock on 2010-08-22
> **locoHost said:**
> If I -were- to open a port (I haven't yet, but I've been considering trying some secure ftp), would I then be vulnerable? I mean of course there would be rule to foward sftp traffic to the one machine, but I'm not gonna try this if it's too risky.

Thanks for the info guys. I learn so much here :-)
The moment you open to the other side of your router you need to have everything as secure as possible. Please see the Security thread by bodhi.zazen and look for the server stuff he has there. He had one great application that blacklists possible intruders for a period of time or permanently, whichever you set it up for. As well as, adding security to your other machines to keep them from becoming a target.

---

### Post by wacky_sung on 2010-08-23
See here below for a general guide for securing your wifi connection although it is kinda old but very much informative.

[Page 1 of 4]("http://www.maxi-pedia.com/wireless+wifi+network+security+tutorial+101")
[Page 2 of 4]("http://www.maxi-pedia.com/WPA+WPA2+WiFi+protected+access")
[Page 3 of 4]("http://www.maxi-pedia.com/ipsec+vpn+wireless+architecture")
[Page 4 of 4]("http://www.maxi-pedia.com/other+wireless+security+WLAN+considerations")

---

