---
title: "Block 1 program from accessing internet"
date: 2011-04-05
forum: Security
---

### Post by corkscrew on 2011-04-05
Is there anyway by use of a firewall to prevent a user from starting a program which  accesses a particular service to the internet during a certain time period

---

### Post by SeijiSensei on 2011-04-05
This sounds a lot like your other question today.  You can add a task to /etc/crontab that would add an iptables rules blocking the connections you wish to stop at the beginning of the time period.  A second iptables rule at the end of the period would delete the rules.  

For instance, adding these entries with "sudo nano /etc/crontab":

```

30 00 * * * root iptables -I INPUT -p tcp --dport 80 -j DROP
00 06 * * * root iptables -D INPUT -p tcp --dport 80 -j DROP

```

would block connections to remote web servers from 00:30 to 06:00.

---

### Post by corkscrew on 2011-04-05
> **SeijiSensei said:**
> This sounds a lot like your other question today.  You can add a task to /etc/crontab that would add an iptables rules blocking the connections you wish to stop at the beginning of the time period.  A second iptables rule at the end of the period would delete the rules.  

For instance, adding these entries with "sudo nano /etc/crontab":

```

30 00 * * * root iptables -I INPUT -p tcp --dport 80 -j DENY
00 06 * * * root iptables -D INPUT -p tcp --dport 80 -j DENY

```

would block connections to remote web servers from 00:30 to 06:00.

Hey thanks this is just the sort of help I need yes I re worded the question after doing more research

How would I do the above commands for an ip range of 199.59.148.0 to 199.59.148.150  the program uses https port 443

Also will this work on a machine which is behind a router?

---

### Post by SeijiSensei on 2011-04-05
> **corkscrew said:**
> Hey thanks this is just the sort of help I need yes I re worded the question after doing more research

How would I do the above commands for an ip range of 199.59.148.0 to 199.59.148.150  the program uses https port 443

Also will this work on a machine which is behind a router?

Is that the range of destination addresses?  Do you care if .151-254 are also blocked?  Otherwise I'd need to do some calculations to figure out the right netmask to (approximately) cover that range.

```
30 00 * * * root iptables -I INPUT -p tcp -d 199.59.148.0/24 --dport 443 -j DROP
00 06 * * * root iptables -D INPUT -p tcp -d 199.59.148.0/24 --dport 443 -j DROP
```

works for all addresses with a 199.59.148. prefix.

On a single machine behind a router, you might need to replace INPUT with OUTPUT in those rules, though I believe either will work.

---

### Post by corkscrew on 2011-04-05
> **SeijiSensei said:**
> Is that the range of destination addresses?  Do you care if .151-254 are also blocked?  Otherwise I'd need to do some calculations to figure out the right netmask to (approximately) cover that range.

```
30 00 * * * root iptables -I INPUT -p tcp -d 199.59.148.0/24 --dport 443 -j DENY
00 06 * * * root iptables -D INPUT -p tcp -d 199.59.148.0/24 --dport 443 -j DENY
```

works for all addresses with a 199.59.148. prefix.

On a single machine behind a router, you might need to replace INPUT with OUTPUT in those rules, though I believe either will work.

No the ip range from 151 to 254  wouldn't matter.The way I am getting these ip's is by letting the program in question run (tweetdeck) then running ```
lsof -Pnl +M -i4
``` to find the range of ip's it is using all the ip's for TCP on https 443 fall in this range there are a bunch of others accessing port 80 but i thought i would start with these.

---

### Post by corkscrew on 2011-04-05
> **corkscrew said:**
> No the ip range from 151 to 254  wouldn't matter.The way I am getting these ip's is by letting the program in question run (tweetdeck) then running ```
lsof -Pnl +M -i4
``` to find the range of ip's it is using all the ip's for TCP on https 443 fall in this range there are a bunch of others accessing port 80 but i thought i would start with these.

