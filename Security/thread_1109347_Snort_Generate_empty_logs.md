---
title: "Snort Generate empty logs"
date: 2009-03-28
forum: Security
---

### Post by madman100 on 2009-03-28
Hi can any one help got snort installed and running but when i check the logs they are empty and  all so have Base setup that too is empty 

Thanks
madman100
:confused:

---

### Post by bodhi.zazen on 2009-03-28
Please post a screen shot of base, that will tell me if all is well with the install.

If snort does not issue an alert every now and again, the connection with the mysql database is lost. The only solution is to re-start snort.

I re-start snort every 6 hours with a cron script, but I do not know if you cna go 12 or 24 hours.

The other way to test snort is to port scan yourself (or similar) and see if it shows in base.

---

### Post by madman100 on 2009-03-28
Hi bodhi.zazen i did insall the script and set it to restart every 6 hours i have all so tested snort with a scan and still did not generate any thing in base here are the screen shots 

Thanks 
madman100

---

### Post by bodhi.zazen on 2009-03-28
It appears to be working.

On the home page, do you see the "sensors 0/2"

base is seeing two sensors, probably times when you started snort with different options.

It appears there have simply been no alerts.

Go ahead and go to the administration page and clear your data bases, "sensors" on the home page will now read " 0 / 0 "

Re-start snort and you will see it change to " 0 / 1 "

The first digit is the number of sensors which have detected an alert, the second number is the number of sensors (you can run a central mysql server and encrypt snort traffic over ssh for example).

Then, once you have re-started snort, scan your box with something ;)

You should should then see some alerts ;)

Unless the traffic is being blocked by OSSEC or iptables ;)

---

### Post by madman100 on 2009-03-29
Hi bodhi.zazen  thanks for the reply i clear the sensors and done some scans from other machines but still the same problem so i will install snort and base of a different machine to see if that makes any difference 


Thanks 
madman100

---

### Post by madman100 on 2009-04-03
Hi bodhi.zazen i have install snort and base to other machines on the network and they all have the same problem with on alerts i have even tried Network Security Toolkit witch as snort and base installed and got the same problem with on alerts  

Thanks 
madman100

---

### Post by bodhi.zazen on 2009-04-03
It is hard to tell from your post what your problem is.

First it would help if you were to log into base, clear the data, you should then see 0 / 0 in the sensors line.

Next re-start snort -> you should then see 0 / 1 in  the sensors line. If you do NOT see that, you have a problem with snort.

If you do, you next need to use a port scanner from another box to test snort.

If you do not get an alert, tell us what you used and how you used it.

Snort will not log an alert if traffic is blocked by iptables or something like ossec, so we need to know something about your firewall settings.

If snort does not log an alert, it loses it's connection to the mysql data base, so if you are seeing no activity, snort needs to be restarted from tome to time. I do not know how long you can go, I restart snort every 6 hours with a cron job.

Once you get snort running on a single machine, then work on your network.

I suggest you put snort / base on a box off your router. You can get a smatr switch with a port to monitor all network traffic.

If you prefer multiple snort deployments, configure snort to log to a central server. The central server will run mysql and apache / base and the client swill send data to mysql over ssh.

As you can see, you have a long list of issues to work through and you need to go one step at a time and provide us with more information.

---

### Post by madman100 on 2009-04-03
HI bodhi.zazen i have log in to base and clear the data to 0/0 and i have restarted snort and now i see 0/1 i have taken the snort box of the network it is connected now to only modem and not the router now done i online port scan this is the results 

Scanning ports on 86.49.30.79

86.49.30.79 isn't responding on port 21 (ftp).
86.49.30.79 isn't responding on port 23 (telnet).
86.49.30.79 isn't responding on port 25 (smtp).
86.49.30.79 is responding on port 80 (http).
86.49.30.79 isn't responding on port 110 (pop3).
86.49.30.79 isn't responding on port 139 (netbios-ssn).
86.49.30.79 isn't responding on port 445 (microsoft-ds).
86.49.30.79 isn't responding on port 1433 (ms-sql-s).
86.49.30.79 isn't responding on port 1521 (ncube-lm).
86.49.30.79 isn't responding on port 1723 (pptp).
86.49.30.79 isn't responding on port 3306 (mysql).
86.49.30.79 isn't responding on port 5900 ().
86.49.30.79 isn't responding on port 8080 (webcache).

