---
title: "Is there any trick or setting to real-time monitor the logs via UFW like Firestarter"
date: 2010-06-08
forum: Security
---

### Post by Smjork on 2010-06-08
I tried both Firestarter and ufw/gufw
What I like best of Firestarter (even if some say it's a dead project) is the possibility to real-time monitor the events (logs)

Now.. ufw/gufw also have some logging abilities (see gufw "Edit"->"Preferences"->"Log options"->Set level "low","medium",high","full"

But no matter what I choose, all I get in the logging window are messages like "[06/08/2010 08:15:31 PM] ufw enable"

Nothing else... compared to what I get in Firestarter's events window.

My question is: is it something I misunderstood, something wrong, some setting to be made, some <you-name-it> in order to make gufw act/react the way Firestarter does ?

---

### Post by an0dos on 2010-06-08
> **Smjork said:**
> But no matter what I choose, all I get in the logging window are messages like "[06/08/2010 08:15:31 PM] ufw enable"


If you go to "system-->administration-->log file viewer" you can  view your UFW log. Although I personally just use the command ```
cat  /var/log/messages | grep UFW
``` in the terminal.

---

### Post by bodhi.zazen on 2010-06-08
> **Smjork said:**
> I tried both Firestarter and ufw/gufw
What I like best of Firestarter (even if some say it's a dead project) is the possibility to real-time monitor the events (logs)

Now.. ufw/gufw also have some logging abilities (see gufw "Edit"->"Preferences"->"Log options"->Set level "low","medium",high","full"

But no matter what I choose, all I get in the logging window are messages like "[06/08/2010 08:15:31 PM] ufw enable"

Nothing else... compared to what I get in Firestarter's events window.

My question is: is it something I misunderstood, something wrong, some setting to be made, some <you-name-it> in order to make gufw act/react the way Firestarter does ?

There are two different logs.

The UFW logs are changes made to UFW, activation, inactivation, rules changes, etc.

You are wanting to monitor the network logs, they are in /var/log/messages.

Honestly, unless you are debugging a networking issue or testing your (iptables) rule set, there is almost never a need to manually monitor the raw logs. Use something like snort or wireshark, depending on your needs.

Monitoring the raw logs, IMO, is information overload, depending on your activity you will see hundreds or thousands of packets. IMO you want snort to alert you to potentially malicious activity you should investigate further or Wireshark (or similar tools) to perform the analysis.

Do not run wireshark as root !!!

---

### Post by Smjork on 2010-06-10
Well, then in that case ... is there any way to add the /var/log/messages "firewall specific messages" to the GUFW log window ?

I mean ... just seeing when the service has been started/stopped and/or when new/old rules are being created/modified ... is kinda useless to me. Of course both "tail -f /var/log/messages | grep <whatever>" or use of Wireshark would do the trick, but this is NOT what I asked.

For a dead project, what Firestarter shows in it's logging facility (even if the info is taken from "/messages" or "/firewall" is USEFUL to a normal user.
Blocked attempts on certain ports, source IP, etc...
This is what Joe Average expects to see in a firewall logging window, along with the already known notifications.

---

### Post by cariboo on 2010-06-10
I'm about as average as they get. I am behind a router, so there isn't a need for a firewall on any system on my internal network. Watching firewall logs gets pretty old after about 6000 false alarms. It's a fact of life on the internet that there is always someone trying to get into your system. As the others have said, a default install has no ports listening on an active interface, so why not sit back and relax and enjoy using your system, instead of constantly being on the lookout for bad guys and doing system maintenance.

---

### Post by doas777 on 2010-06-10
man, I really wish some one would just provide this functionality, rather than side-stepping the issue. I've been asking for it for like 2 years now, and all i get is 'why would you want to do that?'.  well, I want to.

---

### Post by cariboo on 2010-06-10
If you want to watch firewall activity, just open a terminal and type:

```
tail -f /var/log/messages | grep UFW
```

the output you get from the above command will look like this:

```
Jun 10 15:42:46 redstone-maverick kernel: [16002.000407] [UFW BLOCK] IN=eth1 OUT= MAC=90:4c:e5:41:e4:2f:00:24:21:da:4e:f4:08:00 SRC=192.168.1.215 DST=192.168.1.100 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=8580 DF PROTO=TCP SPT=37669 DPT=22 WINDOW=5840 RES=0x00 SYN URGP=0 
Jun 10 15:44:54 redstone-maverick kernel: [16130.104370] [UFW BLOCK] IN=eth1 OUT= MAC=90:4c:e5:41:e4:2f:00:24:21:da:4e:f4:08:00 SRC=192.168.1.215 DST=192.168.1.100 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=11883 DF PROTO=TCP SPT=44085 DPT=80 WINDOW=5840 RES=0x00 SYN URGP=0 
Jun 10 15:44:54 redstone-maverick kernel: [16130.104495] [UFW BLOCK] IN=eth1 OUT= MAC=90:4c:e5:41:e4:2f:00:24:21:da:4e:f4:08:00 SRC=192.168.1.215 DST=192.168.1.100 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=45357 DF PROTO=TCP SPT=58430 DPT=443 WINDOW=5840 RES=0x00 SYN URGP=0 
Jun 10 15:44:56 redstone-maverick kernel: [16132.152398] [UFW BLOCK] IN=eth1 OUT= MAC=90:4c:e5:41:e4:2f:00:24:21:da:4e:f4:08:00 SRC=192.168.1.215 DST=192.168.1.100 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=31942 DF PROTO=TCP SPT=58431 DPT=443 WINDOW=5840 RES=0x00 SYN URGP=0 
Jun 10 15:44:56 redstone-maverick kernel: [16132.152523] [UFW BLOCK] IN=eth1 OUT= MAC=90:4c:e5:41:e4:2f:00:24:21:da:4e:f4:08:00 SRC=192.168.1.215 DST=192.168.1.100 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=43521 DF PROTO=TCP SPT=44088 DPT=80 WINDOW=5840 RES=0x00 SYN URGP=0 
```

As you can see from the output above, the firewall is blocking attempts from 192.168.1.215.

---

### Post by bodhi.zazen on 2010-06-10
Linux is modular, meaning there is a tendency to use smaller applications to perform specific tasks rather then one large monolithic application that does it all.

Linux also offers choice.

If you prefer Firestarter, then use firestarter.

I do not think ufw or gufw were designed to monitor the logs in the way you envision, so it is unlikely they will perform the tasks the way you are wanting.

My guess is that most desktop users do not monitor their firewall logs in this way, so the demand for this function from gufw is low.

You have several options :

1. File a bug report. This is probably the best way to communicate your needs back to the developers.

2. Write you own application or program to follow the logs. Depending on your experience with such things this may vary for a trivial task to insurmountable.

3. Configure your system, via ufw or iptables and rsyslog or syslog-ng to give you more informative messages. This would be easy to use and configure. You can configure your logs as well, so that messages go to /var/log/firewall or wherever you like.

Here are several links to get you started:

[http://blog.shadypixel.com/log-iptables-messages-to-a-separate-file-with-rsyslog/](http://blog.shadypixel.com/log-iptables-messages-to-a-separate-file-with-rsyslog/)

[http://www.gossamer-threads.com/lists/gentoo/security/62069](http://www.gossamer-threads.com/lists/gentoo/security/62069)

You can find more with google.

Open a terminal and use ```
tail -F /var/log/messages
```, you will see our logs in real time.

My point here is that no set of defaults will satisfy everyone but Linux does offer some flexibility if you are willing to look under the hood.

4. Use an alternate application to monitor your network traffic. You have several options here snort and wireshark are probably the #1 and #2 options in terms of popularity, although there are other tools as well (tcpdump)

[http://danielmiessler.com/study/tcpdump/](http://danielmiessler.com/study/tcpdump/)

The "problem" I would have with dumping the logs is that, as pointed out by cariboo907, I would get thousands of (trivial) events.

If you want to know what ports are open, and that your firewall is working, use nmap, zenmap is a graphical front end, or "ShieldsUP!".

If you want to monitor your traffic in more detail, wireshark or tcpdump.

If you want a NIDS system, use snort. The advantage of snort is that snort will watch the thousands of packets and alert you so suspicious traffic, the kind of thing you should probably attend to, such as mysql injections and what not.

The advantage here is you would be using a tool (tcpdump, wireshark, or snort) tailored to what you are wanting to monitor and how you want to monitor your firewall (command line, graphical, rules based/alerts).

So while I understand what you are asking for, I am almost equally certain that the average user does not want this feature, and the more experienced "security power user" wants more detail (ie snort or tcpdump) then the firewall logs.

Honestly, no offense, but watching the firewall logs in real time gets old fast. You will see a lot of denied traffic and you can get the same information with nmap.

Personally, I use snort and investigate the alerts. This is almost certainly overkill for the average desktop user, but this way I spend my sys admin time not watching the thousands of meaningless denials, but rather tracking the potentially malicious traffic and making sure I fix any potential vulnerabilities.

Personally, although firestarter may work well for a simple desktop (no offense intended), it leaves a lot to be desired if one starts using a more complex set of firewall rules such as NAT, bridges, and/or virtualization.

In addition, as long as firestarter is working for you , no problem, but if you come across an actual bug in firestarter, it will never get fixed (unless you code it yourself) as the project is no longer under active development (having the firestarter package in the ubuntu  repositories is NOT active development, it is packaging).

---

### Post by rookcifer on 2010-06-11
There is a Perl script that does what the OP is asking. 

```
sudo aptitude install psad
```

I have never really used it, but it looks like it might do what is being asked.

---

### Post by doas777 on 2010-06-11
Thank you Bodhi, that was surprisingly comprehensive.
I'm looking into rsyslogd now as i would like to aggregate internal and external FW logs, so thanks for the links. I've also been considering a snort rig. 

for the record i gave up on firestarter several years ago for exactly the same reasons you mention, but when i install gufw on hardy, I get no logs at all, despite having previously gotten many from firestarter. this of course leads me to believe that it is not working, and leaves me in a quandry whenever I'm troubleshooting a connection problem. I just miss the simply parsed messages (that you could click on to allow block or other) and the realtime nature. just seeing the listbox scroll was plenty of proof that my firewall was actually running, at a glance. it was also nice that the list was sortable. 

I am impressed with the logging improvements in Lucid (I can actually see that it is doing somthing), but it would still be nice to have a gui window, accessible from the tray, to display info about blocked connections (not packet level, but whole connections).

thanks again for the advice

---

### Post by bodhi.zazen on 2010-06-11
> **rookcifer said:**
> There is a Perl script that does what the OP is asking. 

```
sudo aptitude install psad
```I have never really used it, but it looks like it might do what is being asked.

For the record, UFW and GUFW do what the OP is asking.

The issues is what logs are you looking at ?

GUFW logs changes made to the firewall, and this is what is displayed in the graphical interface.

[img]http://bodhizazen.net/img/GUFW/UFW-7.png[/img]

"Enable gufw logging" = firewall logs = messages about start/stop firewall or rules changes = what is displayed by GUFW when you look at the logs. These logs show messages such as ufw started , ufw stopped, rule abc  added, rule xyz deleted. ie logs changes made to the firewall  configuration.

"Enable ufw logging" = network traffic = logged to /var/log/messages = tail -F /var/log/messages.

The OP wants logs of actual network denials. This is activated either from the gui interface of on the command line and is logged to /var/log/messages. This was demonstrated very nicely by cariboo907 in his most recent post:

```
tail -f /var/log/messages | grep UFW
```[http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/](http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/)

You enable ufw logging with the command

```
sudo ufw logging medium
```The options are off, on, low, medium, high, and full and the information is logged to /var/log/messages. (Note on = LOW !!!)

From the man page:

[http://manpages.ubuntu.com/manpages/lucid/en/man8/ufw.8.html](http://manpages.ubuntu.com/manpages/lucid/en/man8/ufw.8.html)

> **LOGGING**

**ufw** supports multiple logging levels. **ufw** defaults  to  a  loglevel  of
       ’low’  when  a  loglevel is not specified. Users may specify a loglevel
       with:

         ufw logging LEVEL

       LEVEL may be ’off’, ’low’, ’medium’, ’high’ and full.  Log  levels  are
       defined as:

       **off**    disables ufw managed logging

       **low**    logs  all  blocked packets not matching the default policy (with
              rate limiting), as well as packets matching logged rules

       **medium** log level low, plus all allowed packets not matching the default
              policy,  all  INVALID  packets,  and  all  new connections.  All
              logging is done with rate limiting.

       **high**   log level medium (without rate limiting), plus all packets  with
              rate limiting

       **full**   log level high without rate limiting

       Loglevels  above  medium  generate  a  lot  of  logging output, and may
       quickly fill up your disk.  Loglevel  medium  may  generate  a  lot  of
       logging output on a busy system.

       Specifying ’on’ simply enables logging at log level ’low’ if logging is
       currently not enabled.

So you need to use the appropriate logs (ufw vs gufw), log level (low/medium/high/full), and look in the appropriate location.

See also 

[http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/](http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/)
[http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/](http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/)

---