I need help here I tried a practise run first just to see if i could block google without the time so I typed
```
sudo iptables -I INPUT -p tcp -d 209.85.229.0/24 --dport 80 -j DENY

```
which resulted in
```
iptables v1.4.4: Couldn't load target `DENY':/lib/xtables/libipt_DENY.so: cannot open shared object file: No such file or directory
```

then I tried
```
cem@vb-lucid:~$ root iptables -I INPUT -p tcp -d 209.85.229.0/24 --dport 80 -j DENY
```
The program 'root' is currently not installed.  You can install it by typing:
sudo apt-get install root-system-bin
 I then installed root and tried same command again and got
```

Warning in <TApplication::GetOptions>: macro iptables not found
Warning in <TApplication::GetOptions>: macro INPUT not found
Warning in <TApplication::GetOptions>: macro tcp not found
Warning in <TApplication::GetOptions>: macro 209.85.229.0/24 not found
Warning in <TApplication::GetOptions>: macro 80 not found
Warning in <TApplication::GetOptions>: macro DENY not found
  *******************************************
  *                                         *
  *        W E L C O M E  to  R O O T       *
  *                                         *
  *   Version  5.18/00b     10 March 2008   *
  *                                         *
  *  You are welcome to visit our Web site  *
  *          http://root.cern.ch            *
  *                                         *
  *******************************************

ROOT 5.18/00b (branches/v5-18-00-patches@22563, Apr 06 2010, 02:11:00 on linuxx8664gcc)

CINT/ROOT C/C++ Interpreter version 5.16.29, Jan 08, 2008
Type ? for help. Commands must be C++ statements.
Enclose multiple statements between { }.
root [0] 

```

I'm stuck??

---

### Post by bodhi.zazen on 2011-04-05
Become root with ```
sudo -i
```

Then run the iptables command in the terminal.

You might also want to iptables-save and iptables-restore or iptables-apply

See also:

[http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

You can use time in iptables, but in that event you would use OUTPUT rather then INPUT

[http://bodhizazen.net/Tutorials/iptables#Additional_Tips](http://bodhizazen.net/Tutorials/iptables#Additional_Tips)

If you are going to use INPUT you want -s ip_to_block
If you are going to use OUTPUT you want -d ip_to_block

Time stamps do not work so well in the INPUT chain ;)

You can thus specify a rule , in OUTPUT, for a specific user, group, time, port, or use multiport

```
iptables -A OUTPUT -o eth0 -p tcp -m owner --uid-owner 1001 -m multiport --dports 80,443 -m time --timestart 12:00 --timestop 13:00 -j ACCEPT

iptables -A OUTPUT -p tcp -m multiport --dports 80,443 -j DROP
```

Would allow user 1001 to use "the internet" only during lunch hour.

---

### Post by SeijiSensei on 2011-04-05
My bad.  The destination chain, as bohdi.zazen's posting reminds us, is "DROP" not "DENY".  You can also use "REJECT" which tells the remote that the connection was refused.  DROP just ignores the traffic altogether.

---

### Post by corkscrew on 2011-04-06
> **bodhi.zazen said:**
> Become root with ```
sudo -i
```

Then run the iptables command in the terminal.

You might also want to iptables-save and iptables-restore or iptables-apply

See also:

[http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

You can use time in iptables, but in that event you would use OUTPUT rather then INPUT

[http://bodhizazen.net/Tutorials/iptables#Additional_Tips](http://bodhizazen.net/Tutorials/iptables#Additional_Tips)

If you are going to use INPUT you want -s ip_to_block
If you are going to use OUTPUT you want -d ip_to_block

Time stamps do not work so well in the INPUT chain ;)

You can thus specify a rule , in OUTPUT, for a specific user, group, time, port, or use multiport

```
iptables -A OUTPUT -o eth0 -p tcp -m owner --uid-owner 1001 -m multiport --dports 80,443 -m time --timestart 12:00 --timestop 13:00 -j ACCEPT

