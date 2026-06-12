---
title: "ssh connection attempts"
date: 2020-04-08
forum: Security
---

### Post by pogo7 on 2020-04-08
I have just setup my first private cloud storage server and have been running it for about a week.
But today I have logged on and noticed that there have been attempts to  connect to it for about 4 days straight(with "grep "Failed password"  /var/log/auth.log").
And the I went on to check the connected ips (with command "ss" which I  found after a internet search), but now I am a bit lost as I am pretty  new to linux and servers.
I dont know what the output of "ss" means, so I have shutdown the server  because when I checked the ips to ssh which say ESTAB I found that  these are ips from countries that shouldnt be connecting.
I would like to know whether that means that someone got into my server  through ssh or if i should delete everything and start fresh. Advice on  how to protect against this kinds of attacks would be greatly  appreciated aswell.

Thanks in advance.

this is the output from ss:
```

tcp      ESTAB         0         0                           192.168.0.34:ssh                 112.85.42.232:59819
tcp      ESTAB         0         68                          192.168.0.34:ssh               116.196.101.168:52198
tcp      LAST-ACK      0         151                         192.168.0.34:webmin               192.168.0.22:51048
tcp      ESTAB         0         0                           192.168.0.34:ssh                 112.85.42.232:49362
tcp      ESTAB         0         0                           192.168.0.34:webmin               80.82.77.240:64344
tcp      FIN-WAIT-1    0         1                           192.168.0.34:ssh                 112.85.42.232:59191
tcp      FIN-WAIT-1    0         1                           192.168.0.34:ssh                 112.85.42.232:38961
tcp      FIN-WAIT-1    0         1                           192.168.0.34:ssh                 112.85.42.232:32746
tcp      ESTAB         0         68                          192.168.0.34:ssh                31.184.254.198:50394
tcp      FIN-WAIT-1    0         1                           192.168.0.34:ssh                 112.85.42.232:18654
tcp      ESTAB         0         0                           192.168.0.34:ssh                222.186.15.114:10575
tcp      FIN-WAIT-1    0         1                           192.168.0.34:ssh                 112.85.42.232:60052
tcp      ESTAB         0         0                           192.168.0.34:ssh                 112.85.42.232:61394
tcp      ESTAB         0         0                           192.168.0.34:webmin              104.152.52.24:51649
tcp      ESTAB         0         0                           192.168.0.34:ssh                 112.85.42.232:49426
tcp      ESTAB         0         68                          192.168.0.34:ssh                46.101.103.207:34116
tcp      ESTAB         0         0                           192.168.0.34:webmin             157.230.90.160:43287
tcp      ESTAB         0         0                           192.168.0.34:ssh                 112.85.42.232:29238
tcp      FIN-WAIT-1    0         1                           192.168.0.34:ssh                 112.85.42.232:56932
tcp      ESTAB         0         68                          192.168.0.34:ssh                  114.67.79.46:33334
tcp      ESTAB         0         0                           192.168.0.34:ssh                 112.85.42.232:49804

```
snipet from auth.log:
```

Apr  8 20:43:06 nik-server sshd[1572]: Failed password for invalid user user from 106.12.2.81 port 56568 ssh2
Apr  8 20:43:08 nik-server sshd[1574]: Failed password for invalid user ts3bot from 61.74.180.44 port 41070 ssh2
Apr  8 20:43:13 nik-server sshd[1701]: Failed password for invalid user postgres from 157.230.2.208 port 54194 ssh2
Apr  8 20:43:17 nik-server sshd[1714]: Failed password for invalid user ubuntu from 106.13.140.52 port 55260 ssh2
Apr  8 20:43:26 nik-server sshd[1811]: Failed password for invalid user admin from 59.36.19.130 port 46904 ssh2
Apr  8 20:43:58 nik-server sshd[2303]: Failed password for invalid user test from 218.22.36.135 port 9984 ssh2
Apr  8 20:44:21 nik-server sshd[2679]: Failed password for invalid user sai from 142.93.239.197 port 41316 ssh2
Apr  8 20:44:51 nik-server sshd[3045]: Failed password for invalid user nas from 187.11.140.235 port 39754 ssh2
Apr  8 20:44:53 nik-server sshd[3087]: Failed password for invalid user root from 222.186.42.136 port 39624 ssh2
Apr  8 20:44:56 nik-server sshd[3177]: Failed password for invalid user ubuntu from 223.240.70.4 port 37838 ssh2
Apr  8 20:44:57 nik-server sshd[3087]: Failed password for invalid user root from 222.186.42.136 port 39624 ssh2
Apr  8 20:45:00 nik-server sshd[3087]: Failed password for invalid user root from 222.186.42.136 port 39624 ssh2
Apr  8 20:45:08 nik-server sshd[3314]: Failed password for invalid user oracle from 61.74.180.44 port 15713 ssh2
Apr  8 20:45:28 nik-server sshd[3754]: Failed password for invalid user kamal from 175.139.192.37 port 44290 ssh2
Apr  8 20:45:30 nik-server sshd[3756]: Failed password for invalid user roger from 61.175.121.76 port 57607 ssh2
Apr  8 20:46:09 nik-server sshd[4236]: Failed password for invalid user postgres from 218.22.36.135 port 9986 ssh2
Apr  8 20:46:20 nik-server sshd[4415]: Failed password for invalid user webmaster from 134.122.79.129 port 57482 ssh2
Apr  8 20:46:53 nik-server sshd[4779]: Failed password for invalid user andrew from 62.234.193.119 port 42650 ssh2
Apr  8 20:47:00 nik-server sshd[4833]: Failed password for invalid user ts3bot from 106.13.140.52 port 58646 ssh2
Apr  8 20:47:16 nik-server sshd[5042]: Failed password for invalid user coin from 116.196.101.168 port 41896 ssh2
Apr  8 20:47:16 nik-server sshd[5047]: Failed password for invalid user test2 from 220.178.75.153 port 42260 ssh2
Apr  8 20:47:26 nik-server sshd[5177]: Failed password for invalid user ts3bot from 163.239.206.113 port 42734 ssh2
Apr  8 20:47:34 nik-server sshd[5272]: Failed password for invalid user sshvpn from 89.154.4.249 port 44878 ssh2
Apr  8 20:47:38 nik-server sshd[5318]: Failed password for invalid user postgres from 187.11.140.235 port 34530 ssh2
Apr  8 20:47:43 nik-server sshd[5373]: Failed password for invalid user toro from 142.93.239.197 port 50828 ssh2
Apr  8 20:47:50 nik-server sshd[5420]: Failed password for invalid user admin from 82.148.30.250 port 36964 ssh2
Apr  8 20:47:54 nik-server sshd[5515]: Failed password for invalid user user from 45.33.81.143 port 43678 ssh2
Apr  8 20:47:59 nik-server sshd[5565]: Failed password for invalid user test from 175.139.192.37 port 51446 ssh2
Apr  8 20:48:27 nik-server sshd[5907]: Failed password for invalid user test from 223.240.70.4 port 37922 ssh2
Apr  8 20:48:58 nik-server sshd[6232]: Failed password for invalid user deploy from 190.64.213.155 port 37884 ssh2
Apr  8 20:49:54 nik-server sshd[6890]: Failed password for invalid user root from 222.186.30.76 port 48056 ssh2
Apr  8 20:49:59 nik-server sshd[6890]: message repeated 2 times: [ Failed password for invalid user root from 222.186.30.76 port 48056 ssh2]
Apr  8 20:50:11 nik-server sshd[7107]: Failed password for invalid user deploy from 31.184.254.198 port 49888 ssh2
Apr  8 20:50:11 nik-server sshd[7143]: Failed password for invalid user jboss from 51.77.137.211 port 42114 ssh2
Apr  8 20:50:21 nik-server sshd[7248]: Failed password for invalid user mahesh from 62.234.193.119 port 44440 ssh2
Apr  8 20:50:24 nik-server sshd[7296]: Failed password for invalid user postgres from 183.134.199.68 port 46185 ssh2
Apr  8 20:50:49 nik-server sshd[7661]: Failed password for invalid user ems from 163.239.206.113 port 34022 ssh2
Apr  8 20:51:08 nik-server sshd[7905]: Failed password for invalid user root from 157.230.2.208 port 49348 ssh2
Apr  8 20:51:25 nik-server sshd[8192]: Failed password for invalid user admin from 27.78.14.83 port 55816 ssh2
Apr  8 20:51:25 nik-server sshd[8194]: Failed password for invalid user squid from 116.105.216.179 port 51338 ssh2
Apr  8 20:51:26 nik-server sshd[8203]: Failed password for invalid user test from 27.78.14.83 port 51796 ssh2
Apr  8 20:51:27 nik-server sshd[8202]: Failed password for invalid user operator from 116.105.216.179 port 51868 ssh2
Apr  8 20:51:31 nik-server sshd[8266]: Failed password for invalid user git from 220.178.75.153 port 6363 ssh2
Apr  8 20:51:32 nik-server sshd[8308]: Failed password for invalid user postgres from 194.182.175.108 port 35972 ssh2
Apr  8 20:51:38 nik-server sshd[8359]: Failed password for invalid user deploy from 118.27.31.188 port 50070 ssh2
Apr  8 20:51:43 nik-server sshd[8410]: Failed password for invalid user lab from 128.199.169.102 port 49751 ssh2
Apr  8 20:51:56 nik-server sshd[8596]: Failed password for invalid user firebird from 162.243.10.64 port 37806 ssh2
Apr  8 20:52:07 nik-server sshd[8715]: Failed password for invalid user t7inst from 89.154.4.249 port 51860 ssh2
Apr  8 20:52:28 nik-server sshd[8942]: Failed password for invalid user root from 222.186.15.62 port 25058 ssh2
Apr  8 20:52:35 nik-server sshd[8942]: message repeated 2 times: [ Failed password for invalid user root from 222.186.15.62 port 25058 ssh2]
Apr  8 20:52:46 nik-server sshd[9140]: Failed password for invalid user test from 182.61.40.158 port 37208 ssh2
Apr  8 20:53:13 nik-server sshd[9468]: Failed password for invalid user gaurav from 183.134.199.68 port 36854 ssh2
Apr  8 20:53:28 nik-server sshd[9705]: Failed password for invalid user ftptest from 190.64.213.155 port 47420 ssh2
Apr  8 20:53:31 nik-server sshd[9789]: Failed password for invalid user test from 115.217.18.100 port 41643 ssh2

```

