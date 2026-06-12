---
title: "port 22: Connection refused"
date: 2012-03-15
forum: Server Platforms
---

### Post by Fertech on 2012-03-15
I was using the ssh from my mac to my server and I rebooted the server
and now I can't use ssh.  I get this error


ssh: connect to host 192.168.0.103 port 22: Connection refused

~$ sudo service ssh start
start: Job is already running: ssh


I also scan all ports and this and snap a screenshot.
as you can see in the screenshot im blocking the rest of the port, 
just need ssh and http open.

---

### Post by miklcct on 2012-03-16
Do you have your configuration files set up correctly?

---

### Post by Jonathan L on 2012-03-16
> I rebooted the server and now I can't use ssh. [...]Hello Fertech

To me looks like there's no problem with port blocking or similar, but it does look like ssh isn't running, or isn't running properly.  From the description, my guess is that it's not set to start correctly by your reboot, and previously you'd started it manually in a different way -- would that have been possible?

On the server, check to see if the process is running:
```
$ ps ax | fgrep ssh
1726 ?        Ss     0:00 /usr/sbin/sshd -D

```If it is, on the server, see if you can ssh to itself:
```
$ ssh localhost
user@localhost's password: [...]
```If you can get in, then your problem is with networking, port filtering or similar.  If you can't get in locally, then your problem is with ssh, which is what I'm guessing is happening.  Try looking in your log files for any start up errors, in particular problems allocating the port.

Look for this kind of thing in /var/log/auth.log
```
Dec 21 15:35:27 master sshd[1101]: Server listening on 0.0.0.0 port 22.
```
Hope that's of some help isolating your problem.

Kind regards,
Jonathan.

---

