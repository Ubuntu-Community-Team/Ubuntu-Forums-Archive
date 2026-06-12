---
title: "Display IP after boot, before login."
date: 2010-11-26
forum: Server Platforms
---

### Post by erlendoos on 2010-11-26
Hi all,

I use ubuntu server as a virtualbox instance, bridged networking enabled.
It would be helpfull if the server would display the IP with which I can connect to it after boot. In that way I don't have to login as root and run ifconfig.

How can this be done?

---

### Post by James78 on 2010-11-26
I believe you can get the desired effect by going into /etc/update-motd.d/ and adding a shell script to output your IP.

.. Are you trying to list the IP address of a virtual machine instance on the main host, or just on the guest on login? Listing it in the main host will probably be pretty difficult (I believe it's still possible though, especially for VBox), and as for listing it in the virtual machine, well.. Ubuntu Server already shows the interface IP on a default install. Could you explain a little more what exactly you're trying to achieve?

---

### Post by farandwee on 2011-02-02
Hello,

I guess erlendoos point was to show the IP in the virtual machine.

I have this same desire and edited the 00-header in /etc/update-motd.d/ but the info inside it is showing after loggin. 

What I (maybe we) want is to have the IP in the login screen, after boot. My screen is:

```
Ubuntu 10.04.2 LTS servername tty1

servername login: _
```What I want would be something like:

```
Ubuntu 10.04.2 LTS servername tty1

[COLOR=Red]inet addr:192.168.2.1  Bcast:192.168.2.255  Mask:255.255.255.0[/COLOR]

servername login: _
```I'm using the command ifconfig to get that line with IP details, and it works, but only after the login.

Is there a way to show it before the login, as in the second code block?

Thanks,
Faran

---

### Post by lsiu on 2011-10-19
I found the solution to the problem on displaying the IP address before the login prompt.

The following post has the answer: [http://offbytwo.com/2008/05/09/show-ip-address-of-vm-as-console-pre-login-message.html](http://offbytwo.com/2008/05/09/show-ip-address-of-vm-as-console-pre-login-message.html)

---

