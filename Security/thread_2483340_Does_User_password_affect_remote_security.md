---
title: "Does User password affect remote security?"
date: 2023-01-27
forum: Security
---

### Post by anotherChris on 2023-01-27
I installed the new Lubuntu 22.04 LTS.   I only have one user account, I have nothing to hide from my family, and I basically never take the laptop outside my home.  Therefore, [I set the SDDM.conf file to Autologin for my User, so that booting bypasses the log-in screen]("https://discourse.lubuntu.me/t/set-lubuntu-to-autologin-after-installation/3981").  My question is: does Autologin in any way affect the security of the computer from the perspective of remote attacks?  like, does the User password provide any kind of firewall-type protections from the Internet?

---

### Post by TheFu on 2023-01-27
Yes and no.  Depends on the networking architecture and security.
What do you do about house guests or uninvited intruders?
How do you remote to the different systems on the LAN?

---

### Post by anotherChris on 2023-01-27
> **TheFu said:**
> Yes and no.  Depends on the networking architecture and security.
What do you do about house guests or uninvited intruders?
How do you remote to the different systems on the LAN?

Because of my living circumstances, location, poverty, and benign contents of my laptop, house guests and intruders are not a concern.  I have a very simple set-up: modem, wi-fi router, a few devices that are not connected to each other (via bluetooth, eg, and no printers, projectors, etc).  Everything connects to the Internet via the wi-fi router.  I am interested to hear what security the User account password being turned on can supply in that situation, if any.  Thanks.

---

### Post by TheFu on 2023-01-28
Is this user with the automatic login also the sudo-user?  So anyone sitting behind the machine can run any root commands, even by accident?

Remote security comes down to which remote connection methods you have installed and enabled.  There are almost always remote hacks through unexpected methods. For a while, there was a weakness in DHCP that allowed remote logins, for example.  Once some gains access to the system, if there isn't a password needed for a user or to run administration commands, they own the machine completely.

In a perfect world, there wouldn't be any remote access flaws, but we don't live in that world.
In 2002, one of my systems was remotely hacked through DNS.  They got in, pulled some scripts down and tried to move from the "nobody" account to one with more privileges.  Fortunately, none of their 140K attempts to accomplish that worked.  I got an email for each attempt, so it was clear when the system was hacked.  

Once I setup a raspberry pi media player system to auto-login. This was convenient, since it was controlled via a remote control. No keyboard. No mouse connected.  Convenience won that battle, even for me, but the autologin was setup while still needing to enter a password for the user.  Generally, I manage and backup that system using ssh, which uses key-based authentication from another system on the LAN.

Always remember that other people on the LAN aren't necessarily your friends.  It is possible for a guest with a smartphone connected to wifi to hack your Linux system.  Just something else to consider.  BTW in 2016, my freshly installed and patch Ubuntu laptop was hacked without anyone touching it and it not being connected to any network.  I traced the hack back to bluetooth.  Seems Ubuntu enabled bluetooth, which I don't use, and someone nearby decided it would be fun to hack in.

Beware.

---

