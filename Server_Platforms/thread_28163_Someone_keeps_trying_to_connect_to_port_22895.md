---
title: "Someone keeps trying to connect to port 22895"
date: 2005-04-19
forum: Server Platforms
---

### Post by Trickyphillips on 2005-04-19
[IMG]http://img248.echo.cx/img248/8055/screenshotfirestarterubuntu15a.png[/IMG]

It seems like someone is trying to connect to port 22895, through a bunch of proxies. Does anyone know what 22895 might be, and if I should be worried about this? Firestarter keeps notifying me about this, and it's getting annoying.

---

### Post by Vache on 2005-04-19
I know of nothing that runs on 22895. A quick google check brought up nothing as well. The IP addresses you see attempting to connect to you might not actually be people - it might be zombie PCs scanning for other zombies. Probably nothing to worry about. You might want to resolve those IPs and see if you can get in touch with a human that owns the box.

---

### Post by Trickyphillips on 2005-04-19
[QUOTE=Vache]I know of nothing that runs on 22895. A quick google check brought up nothing as well. The IP addresses you see attempting to connect to you might not actually be people - it might be zombie PCs scanning for other zombies. Probably nothing to worry about. You might want to resolve those IPs and see if you can get in touch with a human that owns the box.[/QUOTE]
 Sorry.. Just my paranoia, I guess. I just installed the firewall recently, and got curious at the sight of so much prodding. I think that particular port isn't being checked for anymore. I'm getting lots of different requests on random ports, so as long as I leave my firewall up I don't think I have much to worry about.

Interestingly, someone tried scanning my system for a remote admin tool (Radmin) as I was viewing my activity. I scanned him back, and he had ports open all over the place. I got into his FTP, and uploaded a .txt saying "Hey... I saw you scanning my ports for Radmin. Nice try".

This firewall is fun. :D

Thanks, Vache!

---

### Post by CrustyDOD on 2005-04-19
heh i'm getting scanned by same/similar ip's on same/similar ports :)

i'm just ignoring them..

---

### Post by Vache on 2005-04-19
[QUOTE=Trickyphillips]Sorry.. Just my paranoia, I guess. I just installed the firewall recently, and got curious at the sight of so much prodding. I think that particular port isn't being checked for anymore. I'm getting lots of different requests on random ports, so as long as I leave my firewall up I don't think I have much to worry about.

Interestingly, someone tried scanning my system for a remote admin tool (Radmin) as I was viewing my activity. I scanned him back, and he had ports open all over the place. I got into his FTP, and uploaded a .txt saying "Hey... I saw you scanning my ports for Radmin. Nice try".

This firewall is fun. :D

Thanks, Vache![/QUOTE]

No problem. Any computer connected to the internet is going to get bombarded with port scans. Usually, they are of little to no threat, unless you're running services (Apache, telnet, ftp, etc.) that is available to the outside. Ubuntu does not seem to run anything like that by default, thankfully!

---

### Post by Trickyphillips on 2005-04-19
[QUOTE=Vache](Apache, telnet, ftp, etc.)[/QUOTE]

Yes, yes, yes, yes. I'm running all of those. Would it be almost impossible for someone to get my root password, and own me via telnet?

---

### Post by Vache on 2005-04-19
I really recommend that you turn off all those services - Why do you have telnet running? Very, very bad idea. Firewall or not, someone with a touch of skill or too much free time can get past that single line of defense.

Turn off everything you don't need running all the time, and set up the firewall to deny outside traffic to any of the service's applicable ports! :)

---

### Post by Trickyphillips on 2005-04-20
[QUOTE=Vache]I really recommend that you turn off all those services - Why do you have telnet running? Very, very bad idea. Firewall or not, someone with a touch of skill or too much free time can get past that single line of defense.

Turn off everything you don't need running all the time, and set up the firewall to deny outside traffic to any of the service's applicable ports! :)[/QUOTE]

I take a couple computer-related classes at the local community college, and like to be able to play around with my computer while I'm in the computer lab.

