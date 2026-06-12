---
title: "wifi card"
date: 2011-11-18
forum: Server Platforms
---

### Post by crapster on 2011-11-18
Hi,

Im using for a while ubuntu desktop now, today i started to try 
ubuntu server.
The thing is with the server version, i cant install my wireless network card.
Im giving the right ssid en pw but he cant connect, on my ubuntu desktop its no problem, someone with an idd?

thx in advange and sorry for my bad english...


c

---

### Post by jonobr on 2011-11-18
Hey There


Not a direct answer to your question, but just wondering why your using server?
Is there a compelling reason?
Sounded like you were having better luck with desktop.

---

### Post by volkswagner on 2011-11-18
It would help to have some additional info.

Please paste the output of the following commands.

```
iwconfig
```

```
lspci
```

or

```
lsusb
```

If it is an USB device.

What security protocol are you using on your router?  Can you turn off security on the router temporarily to test if it will connect?

A couple links to check out:
[http://ubuntuforums.org/showpost.php?p=10700392&postcount=2](http://ubuntuforums.org/showpost.php?p=10700392&postcount=2)
[http://ubuntuforums.org/showthread.php?t=1734823](http://ubuntuforums.org/showthread.php?t=1734823)

---

### Post by crapster on 2011-11-19
@[jonobr]("http://ubuntuforums.org/member.php?u=197514") because i want to use sudo command from command line and not from the terminal.
and i cant give you an output because its during install and cant connect.
Ubuntu finds my wifi card (not usb) but i just cant connect it sais that its not the correct ssid/pw.
When i install with the desktop version it works without any problems.

thx in advance

---

### Post by volkswagner on 2011-11-19
You can install without networking I believe, then get it working after the install.

I think there is also an advanced installer.  This will allow you to pick additional packages such as wireless tools.  I have done this with Debian text installer, but I think Ubuntu has the same installer.

Also if you have a wired card, why not install using the wired card, then get wireless working, then move the server away from the router or where ever the permanent location will be?

It also may help to boot the live cd and run the commands from above.  Also run lsmod to see what drivers are being used.

---

