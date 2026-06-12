---
title: "Scared to restart server"
date: 2011-08-05
forum: Server Platforms
---

### Post by kyral210 on 2011-08-05
I have a Ubuntu Server 10.10 running as a backup host, so it just sits there in the server room recieiving bits of data once a day. I access and control it via remote desktop as I have installed the Gnome GUI to make working with it a little easier.
 
If I restart the server (through remote desktop), when it restarts will I be able to access it via remote desktop, or will I have to go into the server room and log in to the server before I can remote connect to it?
 
There is no rush really, but I want to know if I can install updates hassel free...

---

### Post by HermanAB on 2011-08-05
Howdy,

There are some good reasons why sysadmins do not use VNC remote desktop, but rather use SSH and Webmin.

You should at least install sshd and make sure it will start at boot so that you have a second option if VNC won't work.

---

### Post by kyral210 on 2011-08-05
The server is installed as Open SSH, but that is all I know. How would I view & control the server via SSH from my Windows 7 laptop?

---

### Post by karlson on 2011-08-05
> **kyral210 said:**
> I have a Ubuntu Server 10.10 running as a backup host, so it just sits there in the server room recieiving bits of data once a day. I access and control it via remote desktop as I have installed the Gnome GUI to make working with it a little easier.


It's a performance impact but it's your call.

> 
If I restart the server (through remote desktop), when it restarts will I be able to access it via remote desktop, or will I have to go into the server room and log in to the server before I can remote connect to it?


It depends on how the set up is done for the remote desktop.  If it's set up via inetd then it will be available once all the services start up.  However, that won't help you if HW has a problem, so I would use something like ILO on HP servers or something similar.  This will allow remote access even through a reboot.

---

### Post by karlson on 2011-08-05
> **kyral210 said:**
> The server is installed as Open SSH, but that is all I know. How would I view & control the server via SSH from my Windows 7 laptop?

Install SecureCRT or Putty so you can log in to the server via SSH.

---

### Post by ian dobson on 2011-08-05
> **kyral210 said:**
> The server is installed as Open SSH, but that is all I know. How would I view & control the server via SSH from my Windows 7 laptop?

Hi,

Install putty on your windows7 box. I use it on my windows box (64bit) to access 10 different linux boxes.

Regards
Ian Dobson

---

### Post by HermanAB on 2011-08-06
If you install Cygwin on your Windows machine, then you can do anything, including forwarding X for remote GUI programs.

---

### Post by kyral210 on 2011-08-06
Ok I have Putty on my Windows 7 Laptop, tried to log in and it said invallid port number. This is a REALLY basic question but:
1) Do I need to do anything with my server or firewall
2) How do I log into that server with Putty?
 
Sorry I am so new to all of this.

---

### Post by SeijiSensei on 2011-08-06
First make sure that SSH is listening on the server.  Connect to the server as you do now, then run "sudo apt-get install openssh-server".  Either it will be installed or you'll be told you already have the most recent version.  If the latter, try running "sudo restart ssh" to make sure it's up.

Now try again connecting with putty.  You shouldn't need to do anything other than enter the server's IP address or hostname and leave the port set at 22, the SSH default.  You'll be told you don't have a host entry for the machine and asked if you want to trust it.  The *default* in putty is to *refuse* to trust the remote *and* to *disconnect*.  Make sure you choose the option to accept the remote's identity and make the connection.

If putty still can't connect, you may have firewalling issues.

---

### Post by kyral210 on 2011-08-08
I still have to test this from my home network (loging in over the internet), but it works fine within the office network.

I DiDn't realise that Putty gave you the terminal commant rather than GUI. I honestly Dont know how to run everything from the terminal screen, neverminD. 

Thanks for the help.

---

