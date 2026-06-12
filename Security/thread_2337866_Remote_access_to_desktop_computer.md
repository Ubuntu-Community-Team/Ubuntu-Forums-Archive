---
title: "Remote access to desktop computer"
date: 2016-09-22
forum: Security
---

### Post by Elmi77 on 2016-09-22
Hi,

I have installed some friends an Ubuntu 15 system for their desktop computer. These are normal home-computers which are behind a WLAN-Router with integrated firewall. Their IP is dynamic, means it changes at least once a day.

Now I want to have remote-access to these computers to be able to change things for them without visiting them personally. This should be a solution which
[LIST]
[*]does not require any actions on their side to let me in
[*]is able to deal with their dynamic IP and to come through their routers firewall without opening security holes
[*]is secure so that nobody can access these computers, eavesdrop a connection to them and so on
[/LIST]

Any suggestions how and using which software this can be done? An own dedicated server would be available when this helps.

---

### Post by howefield on 2016-09-22
If you want security start with what you are installing on to the computers, both 15.xx versions of Ubuntu are now end of life and should not be used. The current 16.04.1 version is supported for 5 years and is better used.

---

### Post by HermanAB on 2016-09-22
Well, you can set up a script to email you the IP address every day and run sshd on port 443 for secure remote access.  Because port 443 is normally the https port, internet service providers do not block it.

---

### Post by ian-weisser on 2016-09-22
ddns + router port forwarding + sshd.

The ddns provider (many free providers are available) overcomes the dynamic IP.
You often need to insert a simple heartbeat script (with security token) that tells the ddns provider "Hey, I'm at this IP now." Some ddns providers include (occasionally rather bloated) 'client' software if you don't want to put together the simple script.

You must set your router to forward inbound sshd packets to the target system. This is usually two easy steps - assign the target system a consistent IP address based on it's MAC, and the forward sshd packets on your chosen sshd port to that IP address.

Finally, set up sshd on the target system. Configure for the desired port (a different port is a convenience, not a security measure). ALWAYS disable root login and password login. ALWAYS setup and use keys for sshd access; no exceptions.

Example of your command to access the remote machine:
```
ssh account_name@my_ddns_name -p port_num
ssh elmi77@friends_machine.ddns.com -p 12345
```

---

### Post by SeijiSensei on 2016-09-22
I much prefer using OpenVPN for this sort of thing.  It goes through firewalls since it is using SSL for its connections.  You just need to use a simple, shared-key arrangement as described [here](http://openvpn.net/static.html).  Set up the remote as an OpenVPN client using the "remote" directive to identify the server at your end.  When the machine boots, it will start trying to connect to your server.  It will then set up a full-time tunnel that you can use to communicate with the remote host.  I've used this trick to manage remote servers that I have installed in clients' offices.

Most of the time you'll probably be using an SSH client to connect over the tunnel, but you can also configure X so you can run graphical applications on the remote machine and have them display their output across the tunnel to your computer.

---

### Post by HermanAB on 2016-09-25
There are so many ways to do it.  You could set up a cron job that will create a reverse SSH connection from their machine to yours every day at a predetermined time. [https://www.howtoforge.com/reverse-ssh-tunneling](https://www.howtoforge.com/reverse-ssh-tunneling)

Just be sure to kill the existing tunnel, before creating a new one.

---

