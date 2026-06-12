---
title: "reporting the error -on every startup"
date: 2016-03-01
forum: Security
---

### Post by ashok_saini on 2016-03-01
[IMG]http://i.imgur.com/ZPNVxsK.png?1[/IMG]

getting report an error occurred message  on every startup .. asking for key.
is it normal .
ubuntu 15.10   Linux 4.2.0-30-generic

---

### Post by s0urCr34m on 2016-03-05
have you tried removing the apport package(s)?  Edit = apport is a program which "automatically generate[s] crash reports for debugging"  Output from dmesg near the end when you receive this message may help.  Are you experiencing problems with a particular program? Not able to login? Did you verify the ISO to be legit before using?  One of the first tasks I perform with a new install is to remove software like apport, because I don't need or want it.  You might find the program helpful and removal of it could mask a problem with your install, IDK. How long have you been using your install and have you experienced any other errors? If you're able to bypass this window, are you able to check & verify all of your Startup Applications to be legit?

---