iptables -A OUTPUT -p tcp -m multiport --dports 80,443 -j DROP
```

Would allow user 1001 to use "the internet" only during lunch hour.

Thanks very much for taking the time to try and help me with this. I can see I am right out of my depth here!! I will need to take the time to study the material from the links you have posted.

I think I have come up with an easier solution to blocking the program in question for users on my LAN but not sure if you can help or if you could point me in the right direction

I have used the GUI Scheduled Tasks to create a cron job to pkill the program every minute between the hours of 01:00 and 07:00.
Is it possible to write a script to shut the program down at the designated time and prevent it restarting until a designated time?

---

### Post by bodhi.zazen on 2011-04-06
If it is a single program, use cron

Skeleton

# stop use of application:

chmod a-x /path/to/program
pkill program

# Start
chmod a+x /path/to/program

Such cronjobs would be much more efficient and use less cpu time.

iptables is also an elegant solution, yes it takes some time to comprehend, but read my web page and you should be able to sort it out.

---

### Post by corkscrew on 2011-04-06
> **bodhi.zazen said:**
> If it is a single program, use cron

Skeleton

# stop use of application:

chmod a-x /path/to/program
pkill program

# Start
chmod a+x /path/to/program

Such cronjobs would be much more efficient and use less cpu time.

iptables is also an elegant solution, yes it takes some time to comprehend, but read my web page and you should be able to sort it out.

Right I'll give this a go on one of my virtual boxes and see if I can get it right, will let you know.
I had a quick look at your web page ... awesome such a lot to learn though, want to though so I manage my server remotely using webmin but that's another story...

---

### Post by perspectoff on 2011-04-06
> **bodhi.zazen said:**
> If it is a single program, use cron

Skeleton

# stop use of application:

chmod a-x /path/to/program
pkill program

# Start
chmod a+x /path/to/program

Such cronjobs would be much more efficient and use less cpu time.

iptables is also an elegant solution, yes it takes some time to comprehend, but read my web page and you should be able to sort it out.

Doesn't this stop the program from running (executing) altogether?

What if I want to use the program but just prohibit it from connecting over the Internet?

For example, let's say the program connects over port 80. I wouldn't want to block port 80 by iptables, otherwise no other program that connects through port 80 would be able to communicate, either.

How do I let my program run/execute but just block it from connecting over port 80 (while still allowing every other program to connect over port 80)?

That's kind of what a proxy does, isn't it?

So perhaps the question then becomes, what is a recommended, easy-to-use proxy server for Ubuntu that any novice user can easily set up? Something like Squid, perhaps?

[https://help.ubuntu.com/10.04/serverguide/C/squid.html](https://help.ubuntu.com/10.04/serverguide/C/squid.html)

What about portreserve?

Perhaps a good layer 7 filtering application?

[https://www.dpacket.org/group-posts/open-source-software-general-discussion/open-source-software-related-deep-packet-inspect](https://www.dpacket.org/group-posts/open-source-software-general-discussion/open-source-software-related-deep-packet-inspect)

---

### Post by bodhi.zazen on 2011-04-06
> **perspectoff said:**
> Doesn't this stop the program from running (executing) altogether?

Yes, but I was responding to his post above mine where he was using pkill every minute to kill the app.

---

### Post by corkscrew on 2011-04-06
> **bodhi.zazen said:**
> Yes, but I was responding to his post above mine where he was using pkill every minute to kill the app.

Hey works a treat thanks very much just had to change ownership of the program to the user to get the task to run with the GUI Scheduler.

One more thing when you try to start the program during the "stop" time you get a little pop up window saying

```
There was an error launching the application
Details:Failed to execute child
process "totem" (permission denied)
```

I was just using movie player to experiment with, but you get the same message with any program for obvious reasons.

Anyway of either suppressing this message or editing it?

---

### Post by bodhi.zazen on 2011-04-06
Not sure about that one.

See if this helps:

[http://www.barregren.se/blog/pop-notification-command-line](http://www.barregren.se/blog/pop-notification-command-line)

---

