---
title: "Firewall and open ports"
date: 2008-10-29
forum: Security
---

### Post by PhilOHara on 2008-10-29
I have recently installed Ubuntu 8.04 first time Linux user and want to know what to do in regards to setting up a firewall I read that there is a built in firewall called iptables and that needs to be configured! How? Or is there a program that I can install like in the windows world. I ran sheilds up which indicates ports 21 23 and 80 are open, I also readthat ubuntu by default boots with all ports closed?
Confused? I am!! Can someone please clarifywhat I need to do?.....Phil

---

### Post by EnGorDiaz on 2008-10-29
> **PhilOHara said:**
> I have recently installed Ubuntu 8.04 first time Linux user and want to know what to do in regards to setting up a firewall I read that there is a built in firewall called iptables and that needs to be configured! How? Or is there a program that I can install like in the windows world. I ran sheilds up which indicates ports 21 23 and 80 are open, I also readthat ubuntu by default boots with all ports closed?
Confused? I am!! Can someone please clarifywhat I need to do?.....Phil

having ports 21 and 23 open is a real security risk

---

### Post by kreggz on 2008-10-29
I suspect you have installed apache, telnet server and a FTP server?

Ubuntu should not have any ports open unless you install server apps as listed above.

if you want a simple firewall you can use firestarter (gui) or ufw (cli)
these programs manipulate iptables for you.

---

### Post by EnGorDiaz on 2008-10-29
> **PhilOHara said:**
> I have recently installed Ubuntu 8.04 first time Linux user and want to know what to do in regards to setting up a firewall I read that there is a built in firewall called iptables and that needs to be configured! How? Or is there a program that I can install like in the windows world. I ran sheilds up which indicates ports 21 23 and 80 are open, I also readthat ubuntu by default boots with all ports closed?
Confused? I am!! Can someone please clarifywhat I need to do?.....Phil

now lets see there firestarter

ubuntu comes with iptables as default

