---
title: "Connecting Computers"
date: 2006-11-18
forum: The Cafe
---

### Post by urukrama on 2006-11-18
Here is a simple question I've never figured out how to solve:

*How do I connect two computers with each other, not using the internet?*

I have two computers I'd like to connect to each other (a laptop and a desktop), mainly to transfer files, but I've never figured out how to connect them (in Windows and Ubuntu).

Both run Ubuntu Dapper now; the Desktop also has ZenWalk on a partition. I tried using the network cards and an ethernet cable, I tried with a serial port cable, but they don't seem to recognise each other (both in Windows and Ubuntu). ](*,) 

How do I easily connect them?

---

### Post by mips on 2006-11-18
The ethernet cable has to be a cross-over cable.

Configure IP address on both sides in the same network.
Enable NFS

---

### Post by Portable_Jim on 2006-11-18
> **urukrama said:**
> ...I tried using the network cards and an ethernet cable...

What type of Network cable did you use? is it a Crossover cable?

---

### Post by CPtAJ on 2006-11-18
YKnow, I thought by now NICs would support transfer over either cable configuration. It would be a simple matter to engineer a way for them to switch the wire order onboard if needed. God knows some routers/switchers do this and it works out great.

Anyway, yeah. You probably need a crossover cable. They're real cheap to get and look exactly like your ethernet cables.

---

### Post by InsomniacUK on 2006-11-18
Definitely use a cable. Don't be tempted to try and connect two computers via wireless. It can be a *nightmare* to get working.

---

### Post by Engnome on 2006-11-18
> **CPtAJ said:**
> YKnow, I thought by now NICs would support transfer over either cable configuration. It would be a simple matter to engineer a way for them to switch the wire order onboard if needed. God knows some routers/switchers do this and it works out great.

Anyway, yeah. You probably need a crossover cable. They're real cheap to get and look exactly like your ethernet cables.

I've had success connecting two computer with a non cross-over cable.

The difference with cross-over cable can be seen if you hold two ends next to each other, in a straight cable they match up. In a cross over cable they are shuffled.

---

### Post by CPtAJ on 2006-11-18
> **Engnome said:**
> I've had success connecting two computer with a non cross-over cable.

The difference with cross-over cable can be seen if you hold two ends next to each other, in a straight cable they match up. In a cross over cable they are shuffled.

Yup.

[http://www.prismproductivity.com/support/Making%20Crossover%20Cables.htm](http://www.prismproductivity.com/support/Making%20Crossover%20Cables.htm)

---

### Post by urukrama on 2006-11-20
Thanks for all the help. I got a crossover cable, and have tried to set things up, but haven't been succesful so far. (installed nfs and ssh-server, but can't seem to reach my other computer)

Too tired now to try further, but I'll give it another go tomorrow or the day after.

---

### Post by mips on 2006-11-20
> **Engnome said:**
> I've had success connecting two computer with a non cross-over cable.


That is usually only possible when you have Gigabit NICs as they have the ability to do internal MDI/MDI-X swtiching.

---

### Post by DoctorMO on 2006-11-20
set up the network addresses and ping the other network address before you try and use any of that fancy stuff.

---

### Post by christhemonkey on 2006-11-20
Also, you mentioned serial cable connections.

This is possible, but an utter PITA to setup an then with very very slow data transfer speeds, almost not worth it.

Just my opinion.

And make sure you set your ip adresses in networking config to **static** (unless you have a dhcp server installed and configured....) then hopefully you should be able to ping each other as DoctorMo suggested.

```
ping xxx.xxx.xxx.xxx 
```

Where xxx.xxx.xxx.xxx is the ip adress of the other machine. (and xxx is a number freom 1 - 254 (maybe?))

---

### Post by deanlinkous on 2006-11-20
sounds like you are trying too hard
#crossover cable between the two
#go into system>administration>networking and set the ipaddress on computer1 to 192.168.1.1 and netmask to 255.255.255.0 then on the second computer set the ipaddress to 192.168.1.2 and the netmask to 255.255.255.0
#choose a folder on each computer that you want to "share" with the other one, right-click on the folder and choose 'share folder'
#after that you should  be able to browse netwrok servers and see your shares

*did I leave anything out*

---

### Post by Gargamella on 2006-11-20
> **InsomniacUK said:**
> Definitely use a cable. Don't be tempted to try and connect two computers via wireless. It can be a *nightmare* to get working.

i do not agree I share music with all my house via wireless.And on Ubuntu works good.

---