---

### Post by TheFu on 2020-04-08
That's the cost of having a system on the internet.  Here's an article about securing ssh and blocking connections.
[https://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures](https://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures)

i hope you have offsite, versioned, backups working.  Once the system is hacked, which is very common for systems run by noobs, there isn't much that can be done except to wipe the machine completely and start over, being smarter the next time.  Once a system is hacked, it can never be trusted again.

---

### Post by EuclideanCoffee on 2020-04-08
**ss** is used to dump socket statistics. It allows showing information similar to *netstat*. It can display more TCP and state informations than other tools.

Let me filter your list to make sense of it.

```

cat list.txt | grep ESTAB

tcp      ESTAB         0         0                           192.168.0.34:ssh                 112.85.42.232:59819
tcp      ESTAB         0         68                          192.168.0.34:ssh               116.196.101.168:52198
tcp      ESTAB         0         0                           192.168.0.34:ssh                 112.85.42.232:49362
tcp      ESTAB         0         0                           192.168.0.34:webmin               80.82.77.240:64344
tcp      ESTAB         0         68                          192.168.0.34:ssh                31.184.254.198:50394
tcp      ESTAB         0         0                           192.168.0.34:ssh                222.186.15.114:10575
tcp      ESTAB         0         0                           192.168.0.34:ssh                 112.85.42.232:61394
tcp      ESTAB         0         0                           192.168.0.34:webmin              104.152.52.24:51649
tcp      ESTAB         0         0                           192.168.0.34:ssh                 112.85.42.232:49426
tcp      ESTAB         0         68                          192.168.0.34:ssh                46.101.103.207:34116
tcp      ESTAB         0         0                           192.168.0.34:webmin             157.230.90.160:43287
tcp      ESTAB         0         0                           192.168.0.34:ssh                 112.85.42.232:29238
tcp      ESTAB         0         68                          192.168.0.34:ssh                  114.67.79.46:33334
```

These are all connections actively on your device.

It appears there are a lot of IP addresses, which may mean you have people connected to your device that you might want want to have on there. Let's coordinate this with your auth log to see if we can find any active connection.

Good news is that literally every entry you provided in the auth log appears as if IPs were blocked (not all IPs in ss output, but some here).

```

Apr  8 20:50:11 nik-server sshd[7107]: Failed password for invalid user deploy from 31.184.254.198 port 49888 ssh2

```

Does this mean you're good? Unlikely.

To get started, you will want to harden your server the minute it's online. Here's a guide: [https://www.digitalocean.com/community/questions/best-practices-for-hardening-new-sever-in-2017](https://www.digitalocean.com/community/questions/best-practices-for-hardening-new-sever-in-2017)

This is a considerable amount of work, which is why a lot of people don't own a server anymore or hire someone to do it for them. :)

If you don't mind being compromised, you can put as much or as little effort as possible.

I deeply care about being compromised because it's my job not to be compromised in certain spheres. So I've gone great lengths to "layer" my operational security. Look up "layered security" and "operational security" to get some ideas what efforts people go through to secure a network and hardware.

This is a big step into security, I understand. But if you intend to do this professionally, it's important.

If it's not all too important to maintain this server professionally, then a minimal amount of effort by following the guide I posted above should help you.

---

### Post by pogo7 on 2020-04-08
Thanks for the quick and helpful replies, I have physical access to the server so ill disconect it from the internet and then do a fresh install & secure it.
Hopefully ill be able to learn enough about layered security to implement it as well.

---

### Post by EuclideanCoffee on 2020-04-08
I'm glad you took it down and decided to try it again. Best of luck. Feel free to post here if you run into trouble or are not sure what to do.

---

### Post by TheFu on 2020-04-08
When you do that, please disable webmin from any external connections.  if you must have it, please only allow localhost connections.  it is a common target for crackers as are ssh servers that allow passwords for authentication.

---

### Post by pogo7 on 2020-04-08
thanks for the advice i'll make sure to only have it accessible locally.

---

### Post by TheFu on 2020-04-08
> **pogo7 said:**
> thanks for the advice i'll make sure to only have it accessible locally.

Locally means from 127.0.0.x/8, not only on the LAN.

---

### Post by EuclideanCoffee on 2020-04-08
For ipv6 you will see something like [:].

---

### Post by pogo7 on 2020-04-08
Oh, in that case I won't install it. I dont "need" it it was just an easy way of configuring everything from my laptop. Just out of curiosity though if I were to set it to localhost would I then have to connect to the server and open the webpage there ? (asking because im using ubuntu server without the desktop environment)

---

### Post by TheFu on 2020-04-08
you'd use an ssh-tunnel to connect, then use your normal workstation and browser on it to tunnel through that ssh connection.

Same for VNC or any other non-secure network connections.

Really, it is best not to use webmin.  Same for any admin interfaces for anything - wordpress, nextcloud, myphpadmin, cpanel, whatever without forcing only localhost access.  All programs have bugs. Those bugs can be abused if access is possible.

---

### Post by EuclideanCoffee on 2020-04-08
Generally it is fine to use administration portals if you keep them updated. This is generally a lot of work, so people often tout that it's better not to have them at all. You can do whatever you want. Just be mindful as you've been. Good luck.

---

### Post by kevdog on 2020-04-11
I'm just curious about what the OP posted -- where in what he has posted has suggested his system has been compromised?

---

### Post by TheFu on 2020-04-11
> Advice on how to protect against this kinds of attacks would be greatly appreciated aswell.
Was the request.  Don't think anyone said the machine was currently hacked. Did you see that?

---

### Post by The Cog on 2020-04-11
> **kevdog said:**
> I'm just curious about what the OP posted -- where in what he has posted has suggested his system has been compromised?

There were lots of incoming SSH connections from lots of different IP addresses - unlikely for a server that's just been set up. (state ESTAB, local address is 192.168.0.34:ssh, lots of remote addresses). I did a whereis on the first remote listed, and it's in China. I didn't bother to whereis the rest.

---

### Post by kevdog on 2020-04-12
@The Cog

I saw that as well, however there isn't actually any evidence the box was compromised.  If you follow the thread, the OP stated he was going to try again with a "fresh installation" which implies to me that he was going to reinstall, which isn't going to do anything to actually solve his problem -- unless system was compromised -- but there isn't any evidence of this.

He'd probably be better off doing a few things
1. Setting up fail2ban
2. Limiting access to ssh to specific IP addresses (if this is possible).
3. Security through obscurity techniques (I'm not sure this is recommended but things he could try)
    a. Changing ssh port
    b. PortKnocker (if really wanting to go extreme).

Other than that I think a lot of the advice and pointed links in the thread were relevant.  I just wanted to be sure I wasn't seeing something you guys were seeing.  The comment "I'm glad you took it down and decided to try it again" -- why?? -- this comment doesn't make a lot of sense to me.  Just disable the webmin interface.

---

### Post by EuclideanCoffee on 2020-04-12
All of these steps are covered in my initial post's link in full detail.

I also did an analysis where I showed how the user can see if their box was compromised. I determined it likely wasn't, but then I provided that information in a tutorial link to improve security.

Note, please see that this thread has already been solved.

---

