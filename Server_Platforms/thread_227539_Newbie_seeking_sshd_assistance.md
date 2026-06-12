---
title: "Newbie seeking sshd assistance"
date: 2006-08-01
forum: Server Platforms
---

### Post by ckraft on 2006-08-01
I just installed Ubuntu 6.06 server addition and everything is working ok, but I am having trouble with sshd.

I installed and configured sshd. I can ssh to my box locally but when I go to any other machine on my network I cannot ssh to my Ubuntu box.

I clearly am missing an additional step but I cannot figure out what I am doing wrong.

Any advice on how to get this working? 

Thanks

Chris

---

### Post by coach-x on 2006-08-01
Locally, do you mean ssh localhost or 127.0.0.1?  Check ListenAddress in /etc/ssh/sshd_config and make sure it is not set as 127.0.0.1.  The default configuration should give full network access to the ssh server.

Also make sure sshd is running, ps -wef | grep sshd

---

### Post by ckraft on 2006-08-01
I mean I can ssh to the machine from the console. I set the IP address to 192.168.168.168 on my Ubuntu box.

I type "ssh 192.168.168.168" on the Ubuntu box and I can connect fine.

I jump to another machine and do ssh 192.168.168.168 and it just hangs for a while and then says "Connection closed by 192.168.168.168"

I can ping the Ubuntu box from other boxes I just can't seem to make a ssh connection.

I did check with ps and sshd is up and running.

---

### Post by scxtt on 2006-08-01
which package, specifically, did you "installed and configured"?

---

### Post by ckraft on 2006-08-01
As root I did apt-get install openssh-server

---

### Post by coach-x on 2006-08-01
> **ckraft said:**
> I mean I can ssh to the machine from the console. I set the IP address to 192.168.168.168 on my Ubuntu box.

I type "ssh 192.168.168.168" on the Ubuntu box and I can connect fine.

I jump to another machine and do ssh 192.168.168.168 and it just hangs for a while and then says "Connection closed by 192.168.168.168"

I can ping the Ubuntu box from other boxes I just can't seem to make a ssh connection.

I did check with ps and sshd is up and running.

Strange, can you telnet 192.168.168.168 22, will let know if the openssh server is answering.  Could be firewall issue?  Do you have any rules set up in iptables, either machine.

---

### Post by scxtt on 2006-08-01
i doubt **telnet 192.168.168.168 22** will work - doesn't for me (and i have no ssh problems) ...

i do agree w/ the firewall question ... we'll have to wait and see if ckraft has firestarter (or equiv.) installed and opened up ports ...

---

### Post by scxtt on 2006-08-01
...

---

### Post by ckraft on 2006-08-02
> **coach-x said:**
> Strange, can you telnet 192.168.168.168 22, will let know if the openssh server is answering.  Could be firewall issue?  Do you have any rules set up in iptables, either machine.

When I telnet to port 22 from another machine I get this:

SSH-2.0-OpenSSH_4.2p1 Debian-7ubuntu3

I do not have any firewall software installed. After doing the base server install the first thing I tried to setup is sshd.

Thanks for the assistance I appreciate the help in trying to get this resolved.

---

### Post by scxtt on 2006-08-02
AFAIK, ubuntu locks down all ports until you tell it not to (w/ a tool like firestarter) -- i'd recommend installing firestarter and then allowing the IPs from the other boxes on your network ...

---

### Post by ckraft on 2006-08-02
I don't have a GUI installed so doing firestarter is difficult. I guess I could install Xubuntu or something.

If I type iptables -L I do not see any rules in place so I am not sure if it is the firewall.

I installed apache2 just to see if I could get any inbound traffic working and I can connect to apache, running on my Ubuntu box, fine from any other machine on my network.

Another odd thing is that it doesn't just fail. It times out while authenticating. I was trying different changes in the sshd_config file and when I change the port to a different number then the ssh attempts from other machines say connection refused.

Even when I ssh from the Ubuntu machine to itself it pauses for about 25-30 seconds before it actually connects.

I am assuming that whatever it is doing during that pause is what is causing the problem.

My Ubuntu box is a new machine with a new motherboard from Gigabyte with an ali chipset so maybe it is a hardware issue, even though I can connect via ssh.

My next thoughts are to:

- Install telnetd and ftpd and see if that works, I wouldn't use  them, I just want to see if it works.

- Run sshd manually in a debug mode to get a better view of what it is trying to do.

- Install my Intel EEPRO card into the machine and see if that works better than the integrated ethernet port.

---

### Post by jimcooncat on 2006-08-02
> **ckraft said:**
> When I telnet to port 22 from another machine I get this:

SSH-2.0-OpenSSH_4.2p1 Debian-7ubuntu3

I do not have any firewall software installed. After doing the base server install the first thing I tried to setup is sshd.

Thanks for the assistance I appreciate the help in trying to get this resolved.

I don't think there's a firewall issue at all -- you're seeing the sshd server through telnet.

Otherwise, you'd be getting:
[INDENT]telnet: Unable to connect to remote host: Connection refused[/INDENT]

---

### Post by az on 2006-08-02
> **scxtt said:**
> AFAIK, ubuntu locks down all ports until you tell it not to (w/ a tool like firestarter) -- ...

No.  That just means nothing is installed that is listening by default.  SSH should be listening if the daemon is installed.

If all you did was to install the server version, reboot and install ssh, it should work.  Did the installation proceed without errors?

---

### Post by scxtt on 2006-08-02
you should be able to install firestarter (gui or not) and then edit **/etc/firestarter/inbound/allow-from** using the form:
```
:> cat /etc/firestarter/inbound/allow-from
x.x.x.x, work
x.x.x.x, home
```then restart firestarter **sudo /etc/init.d/firestarter restart** ...

---

### Post by Glut on 2006-08-03
Don't install a firewall, there's no point - it wont help anything and will only hinder you.
Let's start from the top. We know that ssh is installed.
> If I type iptables -L I do not see any rules in place so I am not sure if it is the firewall.
Great, we know that you do not have a firewall installed. I suggest not installing one if the only service you have installed is ssh, there's no advantage to be gained.
> 
When I telnet to port 22 from another machine I get this:

SSH-2.0-OpenSSH_4.2p1 Debian-7ubuntu3

OK, this is saying that you can connect to the box and ssh is responding.
I assume that you're not trying to log in as root, as that will fail by default.
We will want to see the relevant logs. Could you:
```
[COLOR="SeaGreen"]tail -n0 -f /var/log/auth.log[/COLOR]
```This will display the log as items are added. Attempt to log into the machine via ssh, then copy the log and post it here.

*Edit* Also, you may want to post /etc/pam.d/ssh as that controls the authentication process.

---

### Post by scxtt on 2006-08-03
...

---