still no alerts in base and lots of snort log but when i open them they are empty

---

### Post by bodhi.zazen on 2009-04-03
OK, well it is likely working then as the sensors are updated from 0 / 0 to 0 / 1

You are likely not getting sufficient traffic as of yet.

use another tool

[http://www.cirt.net/nikto2](http://www.cirt.net/nikto2)

---

### Post by Dr Small on 2009-04-03
Just a simple question, which is probably unnecessary.
Do you have any rules in /etc/snort/rules/ ?

If there are no rules, then snort probably can't preform any alerts (but then again, I just learning snort myself).

---

### Post by madman100 on 2009-04-04
hi Dr Small yes in have the rules installed in /etc/snort/rules


Thanks
madman100

---

### Post by madman100 on 2009-04-04
Hi bodhi.zazen did a scan with nikto but when i restart snort the snort logs are still empty after checking over the system i have found that OSSEC is not installed i have now installed this but when trying to usermod -G ossec -a www-data
i get usermod: unknown group ossec 
do i need this software to get the snort logs to write 

Thanks
madman100

---

### Post by Dr Small on 2009-04-04
> **madman100 said:**
> hi Dr Small yes in have the rules installed in /etc/snort/rules


Thanks
madman100
Ok. Here's another question for you (since I can't see where you otherwise stated it); Did you install snort-mysql from the repositories, or did you compile and configure snort from source (as per bodhi.zazen's guide)?

Sorta the reason I ask, is because when it is installed from the repositories, it had a glitch somewhere and would not start. It said it started, when running `/etc/init.d/snort start`, but when viewing the status, it said it was not.

---

### Post by bodhi.zazen on 2009-04-04
Well you do not *need* ossec, but it does not hurt either.

You will have to turn it off since it does block some traffic and thus snort will not throw an alert.

To install ossec, follow my guide. I just ran the script ...

usermod -G www-data -a ossec

Good question, how did you install snort ? I have found the repositories not so good, better to compile.

---

### Post by madman100 on 2009-04-04
hi dr small in install snort and compile and configure snort from source as per bodhi.zazen's guide

---

### Post by madman100 on 2009-04-04
hi bodhi.zazen the only thing that i have not check it the iptables i all so have firestarter installed on the systems  

Thanks
madman100

---

### Post by bodhi.zazen on 2009-04-04
Turn off firestarter (allow all traffic), restart snort, and hit it again with a port scanner.

---

### Post by madman100 on 2009-04-06
hi bodhi.zazen turn off firestarter and id not make any difference thanks for all you help with this 


Thanks
madman100

---

### Post by Dr Small on 2009-04-06
> **madman100 said:**
> hi bodhi.zazen turn off firestarter and id not make any difference thanks for all you help with this 


Thanks
madman100
Hmm. This is strange indeed.
What is your network interface type? Ethernet or Wireless?

---

### Post by bodhi.zazen on 2009-04-06
You will need to provide more detail. Simply stating that it is not working is insufficient.

You have mentioned everything from firestarter to ossec.

did you re-start snort ?

what command are you using to start snort ? what happens when you start snort manually ?

screen shot of base please.

and output of nikto.

---

### Post by madman100 on 2009-04-08
hi bodhi.zazen thanks for all your help snort is now working done a clean install on  another pc and now base is  fully working as well 

Thanks
madman100

---

### Post by bodhi.zazen on 2009-04-08
SWEET :)

I am very glad to hear you got it sorted out. Do you know what went wrong with your previous attempt ?

I hope it may help others.

---

### Post by madman100 on 2009-04-09
hi bodhi.zazen i do not know what went wrong with the other machines could be some previous application or not full install just upgrades from 7.10 to 8.10  do not really know but it sames it ok  now that i have done a clean install on that machine so will do clean install on all the other machines 

Thanks 
madman100

---

