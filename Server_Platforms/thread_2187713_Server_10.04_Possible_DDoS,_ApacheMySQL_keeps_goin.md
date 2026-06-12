---
title: "Server 10.04 Possible DDoS, Apache/MySQL keeps going down. How to fix?"
date: 2013-11-13
forum: Server Platforms
---

### Post by RavenLX on 2013-11-13
I'm not sure what is happening here. I have a 10.04 LTS LAMP server running and have a cron going to check Apache and MySQL at intervals and if either should go down, restart the unresponsive server. If after so many restarts of the affected server, if it still is unresponsive, the whole server reboots automatically. This has actually worked out pretty well for a long time as it seems self-healing. It's rare that the server would need to reboot (I'm emailed notices when it reboots just before it reboots).

Well, every so often some bot would come along (like one I had come in from an out-of-the-country IP recently) and try to log into the server via ssh and try to log in as root. That won't work because "root" as a user has been deactivated (only special scripts I made to help run the server will run as root/sudo). There is no "root" user that can be logged into. Further, I have ssh set up to only accept logins from an authorized administrator who obviously isn't named "root". That's the FIRST thing I always do when creating a server. Anyway, they do still try to log in as root. And they do it repeatedly over the course of minutes (and getting denied entry, of course).

Now, is there a way to prevent this and is this why Apache and MySQL could go unresponsive? Too many attempts of someone trying to log into the server hitting the server too much? They aren't coming in via Apache or MySQL, just ssh (remote like PuTTY or some other program).

Can someone tell me if I'm looking in the right place and if there is a way I can stop repeated attempts (even if they can't possibly get in anyway)? Also, is there a way to stop it cold before they even make an attempt? I don't know how they got our IP (you need the IP in order to log in via ssh) in the first place so is there a way to get the IP masked for ssh but still work for DNS for Apache running on the server so scanning bots can't even find and try it?

---

### Post by Habitual on 2013-11-13
fail2ban, in a repo near you.

---

### Post by sandyd on 2013-11-13
> **RavenLX said:**
> I'm not sure what is happening here. I have a 10.04 LTS LAMP server running and have a cron going to check Apache and MySQL at intervals and if either should go down, restart the unresponsive server. If after so many restarts of the affected server, if it still is unresponsive, the whole server reboots automatically. This has actually worked out pretty well for a long time as it seems self-healing. It's rare that the server would need to reboot (I'm emailed notices when it reboots just before it reboots).

Well, every so often some bot would come along (like one I had come in from an out-of-the-country IP recently) and try to log into the server via ssh and try to log in as root. That won't work because "root" as a user has been deactivated (only special scripts I made to help run the server will run as root/sudo). There is no "root" user that can be logged into. Further, I have ssh set up to only accept logins from an authorized administrator who obviously isn't named "root". That's the FIRST thing I always do when creating a server. Anyway, they do still try to log in as root. And they do it repeatedly over the course of minutes (and getting denied entry, of course).

Now, is there a way to prevent this and is this why Apache and MySQL could go unresponsive? Too many attempts of someone trying to log into the server hitting the server too much? They aren't coming in via Apache or MySQL, just ssh (remote like PuTTY or some other program).

Can someone tell me if I'm looking in the right place and if there is a way I can stop repeated attempts (even if they can't possibly get in anyway)? Also, is there a way to stop it cold before they even make an attempt? I don't know how they got our IP (you need the IP in order to log in via ssh) in the first place so is there a way to get the IP masked for ssh but still work for DNS for Apache running on the server so scanning bots can't even find and try it?
csf/lfd is a good option as well

---

### Post by RavenLX on 2013-11-13
Thank you both. I'll look into all options mentioned. I appreciate your help.

---

### Post by Habitual on 2013-11-13
could also change the ssh port?

---

### Post by RavenLX on 2013-11-13
@Habitual - That's a very good idea. 