---

### Post by negatory on 2005-04-20
Telnet is a very bad idea!It's a clear text protocol and not very reliable...try ssh instead if you really need it.
I run sshd at all times and keep a close eye at the /var/log/auth.log .Only got one intrusion attempt...wich I promptly denied the service to that IP. 

Pedro Carrico

---

### Post by xy77 on 2005-05-27
[QUOTE=Trickyphillips]Sorry.. Just my paranoia, I guess. I just installed the firewall recently, and got curious at the sight of so much prodding. I think that particular port isn't being checked for anymore. I'm getting lots of different requests on random ports, so as long as I leave my firewall up I don't think I have much to worry about.
[/QUOTE]

I observed a similar behaviour. I'm setting up a webserver that will be available from outside. For installing and testing it's in the local net though. Whenever I try to connect to the webserver, I get a connection to a random port in ascending order, leaving a few out (e.g. 1586, 1590). The connection from the different PC is refused. Firestarter tells me the source is the local pc, Strange, I think. Why should a local connection be triggered on connection to the webserver?

Any ideas would be great, thank you.

- David (xy77)

EDIT: after allowing connects to 1-32000 from <localIP> I can connect to the webserver, but that's not how it should be, is it?

---

### Post by LordHunter317 on 2005-05-27
Running telnet in this day and age is a good way to get owned.  

Portscans are just a fact of life.  Port assaults are a fact of life.  So are SSH dictionary attacks on your box.  Ignore them and move on.  They don't really matter.

---

### Post by fng on 2005-05-27
After reading this thread, is just glanced at my /var/log/auth.log
It seems there a re a lot of people using SSH dictionary attacks.

I count 7 in the past 3 days :(

Is tracing those IP's and sending emails at their hosts and/or ISP's gonna help?

---

### Post by GrumpySimon on 2005-06-03
[QUOTE=fng]After reading this thread, is just glanced at my /var/log/auth.log
It seems there a re a lot of people using SSH dictionary attacks.

I count 7 in the past 3 days :(

Is tracing those IP's and sending emails at their hosts and/or ISP's gonna help?[/QUOTE]
 Probably not. These ssh brute force attacks are very common - If memory serves, this is actually a hallmark of an old & rather widespread linux rootkit called SucKit, and the BruteSSH exploit script dates back at least to 2004.

Anyway - [There's a good discussion](http://andreas.id.au/blog/archives/9_SSH+scans+and+invalid+logins+for+test+and+guest+accounts.html) on this on Andreas Koepke's blog, which includes a dump of the source code of the exploit. Make sure you don't have any of the accounts / password combinations listed there (mainly things like test:test, guest:guest, etc).

Another thing to try is to move the port SSH listens to. If SSH isn't listening on the default port 22, then a brute force attack on 22 ain't going anywhere. Off the top of my head, changing the default port should be as easy as changing the "Port xx" line in /etc/ssh/ssh_config, and restarting sshd (/etc/init.d/ssh stop <wait> /etc/init.d/ssh start).

--Simon

---

### Post by ArmedGeek on 2005-06-11
> Off the top of my head, changing the default port should be as easy as changing the "Port xx" line in /etc/ssh/ssh_config, and restarting sshd (/etc/init.d/ssh stop <wait> /etc/init.d/ssh start).

--Simon


Actually, /etc/ssh/sshd_config.  ssh_config is for the client.  I've got my sshd running on a non-standard port for this very reason.  It's not really dangerous (as long as you password is not 'password') but it IS irritating.

Simply, change the Port xx to another number (NOT 80, 21, 25, etc) and restart the service.  On the client machines (either in ~/.ssh/ssh_config or /etc/ssh/ssh_config) add a section 

Host hostname/ipaddr
    Port xx

where hostname/ipaddr is the hostname or ipaddress of the server and xx is the port number that you changed the server to.  This will keep you from having to specify the port on the commandline everytime you ssh to the server.

--ArmedGeek

---

