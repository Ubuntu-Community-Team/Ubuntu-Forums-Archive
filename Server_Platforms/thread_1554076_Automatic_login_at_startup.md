---
title: "Automatic login at startup"
date: 2010-08-16
forum: Server Platforms
---

### Post by borobudur on 2010-08-16
Hi, 
how can I set my linux server that it logs-in the main user at startup? 

I would like to be able to make a restart remotely and be able to connect to the server again afterwards. 
The problem is that the server waits for a login and than connects to the network. So at the beginning at startup there is no network, I can't connect remotely then.

Thanks!

---

### Post by spynappels on 2010-08-16
The server services should startup independently of a login. Automatic login is extremely insecure and unnecessary if the server is set up correctly. Perhaps the question you should be asking is "Why does the server's networking service not start unless a user is logged in, and how do I fix this?"

---

### Post by spynappels on 2010-08-16
Major headslap moment!

I see this is flagged as Xubuntu. Are you running a desktop distro as a server?

---

### Post by borobudur on 2010-08-16
No, it's a ubuntu server without any GUIs

---

### Post by spynappels on 2010-08-16
What version of Ubuntu server are you running?

---

### Post by borobudur on 2010-08-16
```
lsb_release -a && uname -r
```
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 8.04.2
Release:        8.04
Codename:       hardy
2.6.24-16-server

---

### Post by cdenley on 2010-08-16
> **borobudur said:**
> The problem is that the server waits for a login and than connects to the network. So at the beginning at startup there is no network, I can't connect remotely then.


Are you sure? If you have /etc/network/interfaces configured (which the server install does), then it should bring up your network interfaces without anyone logging in. If it doesn't, then you should resolve that problem, not workaround it by configuring it to log you in or anything.

---

### Post by arrrghhh on 2010-08-16
Are you connecting via wireless?

I know there's some extra leg-work you have to do to get it working with wifi properly.

A wired connection should come up without a user logging in however.

---

### Post by borobudur on 2010-08-16
Sorry guys!
The problem occurred because the keyboard wasn't connected. Then the server didn't proceed, got stuck. 
Usually, then I connected the monitor and the keyboard to the server an checked what's going on and logged in.  
So if the keyboard is connected I can restart the server remotely.
Thanks for the help!

---

### Post by arrrghhh on 2010-08-16
Cool, glad it's sorted out - as a note, there's usually a setting in the BIOS to ignore a missing keyboard.

---

### Post by borobudur on 2010-08-17
> **arrrghhh said:**
> Cool, glad it's sorted out - as a note, there's usually a setting in the BIOS to ignore a missing keyboard.
Thanks for the info!
Regards from Switzerland

---

