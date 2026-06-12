---
title: "Weird Ubuntu behavior. How to find a keylogger if it exists on your system?"
date: 2011-10-31
forum: Security
---

### Post by nooto_n on 2011-10-31
Hi there, 

Recently my ubuntu stated to behave strange regarding the keyboard input.

Starting from Thursday on various days I had experienced different problems.

Thursday:

1. Copy and paste did not work as expected. I copy text and paste it into the gedit. This works fine. If I try to paste the same text in to the terminal - nothing happens, the text does not appear in the terminal. After pressing shift+ insert for 6-8 times pasting text works. When I copy another text I have the same problem all over again. So I kept struggling like that until I rebooted the system.

Friday (was hell frightening): 

2. Went to HP website to look for the drivers for other PC. [http://www8.hp.com/us/en/support-drivers.html](http://www8.hp.com/us/en/support-drivers.html) 
I could not type in the search field. The cursor was blinking in the search field, however the text was not appearing when i type. After struggling for a minute or two even weirder thing has happened. A one line text box (in ubuntu ambiance theme colors - the theme I use)  appeared near the middle of the screen and the text i was typing appeared on the box, but not on the search field !!! Now I feel so stupid I have not print-screened it.

Saturday: (upgrade from ubuntu 10.4? to 10.10)

Sunday:

3. After using my laptop for a while continuous typing just stopped working if I pressed single letter and was holding it pressed i would get only one letter instead of many. For example: after pressing and holding "a" I get just "a", not "aaaaaaaaaaaaaaaaaaaaaaaaaa".

I am afraid there might be a keylogger on the system. SSHD was always disabled. Only 2 users exist on the system. A guest user had a weak password :}. Just changed it to a stronger one.

Any thoughts, or clues anyone ?

K.

---

### Post by HermanAB on 2011-10-31
Ever played with VNC?  If so, hunt it down and kill it.

You can observe network traffic with Wireshark.

---

### Post by haqking on 2011-10-31
Does the same thing happen from a Live CD/DVD/USB ?

**have you tried a different keyboard ?**

If i was you i would Backup your personal data and do a fresh-install if its not hardware related.

As for keylogger, i highly doubt it, but ya never know, however that sort of issue is not usually indicative of a keylogger as they are designed to sit quietly and capture key input, not destroy key input ;-)

---

### Post by emiller12345 on 2011-10-31
> **haqking said:**
> 
have you tried a different keyboard ?
:wink:
+1
You may consider trying to swap out your keyboard for another one, just to make sure it's not a hardware problem.  Some times bad equipment can manifest symptoms just like these.

---

### Post by Dangertux on 2011-10-31
Yeah I think your keyboard is broken.

There are two things a keylogger doesn't want.

1 - to be noticed by you.
2 - to be noticed by AV.

The two quickest ways for that to happen are for it to screw with input and or broadcast that input over a network.

Just my 2 cents.

---

### Post by tubbygweilo on 2011-10-31
Occasional hardware faults in mouse or keyboard could well cause a few problems such as you describe.

---

### Post by nooto_n on 2011-10-31
Have never used VNC server on this machine. I don't have it installed.

I took a glance at the LISTENING or CONNECTED ports, could use TCPDUMP, but monitoring interpreting network traffic migh be difficult. Many virus use connections to HTTP ports. I guess I'll try to hunt for it leaving overnight with all the other programs switched off.

Another keyboard is not that easy as this is a laptop. Might try if the problems persist.

Fresh install is an option. Still, want to hunt for "it" :D.

> 
As for keylogger, i highly doubt it, but ya never know, however that  sort of issue is not usually indicative of a keylogger as they are  designed to sit quietly and capture key input, not destroy key input :wink:


Ha ha .. Yeah, actually this is the only thing makes me feel this is not a keylogger after all.. Or a bad bad keylogger..

---

### Post by haqking on 2011-10-31
> **nooto_n said:**
> Have never used VNC server on this machine. I don't have it installed.

I took a glance at the LISTENING or CONNECTED ports, could use TCPDUMP, but monitoring interpreting network traffic migh be difficult. Many virus use connections to HTTP ports. I guess I'll try to hunt for it leaving overnight with all the other programs switched off.

Another keyboard is not that easy as this is a laptop. Might try if the problems persist.

Fresh install is an option. Still, want to hunt for "it" :D.


Ha ha .. Yeah, actually this is the only thing makes me feel this is not a keylogger after all.. Or a bad bad keylogger..


I highly expect it is a keyboard issue, a new one is an option as you can plug in a USB one or a PS/2 depending on how old your machine is.

You are likely wasting your time using TCPDUMP....LOL

Check your hardware, check a Live CD/DVD out etc to remove install from the equation.

---

### Post by nooto_n on 2011-11-11
The system seems to be compromised afteral...

I get the same banner in almost every web page.. the banner has the following link (Deleted http in the beginning):

d.adroll.com/r/N34ZPOW5TRGMJKDEFHM2G4/UAZEVLFYKZGQPMOT77ULX3/e60920bf5ae3255a972365933dc487b9.re?ct=1&clickurl=http://adclick.g.doubleclick.net/aclk%3Fsa%3Dl%26ai%3DB3odhrHG9Tpr6KeOW0AXngMWXArK73pICwuLMnyOK7d_obwAQARgBIAA4AVCAx-HEBGC5u-0EggEXY2EtcHViLTkwNzkwNjEwNDAyMzQ2ODWgAeDgsewDsgEQd3d3LmxpZmVoYWNrLm9yZ7oBCTcyOHg5MF9hc8gBCdoBV2h0dHA6Ly93d3cubGlmZWhhY2sub3JnL2FydGljbGVzL3RlY2hub2xvZ3kvMTktZnJlZS1ndGQtYXBwcy1mb3Itd2luZG93cy1tYWMtbGludXguaHRtbJgCpA3AAgXIAtyIgwmoAwHoA-YG6APPCugD3AX1AwAAAMA%26num%3D1%26sig%3DAOD64_1Cmy5gTfb0xAnNW0bUIpTztFbwKA%26client%3Dca-pub-9079061040234685%26adurl%3D

Fresh install ... now ... :(

---