see how to close traffic and ports there
[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

---

### Post by PhilOHara on 2008-10-29
> **EnGorDiaz said:**
> having ports 21 and 23 open is a real security risk
So how did they open and how do I close them?

---

### Post by EnGorDiaz on 2008-10-29
can you also post the output of

```
netstat -ta
```


and also you have to see why these ports are open maybe a program of some sort so run this command

netstat -tap

---

### Post by PhilOHara on 2008-10-29
> **EnGorDiaz said:**
> now lets see there firestarter

ubuntu comes with iptables as default

see how to close traffic and ports there
[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)
I am unaware that I installed these programs - apache, telnet server and a FTP server?
I am running dual boot system, could they be open from Win XP in the other partition?
I have run firestarter and rerun sheildup which still states these ports open?

---

### Post by PhilOHara on 2008-10-29
> **EnGorDiaz said:**
> can you also post the output of

```
netstat -ta
```


and also you have to see why these ports are open maybe a program of some sort so run this command

netstat -tap
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 localhost:ipp           *:*                     LISTEN

---

### Post by PhilOHara on 2008-10-29
> **PhilOHara said:**
> Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 localhost:ipp           *:*                     LISTEN
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 localhost:ipp           *:*                     LISTEN

---

### Post by EnGorDiaz on 2008-10-29
> **PhilOHara said:**
> I am unaware that I installed these programs - apache, telnet server and a FTP server?
I am running dual boot system, could they be open from Win XP in the other partition?
I have run firestarter and rerun sheildup which still states these ports open?

to answer your questions apache telnet and ftp come as default what we are saying is they might be causing it to be open bcus you might be using a particular application which uses those protocols which i think you are not

its impossible for another os on your hard drive to interfere with the other

---

### Post by EnGorDiaz on 2008-10-29
> **PhilOHara said:**
> Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 localhost:ipp           *:*                     LISTEN

wait somethings wrong there hmmm just gotto figure out what ive never had this problem before maybe youll have to edit your iptables config or do some grep commands

---

### Post by EnGorDiaz on 2008-10-29
ive got it!


you might have to run the sudo command dont if its successful

```
(sudo -i)iptables -A INPUT -d (your ip address here) -p tcp --dport 21 -j REJECT
```

and do so for each port replacing 21 with the ports which are open

---

### Post by brian_p on 2008-10-29
> **PhilOHara said:**
> 

Confused? I am!! Can someone please clarifywhat I need to do?.....Phil

Let's give it a go.

Do you have your internet connection through a router?

Run ShieldsUp from Ubuntu. Make a note of open ports. They show as red.

Now reboot the machine and run ShieldsUp from Windows. Note the open ports.

Report back here with the results.

---

### Post by brian_p on 2008-10-29
> **EnGorDiaz said:**
> to answer your questions apache telnet and ftp come as default . . . . 

Not with the desktop edition they don't.

---

### Post by brian_p on 2008-10-29
> **EnGorDiaz said:**
> wait somethings wrong there . . . . 

Not necessarily. If PhilOHara is reporting correctly his machine is listening only to itself for connections to the printing service.

>  . . . .  hmmm just gotto figure out what ive never had this problem before maybe youll have to edit your iptables config or do some grep commands

If (and it's a big 'if') PhilOHara has installed ftp, telnet and web services (inadvertently or otherwise) he has no need to resort to the intricacies of iptables rules. It would be sufficient to uninstall the services.

---

### Post by kreggz on 2008-10-29
another point is that when you do a shields up scan it is scanning your router, not your pc - unless of course the ports are forwarded to your pc...

---

### Post by hyper_ch on 2008-10-30
I think in most cases you don't need to worry about the firewall in ubuntu.

---

### Post by booksbuggy on 2008-11-02
Well personally i am a security freak myself so i run both guard dog and fire starter at the same time and manually enable the ports i use daily.

I go into the internet and look for the ports of which are dangerous while intrusion and block them.

---

### Post by bodhi.zazen on 2008-11-02
> **booksbuggy said:**
> Well personally i am a security freak myself so i run both guard dog and fire starter at the same time and manually enable the ports i use daily.

I go into the internet and look for the ports of which are dangerous while intrusion and block them.

:lolflag: I am sorry but I actually laughed out loud when I read that. I am curious how it is you feel more secure in acting this way ?

Please do not take me the wrong way, I am not trying to mock you, but I would like to at least make you aware of a few things. I should probably not tell you this, but firestarter and guard dog are not firewalls. They are configuration tools and if you run them both I would assume either they confuse one another or the second one you start cancels the first.

Your firewall is IP tables.

Firestarter is outdated to say the least. It has not been maintained in several years, certainly not ideal for the paranoid. Now I know some paranoid people, and paranoid people run self-compiled, up to date applications and none of the paranoid would dream of running an application that has not been maintained.

If you open the ports daily, how is that more secure then leaving them open all the time and turning your computer off when you are done with it ?

If you are running a server, please look into securing it. Server security is more then the gui apps you mentioned.

Also see the security and intrusion detection sickies at the top of these forums. They have been reviewed by people who know more about security then I do.

---

### Post by EnGorDiaz on 2008-11-23
> **booksbuggy said:**
> Well personally i am a security freak myself so i run both guard dog and fire starter at the same time and manually enable the ports i use daily.

I go into the internet and look for the ports of which are dangerous while intrusion and block them.

well if you think thats securing you then LOL set up an IPcop box

---

### Post by gTinker on 2008-11-24
I know this is a thread in the section for security discussions but wouldn't it be more helpful for the op, PhilOHara if we got back to his problem?

As has been correctly mentioned, it sounds like it's your router configuration that you should check. Presumably it has been configured to allow those open ports. Do you find anything about that on the router configuration page for the router's firewall? Is it possible that something on the Windows install when it's booted up could be communication on those ports, even a rootkit or backdoor?

The good advice to check these things, which have already been suggested, is something you should consider PhilOHara. Telnet, 23 and ftp, 21 are not ports you would want to have open if you weren't using them and telnet is inherently insecure and has been for years. It doesn't appear, from the way you answered, that Ubuntu is listening on those ports. I have lately, though, been getting attempts on my firewall at 23, so there might be some malware using it.

---

### Post by kevdog on 2008-11-24
Just a clarification of terms

By default Ubuntu has all incomping ports open -- but there are no processes that are listening -- so no security risk

If you install for example a ftp or ssh server, suddenly you do however have a process listening on an open port.  The purpose of the firewall is to restrict access to this listening port -- run the request through a filter.

Its possible for the firewall to restrict access to all ports, even ports that have listening processes.

---

### Post by koenn on 2008-11-24
Well, it's a 3 week old thread, but anyway:

My take is that the OP is behind a NAT router, and that shields-up therefore scanned his router. The open ports are (probably) actually on the router, say 80/tcp  for a management web interface, 23/tcp for command line management, and 21/tcp for FT uploads of, hm ..., firmware updates or config files uploads.

To fix the problem, first establish whether its the router or the PC's behind it that need fixing

---

### Post by stmurray on 2008-11-25
> **kevdog said:**
> Just a clarification of terms

By default Ubuntu has all incomping ports open -- but there are no processes that are listening -- so no security risk



Everyone always says this, and it is true for TCP.  However, on all my Ubuntu installations there are two processes listening on UDP ports-- avahi and dhclient3.  Things like Shields Up only scan TCP ports as UDP scanning can be problematic.  If there were ever a vulnerability found in avahi or dhclient3, then (unless I am mistaken) all Ubuntu machines without a firewall would be vulnerable, until they get patched.  I believe this risk is low, but I still feel that people should know that there are IP ports open, so they can make their own decisions on whether to install a firewall.  (Stepping down from the soapbox now....)

---

