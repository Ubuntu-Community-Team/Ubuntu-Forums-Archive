---
title: "Question about Freeradius"
date: 2014-03-31
forum: Server Platforms
---

### Post by thomas.l.hull on 2014-03-31
I have a small network on my desk, a Cisco 2960G I configured to replicate a switch on my actual network, and the FreeRadius server  plugged in directly to this switch. The switch is not actually connected to our actual network but used only as a test switch. My question is does the server need to have an active internet connection so that free radius can access the Ubuntu archive mirror in order to work?

 I can ping from switch to server and back however; I can not log into the switch using the username and password  I created on the server. The switch has been properly configured as well.


Any insight would be very much appreciated. Thank you!

---

### Post by koenn on 2014-03-31
> **thomas.l.hull said:**
> My question is does the server need to have an active internet connection so that free radius can access the Ubuntu archive mirror in order to work?
No. Radius doesn't relay on anything on the internet, and the archive mirror is just a repository of installable software and updates. 


> **thomas.l.hull said:**
> 
 I can ping from switch to server and back however; I can not log into the switch using the username and password  I created on the server. The switch has been properly configured as well.

What is your Radius server supposed to do ? What is it for ?
AFAIK, RADIUS is about **network** access - i.c. about allowing or disallowing network access to a host plugged in into one of the switch's ports. Authenticating access to your switch's  management tool (its CLI or a web-based management environment)  has nothing to do with that.

---

### Post by thomas.l.hull on 2014-04-01
Ok thank you for taking the time to  clear that up for me. The intention is to use Radius to monitor the users accessing our network. Radius has been a bit of a learning curve as I have never used it before.

---

### Post by koenn on 2014-04-01
> **thomas.l.hull said:**
> Ok thank you for taking the time to  clear that up for me. The intention is to use Radius to monitor the users accessing our network. Radius has been a bit of a learning curve as I have never used it before.
I don't have much experience with it myself.
And yes, it's rather versatile - it can do a lot of different but related things - which makes it confusing if you just try to learn it by doing.

It helps to remember what RADIUS is for : it controls access to a network - that includes dial-in with modems, connecting to a switch port, or getting connected to a wireless access point. Between the physical connection (a wire, a cable, a radio wave) and  actually getting "on the network" (access to a dhcp server so you can get an address, regular IP-level access to hosts on the network), RADIUS will interject an authentication stage  - which  can take several forms ; RADIUS might expect a device to authenticate by means of SSL certs, or it might prompt the user for a username and password. A username/password pair might be checked against RADIUS's own user database or against an external system such as LDAP or MS-ADS.  And so on. 
It's those options that you have to choose between and configure. 


Also remember that the devices (computers, ...) that you want to allow on the network may need to have their network cards configured to support this. I think the term for that is NAC (Network Access Control) but I don't quite remember the details.  You may want to look that up.
 
Have fun.

---

### Post by thomas.l.hull on 2014-04-03
Thank you for the break down on Radius Koenn! Its been a learning curve but I am having a pretty good time playing around with Ubuntu and Radius as a whole.

---

### Post by m-dw on 2014-04-05
> **thomas.l.hull said:**
> I can not log into the switch using the username and password  I created on the server. The switch has been properly configured as well.


Any insight would be very much appreciated. Thank you!

A couple of thoughts.

[LIST=1]
[*](and most important) What do the RADIUS logs on the server say?  They can usually tell you if the switch is actually communicating with the server, and often why it didn't allow you to log in.  If the login attempt isn't recorded, it probably means that the switch isn't talking to the server.
[*]Have you proved that RADIUS is actually working?  Do you have a test client on the server to check?
[*]Do you have a PC (or MAC) with a test client installed?  Is it only the switch that isn't working?
[*]Have you tried setting up AAA on the switch to use RADIUS? Don't lock yourself out in the process, just set it on line con0 _or_ line vty 0 4 not both, and keep an active connection when testing.  Does the server respond?
[/LIST]

I don't know the freeradius product but I've configured a lot of network kit to authenticate against RADIUS, and the first place to troubleshoot is in the server logs.

---

### Post by frankerooney on 2014-04-07
Freeradius is pretty straightforward to test : make sure it's not running as a service first - 

service stop freeradius
or pgrep freeradius and kill -9 the process id

then run it in "diagnostic mode"

freeradius -X

when you log into your switch you should see lots of text on the screen and it's then pretty straightforward to find out why it's not working.

Planning a network - wide (i.e. all user) port based freeradius setup is not a small job, but is quite possible. Factor in HA - most NAS's will fail over automatically, so at least have a couple of instances of freeradius with the same config on a couple of servers.
We use it for all our network and wireless auth, and go as far as doing automatic switch backups following logging out of a switch for example.
Freeradius is a good choice by the way, probably the best I've seen for radius so far (and it's free).

---

