---
title: "iptables, port still open after DROP"
date: 2010-07-16
forum: Security
---

### Post by HAcland on 2010-07-16
Hello,

I'm new to using iptables. I wanted to open port 4888 so I 'ALLOWED' it.

All was fine. But then I wanted to DROP it so  I did. I then reboot the server and after running iptables -L it looked like my initial addition to the FORWARD chain had been successfully removed.

However the port is still open!

Can anyone please shed some light on this please?
Many thanks

---

### Post by bodhi.zazen on 2010-07-16
My guess it that your rules are off.

Rules in iptables are processed in order. So if there is a rule early in the table to accept traffic, traffic is allowed. Adding a rule later does not change that.

Beyond that you did nto provide sufficeint information.

1. How are you configuring iptables ?

2. How are you restoring your rules after rebooting ?

3. Most important, what are your rules ?

```
sudo iptables -L -v -n
```

---

### Post by HAcland on 2010-07-16
thanks for your reply.

The funny thing is that:

iptables -L -v -n

returns this:

Chain INPUT (policy ACCEPT 2041K packets, 1816M bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 2040K packets, 2157M bytes)
 pkts bytes target     prot opt in     out     source               destination

-----

which to me means that nothing is being allowed or dropped? So how come the web-server still works? And other services? I'm guessing that there must be a file somewhere which lists the default firewall policy...

---

### Post by wacky_sung on 2010-07-16
It show that your iptables rules is not saved or reloaded after server start up.

---

### Post by bodhi.zazen on 2010-07-16
> **wacky_sung said:**
> It show that your iptables rules is not saved or reloaded after server start up.

This ^^

You need to either write a script or use iptables-save and iptables-restore.

I posted some tips on this here :

[http://bodhizazen.net/Tutorials/iptables/#Saving_your_configuration](http://bodhizazen.net/Tutorials/iptables/#Saving_your_configuration)

---

### Post by wacky_sung on 2010-07-16
Much appreciated Bodhi.zazen for your link and guidance.Actually i am using the documents from [here]("https://help.ubuntu.com/community/IptablesHowTo") without uninstalling network manager and it work.The reason is using the script will disable the network manager which disable the wireless as well.Therefore i will disable the script if i wanna use wireless and manually cut and paste the iptables rules into the terminal whenever i using wireless.Probably you can give me a better recommendation / suggestion.:D

---

### Post by HAcland on 2010-07-16
Many thanks for your replies, I understand that I need to write a script but the server was a fresh build and there was no initial script. However there must have been a default iptables because Apache worked out of the box, and come to think when I installed Glassfish on port 8080 it too was automatically open.

Where my confusion lies is that I first of all checked if 4888 was open and it wasn't. So I opened it (ALLOW) and lo and behold, it opened. Then I closed it using DROP and it is still open? So what gives?

Thanks again.

---

### Post by bodhi.zazen on 2010-07-16
> **wacky_sung said:**
> Much appreciated Bodhi.zazen for your link and guidance.Actually i am using the documents from [here]("https://help.ubuntu.com/community/IptablesHowTo") without uninstalling network manager and it work.The reason is using the script will disable the network manager which disable the wireless as well.Therefore i will disable the script if i wanna use wireless and manually cut and paste the iptables rules into the terminal whenever i using wireless.Probably you can give me a better recommendation / suggestion.:D

I use iptables-save and iptables-restore.

If you use NetworkManager, save your rules with iptables-save

```
sudo iptables-save > /etc/iptables.save
```

put this in /etc/rc.local

```
sleep 10
/sbin/iptables-restore < /etc/iptables.save
```

---

### Post by bodhi.zazen on 2010-07-16
> **HAcland said:**
> Many thanks for your replies, I understand that I need to write a script but the server was a fresh build and there was no initial script. However there must have been a default iptables because Apache worked out of the box, and come to think when I installed Glassfish on port 8080 it too was automatically open.

Where my confusion lies is that I first of all checked if 4888 was open and it wasn't. So I opened it (ALLOW) and lo and behold, it opened. Then I closed it using DROP and it is still open? So what gives?

Thanks again.

Hard to know without reviewing your rules. 

By default iptables is permissive and allows all traffic.

When you reboot, your rules were lost.

So you may have set the policy to DROP, or who knows at this point.

Moving forward, learn to write a script to set up iptables or use iptables-save.

Alternately you can use ufw.

---

### Post by wacky_sung on 2010-07-16
If you are using the iptables to close the open port(Input / Output / Forward?) in which you have identified.It does not mean that the port is still not fully closed as in your system ,there is a service open out that port is still running but you close it by using iptables which is transparent to intruder.The proper way is find out that service which opened that port and shut it off if you do not need it.

Correct me if i am wrong.This is how i deal with it in Window Operating System

---

### Post by cdenley on 2010-07-16
> **HAcland said:**
> Where my confusion lies is that I first of all checked if 4888 was open and it wasn't. So I opened it (ALLOW) and lo and behold, it opened.

By default, nothing should get filtered. Did you add a rule to "close" the port? How did you "check if 4888 was open"? Are you sure there was a process listening for connections on that port?

---

### Post by HAcland on 2010-07-16
Thanks all, so would I be correct in saying that a fresh build of Ubuntu server (8.04) is inherently very unsecure? If the default is to ALLOW all connections on all ports it certainly sounds unsecure!

Wouldn't a better policy be to have a fresh build completely locked down?

Thanks again...

---

### Post by cdenley on 2010-07-16
> **HAcland said:**
> Thanks all, so would I be correct in saying that a fresh build of Ubuntu server (8.04) is inherently very unsecure? If the default is to ALLOW all connections on all ports it certainly sounds unsecure!

Wouldn't a better policy be to have a fresh build completely locked down?

Thanks again...

No. There is no point in filtering traffic which no processes are listening for. No listening processes means no open ports. Any network services listening for connections are services that you installed, therefore intended it to be accessible, so why filter it? Letting your OS reject unsolicited network traffic instead of filtering it before it can be rejected does not make you vulnerable.

---

### Post by bodhi.zazen on 2010-07-16
> **cdenley said:**
> No. There is no point in filtering traffic which no processes are listening for. No listening processes means no open ports. Any network services listening for connections are services that you installed, therefore intended it to be accessible, so why filter it? Letting your OS reject unsolicited network traffic instead of filtering it before it can be rejected does not make you vulnerable.

That and it depends on what service you are running. There is no set of firewall rules that will make everyone happy, especially server side. are you running Apache ? A web interface (webmin) ? Samba ? NFS ? Kerberos ? NTP ? DHCP ? BIND ? Is this a router ? The list goes on and on.

I use very different rules for port 22 then port 80, and those rules are a bit more then ACCEPT||DROP.

The point is, if you install a server, you need to understand the security implications and iptables is a powerful tool with many applications.

---

