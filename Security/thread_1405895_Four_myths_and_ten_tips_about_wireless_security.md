---
title: "Four myths and ten tips about wireless security"
date: 2010-02-13
forum: Security
---

### Post by Pjotr123 on 2010-02-13
There are four obnoxious common myths about wireless security (wifi), which I've tried to disprove convincingly on my website. Also I've added 10 effective tips to improve the wireless security of your Ubuntu box:
[http://sites.google.com/site/easylinuxtipsproject/securitywireless](http://sites.google.com/site/easylinuxtipsproject/securitywireless)

Reactions are welcome. :)

---

### Post by tucemiux on 2010-02-13
Thanks a lot for the post, I now have my broadcast SSID as enabled.  This fixed the issue I've been having with my laptop at home.  My laptop would configure itself with the correct SSID but it was unable to grab an IP.  I had to disconnect, wait for a few seconds until my SSID appeared as an option in network-manager and then I could connect to it.  Reconnecting alone did not help, I had to disconnect first, wait for the SSID to appear on network-manager and then connect.  I made the changes suggested in your tips and I can boot up my laptop, when I log in my machine already has an IP with connection to the net.

---

### Post by slowth5 on 2010-02-13
Well done. I'm a wireless security nut, and I don't see anything wrong with this site. In fact, you've listed only pertinent information. This is refreshing.

---

### Post by underquark on 2010-02-13
Tip 11
Use a Linux variant.  At least it's some protection against viruses and malicious altering of your files.  Also, some hackers (yeh, OK, not that many) are too thick to use anything but Windows.

Tip 12
Reduce the output of your wireless router to the minimum required to operate your network.  I can't access mine outside of the walls of my house.

Tip 13
Change your passwords/keys etc. at random and often.  Use a 13-character phrase that has a good visual clue for you to remember but which is utter nonsense if looked up in a dzctzznary.

Tip 14
Keep the really sensitive stuff off your main PC - on a USB stick, a CD or whatever.

---

### Post by OpSecShellshock on 2010-02-13
Shouldn't people be using WPA2 if it's available? Also I think it would be good to explain that the AP's encryption is for the connection between the wireless device and the 
AP itself. Once it moves on to the modem and out to the Internet it's going to be clear text unless they use TLS or VPN (as far as I know).

---

### Post by rookcifer on 2010-02-14
I use a 63 character randomly generated password for my encryption key.  The Tomato firmware makes this easy to do -- all you have to do is hit "generate" and it automatically fills it in the field for you.  The only thing you have to do then is get it to your client PC, which is fairly simple to do via a secure IM or e-mail.  From there you can just cut and paste the key into your client's wireless login field and let it save it in memory (so you don't have to paste it in each time).  Then rotate the key out every couple months for safety.

No one (black-hats, governments, space aliens) is going to brute force a 63 character random key, and rainbow tables are definitely out of the question when dealing with that kind of entropy.  For a key of that length there are 63^62 possibilities, which is **1.34364564515225004658e111**  Our sun will burn out long before anyone, using every computer on earth, will brute force it.

---

### Post by Pjotr123 on 2010-02-14
I've merged tip 1 and 2, and created a new tip 2: update the router firmware. :)

---

