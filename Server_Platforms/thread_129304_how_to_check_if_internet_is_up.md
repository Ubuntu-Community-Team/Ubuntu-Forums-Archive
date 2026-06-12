---
title: "how to check if internet is up?"
date: 2006-02-13
forum: Server Platforms
---

### Post by art2003 on 2006-02-13
I have setup a ubuntu server running 24 hours a day.
It has usb modem ADSL connection to the internet (ppp0)
and a lan connection (eth0)
shorewall is running happily providing firewall services and internet connectivity to all clients in the LAN.
the command pon is set to activate the ADSL connection and poff de-activates it.
The problem is that sometimes pppd is running ok but the internet connexion has stalled and I need to log on and run poff and pon manually to fix the problem.

I wonder if somebody has a script that I could run with cron to check if internet is up and if it is not, then do a poff and pon

I think a fair way to establish if the internet connection has died is to check if 3 well known web sites such as [www.xxx.com](www.xxx.com) [www.yyy.com](www.yyy.com) and [www.zzz.com](www.zzz.com) are responding on port 80. If none of them are then it is safe to assume the ADSL connection need restarting.

Also if there is a package that has this functionality please let me know and I will be happy to install it!

Many thanks!
Art2003

---

### Post by majikstreet on 2006-02-13
ping -c4 google.com
ping -c4 microsoft.com
ping -c4 yahoo.com

that's good enough :D

---

### Post by art2003 on 2006-02-13
That is hardly an automated script.
I can also try a web browser and if I notice internet is down ssh to the server and type poff and pon myself
no need for the pings. isn't that great?

My question is how to make this proving automatically as part of a script I can have running in cron say every 3 minutes.

---

### Post by nagilum on 2006-02-13
I don't have a tested script but maybe something like the following is already sufficient. $HOSTX is 1 if the host was online, 0 otherwise.

```

#!/bin/bash

# timeout 5, zero IO mode (for scanning)
HOST1=$(netcat -z -w 5 www.xxx.com 80 && echo 1 || echo 0)
HOST2=$(netcat -z -w 5 www.yyy.com 80 && echo 1 || echo 0)
HOST3=$(netcat -z -w 5 www.zzz.com 80 && echo 1 || echo 0)

# do poff/pon if none of the hosts answered
if [ $HOST1 == 0 && $HOST2 == 0 && $HOST3 == 0 ]; then
   poff
   pon
fi

```

HTH

---

### Post by art2003 on 2006-02-13
nagilum, thanks a lot for the script, looks good however it throws a little error:

line 9: [: missing `]'


------
line 9 corresponds with the if line 
I did copy and paste so both [ and ] are in that line.

Any ideas?

---

### Post by Zimmer on 2006-02-13
[http://linuxreviews.org/beginner/Bash-Beginners-Guide/en/x3874.html](http://linuxreviews.org/beginner/Bash-Beginners-Guide/en/x3874.html)

Try double braces as per the examples in the above link...
if [ [ $HOST1 == 0 && $HOST2 == 0 && $HOST3 == 0 ] ] ; then

---

### Post by art2003 on 2006-02-14
thanks the double braces work!

Now I am thinking of also checking whether my ISP's router answers a ping request.

ifconfig ppp0 gives me this:
 ppp0      Link encap:Point-to-Point Protocol
          inet addr:123.xxx.xxx.xx  P-t-P:**123.yyy.yyy.17**  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:598978 errors:0 dropped:0 overruns:0 frame:0
          TX packets:800296 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:301304850 (287.3 MiB)  TX bytes:131652623 (125.5 MiB)

How can I 'extract' the **123.yyy.yyy.17** bit and say assigned it to $router so I can ping it as part of the script? with ping -c4 $ router or with netcat as in the above postings.

---

### Post by robert_pectol on 2006-02-14
> How can I 'extract' the 123.yyy.yyy.17 bit and say assigned it to $router so I can ping it as part of the script? with ping -c4 $ router or with netcat as in the above postings.
Pretty easily with:
```

router=`ifconfig ppp0 | grep 'addr' | awk '{$1=$1;print}' | cut -d ':' -f3 | cut -d ' ' -f1 | sed 's/^[ \t]*//;s/[ \t]*$//'`

```
...which should work if the output of, "ifconfig ppp0" is as you've posted.  I don't have a ppp interface on my box with which to test it though.  Anyhow, good luck.

---

### Post by art2003 on 2006-02-14
Thanks Robert works perfectly!
I know a bit of bash but awk sed and their powerful but cryptic switches are beyond me. Is there a good website where to learn this sort of bash stuff?

---

### Post by robert_pectol on 2006-02-14
There are several tutorials on the Web for both sed and awk.  Just google, "sed tutorial" and, "awk tutorial" and you'll get quite a few hits.  Anyway, to get you started, here are a couple of cheat sheets that I use for sed and awk:
[http://www.student.northpark.edu/pemente/sed/sed1line.txt](http://www.student.northpark.edu/pemente/sed/sed1line.txt)
[http://www.student.northpark.edu/pemente/awk/awk1line.txt](http://www.student.northpark.edu/pemente/awk/awk1line.txt)

Piping command output to sed and awk is extremely easy in scripts, too.  Also, I use cut a lot.  Pull the manpage for 'cut' for more info.  Hope that helps.

---

