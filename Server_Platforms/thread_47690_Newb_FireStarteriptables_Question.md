---
title: "Newb FireStarter/iptables Question"
date: 2005-07-09
forum: Server Platforms
---

### Post by linuxNewb on 2005-07-09
I am a linux newb, so I apologize if my question doesn't make sense, or is answered elsewhere. I've been unable find this an answer to this "basic functionality" question. I installed and configured (just by using the statup wizard) FireStarter as per the UbuntuGuide. Firestarter was decribed online as an iptables front-end. I'm trying to understand the basics...

Does firestarter need to be running (in the system tray) for my firewall to be active, or is Firestarter simply a front-end that configures iptables, which runs in the background even when Firestarter isn't running?

In other words, if FireStarter isn't in my system tray, is my "firewall" still protecting me?

---

### Post by linuxNewb on 2005-07-09
Found the answer. In case others have the same question...

"Quitting the program

A frequently asked is question is, what happens when you quit the program. The answer is that the firewall will keep functioning. If you are running Firestarter as a system service, which is automatically set up for you when installing Firestarter from a binary package, the firewall is in many cases even running before you start the program"

-- Taken from [http://www.fs-security.com/docs/tutorial.php](http://www.fs-security.com/docs/tutorial.php)

---

