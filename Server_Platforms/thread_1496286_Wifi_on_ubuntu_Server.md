---
title: "Wifi on ubuntu Server"
date: 2010-05-29
forum: Server Platforms
---

### Post by Brando753 on 2010-05-29
Hello There.
I have been searching for hours to find a way to connect my Ubuntu Server 10.4 to a wifi network as I am in a situation where it is impossible to be wired in. I have looked in many forums, been on IRC, and googled till I almost lost it](*,), I have been able to scan and pick up my wifi router but have been unable to connect as it is encrypted. 

What I am asking for is not a bunch of links to forums and manuals [-Xas I have tried them all to no avail. I am simply asking for what do I enter into the CL if my ESSID: "Superlink1" and Password is "onetwothree123"<--- not actual password, and its WPA encryption.

Thanks to everyone who has looked and commented ahead of time this is very much appreciated.=D>

---

### Post by Bachstelze on 2010-05-29
Since it's WPA, you'll need wpasupplicant:

[https://help.ubuntu.com/community/WifiDocs/WPAHowTo#WPA%20Supplicant](https://help.ubuntu.com/community/WifiDocs/WPAHowTo#WPA%20Supplicant)

---

### Post by Brando753 on 2010-05-29
I have already viewed that page, made the config file, but wasn't sure what I had to do next. So if someone will post the CL code to enter it would be much obliged.

---

### Post by Brando753 on 2010-05-30
For anyone having troubles with this I found my solution through this great guide [http://modelr.wordpress.com/2009/06/01/how-to-get-wireless-network-on-ubuntu-server/](http://modelr.wordpress.com/2009/06/01/how-to-get-wireless-network-on-ubuntu-server/) 

Just go to the section to get WPA working 

Good luck to all

---

