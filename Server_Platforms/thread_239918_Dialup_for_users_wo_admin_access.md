---
title: "Dialup for users w/o admin access"
date: 2006-08-20
forum: Server Platforms
---

### Post by Coburn on 2006-08-20
I'm trying to set up a user account w/o root privileges (no sudo).

Trouble is, I'm using dialup, and the following tools require sudo to work properly:

wvdial
modem_applet
gnome-ppp

pon does not appear to work on my system.  Sorry, I've only been using Linux since January.  Is that because it's for broadband?

I have tried chmodding these applications and the associated devices and config files.  Certainly there are many other files I have not looked at.

What does one do to give dialup access to a non-privileged user?

Thanks,

Coby

PS I am reporting this as a bug when I get some time.  Enabling this access should not be like finding a needle in a haystack.

PPS
Athlon 2G machine w/ Dapper
Using Intel537EP modem via Intel driver (slmodemd not configured to work)

---

### Post by croak77 on 2006-08-20
It is not a bug its a group thing. For wvdial and ppp, you need to add the user to dialout and dip group. Then it should work for non-sudo user.

From a terminal;
```
sudo adduser *username* dip
```

---

### Post by Coburn on 2006-08-22
No offense, but have you actually tried this?

My problem seems to be that wvdial and modem_applet call other modules, e.g. /etc/wvdial.conf, ppp0, /dev/modem, that require root permissions to operate properly.  I have chmodded them, but the problem remains.  Apparently there are other, hidden modules that also require root access.

Alternatively, there may be a command that I am still unaware of that will correct this.

How about this command:  Somebody fix this feature in Gnome! :-)

---

### Post by croak77 on 2006-08-22
Yes I have, have you? Your user needs to be in both groups.

Admittedly, it has been a few years since I've used dialup, but that did work for me. What and how did you chmod? What does ls -l /dev/ttyS1 return? Replace ttyS1 with the location of your modem. And ls -l /etc/wvdial.conf?

---

### Post by Coburn on 2006-10-18
I did some further checking.  My problem seems to be with ppp.  For security reasons it is set up to not allow normal users access.  The suggested remedy is to make a copy of /etc/ppp/chap-secrets with the user's name attached.  My 45-year-old brain is getting stiff like my legs, so I haven't quite figured out how to try it yet.  But it sounds relatively simple in the pppd manpages.

---

### Post by Coburn on 2006-11-24
> **Coburn said:**
>  ... It sounds relatively simple in the pppd manpages.

Info pppd says:

> When opening the device, pppd uses either the invoking user’s  user  ID
or  the root UID (that is, 0), depending on whether the device name was
specified by the user or the system administrator.  If the device  name
comes from a privileged source, that is, /etc/ppp/options or an options
file read using the call option, pppd uses full  root  privileges  when
opening  the  device.   Thus,  by  creating  an  appropriate file under
/etc/ppp/peers, the system administrator can allow users to establish a
ppp  connection via a device which they would not normally have permission to access.  
Otherwise pppd uses the invoking user’s real UID  when
opening the device.

Further looking shows that you must copy /etc/ppp/chapsecrets to /etc/ppp/peers/username and tweak it to reflect their information, and then "call" it during the invocation of pppd.  Or something like that--I don't remember exactly.

Sounds like some serious HVAC work:  "bash to fit, paint to match." 

Has somebody done this that could give me the steps?  I am using chapsecrets "*".

Thanks

---

