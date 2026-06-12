---
title: "Remote power-down and wake up"
date: 2009-03-02
forum: Server Platforms
---

### Post by dnel on 2009-03-02
I have a server running in co-location running Ubuntu hardy. I've seen over the last 4 months of uptime the hard disk temp gradually rise, currently to 50 degrees C. 

At some point in the next few weeks I'll need to power down the hard disk to cool it off but visiting the box is not straightforward.

I'm not sure if the spin-down feature of hdparm will work as there are frequent database lookups from other users. I think I'll need to put the server into a low-power mode or power-off completely which is no problem but I was wondering if there's a method to get it to wake itself back up again after a few hours?

Any suggestions?

---

### Post by veloce on 2009-03-08
> **dnel said:**
> I have a server running in co-location running Ubuntu hardy. I've seen over the last 4 months of uptime the hard disk temp gradually rise, currently to 50 degrees C. 

At some point in the next few weeks I'll need to power down the hard disk to cool it off but visiting the box is not straightforward.

I'm not sure if the spin-down feature of hdparm will work as there are frequent database lookups from other users. I think I'll need to put the server into a low-power mode or power-off completely which is no problem but I was wondering if there's a method to get it to wake itself back up again after a few hours?

Any suggestions?

Since no one else has jumped in here:

A wake-on-lan type of approach will be hardware dependant and would probably require some bios configuration.

I think you'd be best to carry on the track of using hdparm to spin-down the disk.  You just need to add the ability to stop processes that will call on the hd while you're trying to get it to sleep.  Best would be to isolate all the processes and shut them down.  You could set up a script that shuts them down for an hour or two every night.

An alternative might be to put some temporary firewall rules in place that only allow your ssh session (or however you communicate) to interact with the machine. 


OR: you could get an auxiliary fan to cool the box. :-)

---

### Post by dnel on 2009-03-09
Thanks for your advice, certainly makes sense. I remember there was a command that shows me what processes were accessing what files but it escapes me, do you know of a way to trace the processes I need to stop?

Unfortuantely the drive in question is in a removable caddy which while it comes with a 40mm fan it seems to be mostly for show than any real practical cooling reasons :(

---

### Post by o891 on 2009-03-09
> 
I remember there was a command that shows me what processes were accessing what files but it escapes me, do you know of a way to trace the processes I need to stop?


Maybe top...[http://linux.about.com/od/commands/l/blcmdl1_top.htm](http://linux.about.com/od/commands/l/blcmdl1_top.htm)

Try:

```

top -i

```

Then you should be able to kill the processes using their IDs. Is this what you were looking for?

---

### Post by gsmg on 2010-02-25
In server room and on remote equipment we use (we internet provider) such device Elgato GSM-rebooter [http://elgato.com.ua/en/products/gsm-](http://elgato.com.ua/en/products/gsm-) for 6 outlets (220 V). Can control it by SMS or GSM-calling.  Every outlet controlled separately On/Off/Reset (Off and after pause - On) + temperature sensor with alarm by SMS, SMS-messages about Power loss and so on.. Usefull stuff! Save time on driving to other part of city for switch reset.

---

