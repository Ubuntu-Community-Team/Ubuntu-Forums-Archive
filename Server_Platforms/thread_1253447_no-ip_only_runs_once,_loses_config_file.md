---
title: "no-ip only runs once, loses config file"
date: 2009-08-30
forum: Server Platforms
---

### Post by CarltonF on 2009-08-30
Hi all,

I have my web server running and since it does not have a static IP, I am using no-ip duc in order to keep it available. The trouble I am having is that it seems to create a config file in one place then look for it in another, which obviously leads to a claim that it is missing.

Here's an example:
```
sudo apt-get install noip2

Auto configuration for Linux client of no-ip.com.

2 hosts are registered to this account.
Host xxxxxxxx.no-ip.org selected.

New configuration file '/var/lib/noip2/noip2.conf' created.

Starting dynamic address update: noip2.

me@myserv:~$ noip2
Can't locate configuration file /usr/local/etc/no-ip2.conf. (Try -c). Ending!
```

It found the config file from my previous attempt, realised there are 2 hosts (which is correct - only 1 should be updated here though) and then when I run it again it looks in a completely different place and then does not work. I tried running no-ip2 -C -c /usr/local/etc/no-ip2.conf and then setting it up again, verified the config file was there by looking manually and yet when I ran it again it still complained that it was unable to find it.

I don't know what the problem is, but it is rather annoying because it updates once (on the first run) and then never again, so when the ip changes I have to travel to where it is, check the ip, log in to no-ip.org and update it manually. As you can probably guess, this becomes rather tedious.

Can anyone help me solve this problem?

---

### Post by doogy2004 on 2009-08-30
try this
```
sudo noip2 -C
```

---

### Post by CarltonF on 2009-08-31
Thank you for the reply, however I am still unable to get this to work. Here is the output I receive from my SSH session:

```
me@myserv:~$ sudo noip2 -C
[sudo] password for me:

Auto configuration for Linux client of no-ip.com.

Please enter the login/email string for no-ip.com  xxxx@xxxx.com
Please enter the password for user 'xxxx@xxxx.com'  ****************

2 hosts are registered to this account.
Do you wish to have them all updated?[N] (y/N)  n
Do you wish to have host [xxxx.no-ip.org] updated?[N] (y/N)  y
Do you wish to have host [xxxxx.no-ip.org] updated?[N] (y/N)  n
Please enter an update interval:[30]  30
Do you wish to run something at successful update?[N] (y/N)  n

New configuration file '/usr/local/etc/no-ip2.conf' created.

me@myserv:~$ noip2
Can't locate configuration file /usr/local/etc/no-ip2.conf. (Try -c). Ending!
```

---

### Post by doogy2004 on 2009-08-31
noip2 runs as a daemon/service when the computer starts up, therefore it must be run as root using sudo.

This command creates the configuration file and saves it in the proper place, then it starts the noip2 daemon.
```
sudo noip2 -C
```

if you like you could run the following to verify that noip2 is running.
```
sudo noip2
```

---

### Post by JT9161 on 2009-08-31
[quote=CarltonF;7877600]
 
Change

```
noip2
```

to

```
sudo noip2
```

---

### Post by CarltonF on 2009-09-01
Ah thank you both for your replies. I did this and now it says that it is running already. No more travelling to the server to manually check the IP. Thanks for all of the help.

---

