---
title: "no internet"
date: 2008-10-23
forum: Server Platforms
---

### Post by adept_king on 2008-10-23
i have been sitting here for two days, googling my fingers off and i still cannot get onto the internet using my ubuntu server.

ubuntu desktop: i got on the internet in minutes
ubuntu server: still no internet for two days

---

### Post by Iowan on 2008-10-23
Post results of **ifconfig -a**, **lspci**, and contents of */etc/network/interfaces*.  Is the server set up for static address or does it get DHCP address?

---

### Post by adept_king on 2008-10-23
thank you very much for your reply.
all my gooling and whining finally paid off!

--

heres the elusive formula:

i first re-installed the 3945 driver.
then found a file called compatable old drivers or something.
made that, make installed it, make unloaded, make loaded.

then **iwconfig** shows lo, eth0, wmaster0 and wlan0

wlan0 is the one i wanted, it had info next to it. the others do not, so *ignoring them was my biggest lesson* of the day.

next:

**_sudo dhclient wlan0_** #(this command was *AWESOME* & my new obsession)

```
sudo iwlist scanning
``` #(to find what connection you want, take note of the name and the many coloned number. very very useful.)

sudo iwconfig wlan0 essid "netwhatever" #use to fix the name of the network if its wrong by some chance

sudo iwconfig wlan0 ap xxxxxx #replace the x's with the many coloned alphanumeric string found in iwlist scanning.

and if need be do this again:

**sudo dhclient** wlan0 #(you might have to replace wlan0 with your own special funny little word)

go ahead and ping google.com, hitting ctrl+c when you're tired of watching the results.

and better use 'sudo apt-get update' like crazy!

i came up for air and sudo apt-get install xmonad
...a little easier than one big scary bash window?

---

