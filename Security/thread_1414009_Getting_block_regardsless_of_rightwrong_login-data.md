---
title: "Getting block regardsless of right/wrong login-data (SSH)"
date: 2010-02-23
forum: Security
---

### Post by nuffe on 2010-02-23
My servern keeps blocking me and it's permanent ban :(

Started out with a fresh installation of ubuntu server then did the following:

* Installed (L)AMP
* Changed sshd_config to disable RootLogins
* Installed OSSEC
* Tried to install OSSEC WUI -> Failed
* Removed OSSEC WUI
* Reinstalled Postfix
* Reloaded server
* Open a session with PuTTY
* Enter wrong password 2 times
* Enter correct password
* See that I have 4 zombie-processes
* Getting a prompt for 1 second
* Now I'm banned

At this stage the server keeps blocking we. I open PuTTY as normal, open a session, enter username and password correctly but it takes about 1 second and then I'm banned and have to change IP. Since I'm using dynamic IP's I can retry infinite times, although it's in a limited IP-range (same subnet).

So, I have about 1-2 seconds to execute a command. What I've done so far is look at /etc/hosts.deny and there is just a few IP's there where I've logged in from but not all of them, I have one IP that is banned but it's not in hosts.deny-file. So I guess it's blocked by iptables. (I did this with the "Execute Remote Command" in PuTTY and saved to log)

At this time I've got no zombie-processes.

What I need help with is to execute root-commands, ex. a script that execute a "sudo reboot" or flushes/stops iptables and them simulates keystrokes (enters the root-password). If this isn't possible I would like a solution.

I've got no physical access to the server, just remote. Any other services like HTTP is working fine but stops working when I log into SSH.

Please help!

EDIT:
2 Zombie processes are back.... It also seems like I'm only banned for a limited time but some IP's are still banned since 48 hours...

---

### Post by pebo on 2010-02-23
Have you edited /etc/hosts.allow? Mine looks like this: ```
sshd: ALL: ALLOW
```and /etc/hosts.deny:```
ALL: ALL: DENY
```

---

### Post by nuffe on 2010-02-23
> **pebo said:**
> Have you edited /etc/hosts.allow? Mine looks like this: ```
sshd: ALL: ALLOW
```and /etc/hosts.deny:```
ALL: ALL: DENY
```

My hosts.allow is empty (except the default comments) and hosts.deny contains the same + one IP.

I came across something like this:

sudo reboot < /home/user/<file with root-password>

But it didn't work, could it be modified to work?

All SSH-communication worked perfectly until I reloaded the server.

EDIT:
The IP that is blocked for 48 hours and counting can not reach the server BUT a nmap-scan with -P0 set revealed open ports (80,25,22,21) which I think is odd...

I really need a way to execute commands as root. Any way is welcome, dirty or not, need access! SCP worked as a charm when I copied a file.

---

### Post by bodhi.zazen on 2010-02-23
Sounds like ossec if blocking your access.

Ossec looks for new connections / failed log in attempts and typically blocks an IP Address for 15 minutes.

Since you are using multiple IP , my guess it is blocking your subnet.

ossec will also watch for changes to config files as well, so running some applications as root will likely result in a block as well.

Dy you have physical access to the server ? If so, stop ossec and re-configure.

---

