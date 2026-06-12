---
title: "discover and connect to wireless in command line"
date: 2008-10-23
forum: Server Platforms
---

### Post by adept_king on 2008-10-23
in the gui version of ubuntu, networks are found automatically and presented in a list.  

in ubuntu server, i guess i could search for random ip's using nmap or something, but what if i dont know the range to search?  in short, how do i get connected to one of these wireless networks if i dont even know which ip's they are?  i -really- want to figure this out, but i am days behind schedule.  i have a week to learn everything there is to know about running a linux server.  ha. ha. ha.

my wireless adapter is recognized and i think it works, but i would sure like to 'test it.'

my platform is in my sig.

---

### Post by lykwydchykyn on 2008-10-23
To scan for networks:
```

sudo iwlist eth0 scanning

```
Configuring wireless can be done with iwconfig.  Check the man page for syntax and commands.  I don't think it deals with WPA, though; I never quite got a handle on how to deal with wpa from the CLI.

---

### Post by cariboo on 2008-10-23
Are you saying that you don't know your wireless routers ip address?

Jim

---

### Post by adept_king on 2008-10-23
here is the answer as i found it:

i first re-installed the 3945 driver. 
then found a file called compatable old drivers or something.

then iwconfig shows lo, eth0, wmaster0 and wlan0

wlan0 is the one i wanted, it had info next to it.

so...

sudo dhclient wlan0

sudo iwlist scanning  #(to find what connection you want, take note of the name and the many coloned number)

sudo iwconfig wlan0 essid "netwhatever"

sudo iwconfig wlan0 ap xx:xx:xx:xx:xx

and if need be

sudo dhclient wlan0 

and better use 'sudo apt-get update' like crazy!

i came up for air and sudo apt-get install xmonad

a little easier than one big bash window.

---

### Post by go_beep_yourself on 2010-02-28
> **cariboo907 said:**
> Are you saying that you don't know your wireless routers ip address?

Jim

You do not need to know the ip address of any of the APs, just the essid.

Example:

sudo iwconfig wlan0 essid "bestcoffee"

---

