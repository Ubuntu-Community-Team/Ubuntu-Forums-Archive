---
title: "Wake-on-lan"
date: 2006-06-23
forum: Server Platforms
---

### Post by flash777 on 2006-06-23
Hi,

I'd like to enable Wake-on-lan on 6.06 server installation. Here are some questions that I have regarding this:

[LIST]
[*]Is The WOL support enabled by default?
[*]If not do I have to do something special to enable it?
[*]How would I know if it is enabled/disabled? Is there a certain command for that?
[*]I presume the hardware needs to support this feature. How can I tell whether my card does or not. I have a HP a1100y desktop and haven't found any documentation specifying what the network card is.
[/LIST]

Thanks in advance for your help!

---

### Post by jinx099 on 2006-06-23
[QUOTE=flash777]Hi,

I'd like to enable Wake-on-lan on 6.06 server installation. Here are some questions that I have regarding this:

[LIST]
[*]Is The WOL support enabled by default?
[*]If not do I have to do something special to enable it?
[*]How would I know if it is enabled/disabled? Is there a certain command for that?
[*]I presume the hardware needs to support this feature. How can I tell whether my card does or not. I have a HP a1100y desktop and haven't found any documentation specifying what the network card is.
[/LIST]

Thanks in advance for your help![/QUOTE]
Wake on lan has nothing to do with Ubuntu or any OS.  You need a WOL enabled NIC and to enable it in your BIOS.  depending on your motherboard, you may or may not need to plug in the WOL cable to the mobo (i believe most new mobos dont need it).

---

### Post by xxMEL0Nxx on 2006-07-07
> Wake on lan has nothing to do with Ubuntu or any OS. You need a WOL enabled NIC and to enable it in your BIOS. depending on your motherboard, you may or may not need to plug in the WOL cable to the mobo (i believe most new mobos dont need it).

You need to enable the WOL feature within your OS, windows enable this by default but with ubuntu you must do ```
ethtool -s eth0 wol g
``` this is for wake up with the magic packet for other options ```
man ethtool
``` also you need to disable the -i option from halt

---

### Post by eetbrood on 2006-08-03
Hey xxMELONxx,

thanks a million for this tip of enabling wol on the eth card, but with this thing i can only boot with WOL once, next time it seems like the system forgot the setting

Is there a way to make this more permanent? Or can i put it in some startup script?

running a fresh new ubuntu 6.06 (desktop) as a headless home server.


thanks,

eetbrood

---

### Post by wasauce on 2006-08-08
eetbrood,

 I have been having the same problem. I tried to setup a script to enable WOL on boot up but like you I am having trouble getting it to work everytime. Sometimes when i shutdown it works sometimes it doesnt and I have not been able to figure out why. 

check out this site for the script: [http://wasauce.blogspot.com/](http://wasauce.blogspot.com/)

also did you figure out the halt command that xxMELONxx mentioned?

i think I found and removed the -i in question but still no luck. Please tell me if you get it working. 

thanks,

 wasauce

---

### Post by HobbitTR on 2007-11-24
wasauce  I could not find the specific script, your link leads to the blog page but not the permanent link of the actual script.

Much thanks to xxMELONxx which led me to this:
[http://blog.timc3.com/2006/10/23/wakeonlan-nforce-and-ubuntu/]("http://blog.timc3.com/2006/10/23/wakeonlan-nforce-and-ubuntu/")
I followed the instructions here but it still would not wake on lan. 

Each time I shutdown my "headless" (remote) machine it would not wakeonlan so I manually restarted and did this: 
code:
 sudo ethtool eth0  
and each time I found this:
Wake-on: d
for some reason the /etc/network/interfaces file did not make the change permanent to Wake-on: g

I wrote a simple bash file which works for me. 
The bash file is this:
**********************
#/bin/bash
#
sudo ethtool -s eth0 wol g
sudo shutdown -h now
exit 0
**********************
First login to your "headless" machine 
(I use ssh) ssh -Y -l machinename 10.0.0.4

I made the bash file and named it shutoffpc 
you must  copy it to:
/usr/local/bin
then make it executable:
sudo chmod 755 /usr/local/bin/*

type shutoffpc.  This runs the bash file.

If all goes well the "headless" machine will shut down and allow you to wake on lan: 
code:
wakeonlan 00:0X:54:3X:0B:AX 
(the MAC address of the "headless" machine)

---

### Post by RothWerx on 2008-02-24
On my 7.10 machine, I created a script /etc/network/if-up.d/wol-enable with this in it:

#!/bin/bash
/usr/bin/sudo /usr/sbin/ethtool -s eth0 wol g

Works like a charm for me.

---

### Post by lowebb on 2008-02-25
Guys, I've Wake-on-Lan working great from inside my LAN but I cannot get it working over the Internet. I've found a number of post about this on the Internet but none detail to me the actual issue why it is not working.

It seems that your LAN needs to have a specific subnet mask (not 255.255.255.0) but I dont understand why this is or what it should be.

Does anyone here have any details on this? I'd appreciate the help. Thanks

---

### Post by boardtc on 2008-02-25
> **RothWerx said:**
> On my 7.10 machine, I created a script /etc/network/if-up.d/wol-enable with this in it:

#!/bin/bash
/usr/bin/sudo /usr/sbin/ethtool -s eth0 wol g

Works like a charm for me.

Sounds good. New to the WOL idea. How would I then execute this from my windows box to turn on/off the server...

just found
[http://ubuntuforums.org/showthread.php?t=234588&highlight=wol+server](http://ubuntuforums.org/showthread.php?t=234588&highlight=wol+server)

---