On a slightly related question: Do you (or anyone reading) know how I could test the ports to see if they are stealth? I know the site grc.com has a tester but the server doesn't have a browser installed on it that can be used with the site (that I know of). I probably would avoid installing lynx or something anyway on a server (this is not the desktop Ubuntu but the Server version of Ubuntu).

---

### Post by RavenLX on 2013-11-13
I've used nmap to scan the IP of the server and found in it:

Discovered open port 22/tcp on [IP Edited for Privacy]

and:

PORT     STATE    SERVICE
21/tcp   open     ftp
22/tcp   open     ssh
80/tcp   open     http

So if I changed the ssh port #, wouldn't someone still be able to get the port # anyway like this? I was able to do that from a remote machine (my laptop) and the server is at a data center not anywhere near home. So, if I could do it easily it's plausable anyone can.

Is there a way to stealth this but keep functionality enough for admins to log in and administer the server when needed?

---

### Post by sandyd on 2013-11-13
> **RavenLX said:**
> I've used nmap to scan the IP of the server and found in it:

Discovered open port 22/tcp on [IP Edited for Privacy]

and:

PORT     STATE    SERVICE
21/tcp   open     ftp
22/tcp   open     ssh
80/tcp   open     http

So if I changed the ssh port #, wouldn't someone still be able to get the port # anyway like this? I was able to do that from a remote machine (my laptop) and the server is at a data center not anywhere near home. So, if I could do it easily it's plausable anyone can.

Is there a way to stealth this but keep functionality enough for admins to log in and administer the server when needed?
changing the port is security through obscurity and is only a bit more tad secure than having a default ssh port because of port scanners

If you want to have something thats secure, just either
a) setup and restrict to ssh keys
b) setup a openvpn server and disable ssh from outside access

Also - might be worth menthioning that the mentioned csf/lfd does detect port scans, and a bit of tuning will allow csf to auto-block port scanners :p

---

### Post by Habitual on 2013-11-13
> **RavenLX said:**
> I've used nmap to scan the IP of the server and found in it:

Discovered open port 22/tcp on [IP Edited for Privacy]

and:

PORT     STATE    SERVICE
21/tcp   open     ftp
22/tcp   open     ssh
80/tcp   open     http

So if I changed the ssh port #, wouldn't someone still be able to get the port # anyway like this?
They'd have to **know** the ssh port, not guess and nmap wouldn't show "open ssh" as it's not the standard ssh port.
It would show "22/tcp open unknown" and that's about it for that port.

Bots (scripts) are stupid and believe ssh is only on 22, so changing the ports breaks them of that "habit" and they'd move on.
Smarter scripts could come by 'later' and try ssh <ip>:<port> on something higher, but generally speaking, it's a solid Security Practice.


Also as sandyd has suggested, ssh keys are a good idea.

---

### Post by RavenLX on 2013-11-14
Thank you all very much for your information. You've given me a good deal to think about. I'm going to try and implement as many of these suggestions as possible for best security. I'm going to do some experimenting on some of my other servers to see how it all works and use nmap to see what changes or doesn't when I make some changes. This is turning out to be a great learning experience for me.

---

### Post by Habitual on 2013-11-14
</edited>

---

### Post by Habitual on 2013-11-14
I mis-spoke.
I meant to say ""2222/tcp open unknown"
and that is to indicate you moved ssh port to 2222.

Don't forget....**backup /etc/ssh/sshd_config** first, then edit.
and restart (this may be different on Ubuntu these days).
service openssh-server restart

Open a terminal > ssh session to the host and STAY CONNECTED.
make edits to  /etc/ssh/sshd_config
restart openssh-server...
netstat -plaunt | grep <newport>
and from another terminal
ssh user@server -p <newport>

Once ssh user@server -p <newport> works you're ok to disconnect from the first terminal.
DO NOT LEAVE THE SERVER until you're 100% certain that the <newport> is open and accepting ssh connections.
Have fun!

---

### Post by Habitual on 2013-11-14
</edited>

---

