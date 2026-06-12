---
title: "Multiple Ip Addresses Trying To Connect To My Machine"
date: 2010-12-19
forum: Security
---

### Post by dodo3773 on 2010-12-19
Last night I decided to fire up etherape and there are about 100 - 200 ip addresses trying to connect to my machine. I do not know what to do. Have I been compromised? Is there a way to stop them? I closed my web browser, email client, basically any internet program and the problem still persists. I ran a rootkit check and came up with this
```

    /usr/bin/dpkg                                            [ Warning ]
    /usr/bin/dpkg-query                                      [ Warning ]

    /usr/bin/ldd                                             [ Warning ]
   
    /usr/bin/lynx                                            [ Warning ]

    /usr/bin/lynx.cur                                        [ Warning ]

    /usr/sbin/inetd                                          [ Warning ]

    /usr/sbin/rsyslogd                                       [ Warning ]

Checking for enabled inetd services                      [ Warning ]
Checking /dev for suspicious file types                  [ Warning ]
    Checking for hidden files and directories                [ Warning ]
```I am not sure if it is a rootkit or just standard bot type activity against my ip. Any help would be greatly appreciated.

Here are some of the ip addresses
```

109.205.252.203
114.37.135.202
118.243.234.87
121.166.140.150
224.0.0.251

```There are many more. Thanks in advance.

---

### Post by cariboo on 2010-12-19
Were you running a bittorrent client at the time?

---

### Post by dodo3773 on 2010-12-19
> **cariboo907 said:**
> Were you running a bittorrent client at the time?

No, that is with all internet applications closed. Not really sure what's going on.

---

### Post by bodhi.zazen on 2010-12-19
Do you have any listening services ?

```
sudo lsof -i -n -P
```

---

### Post by dodo3773 on 2010-12-19
> **bodhi.zazen said:**
> Do you have any listening services ?

```
sudo lsof -i -n -P
```
 
Here is the result from    sudo lsof -i -n -P

```
COMMAND    PID        USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
avahi-dae  957       avahi   13u  IPv4   4407      0t0  UDP *:5353 
avahi-dae  957       avahi   14u  IPv4   4408      0t0  UDP *:48791 
exim4     1484 Debian-exim    3u  IPv4   5088      0t0  TCP 127.0.0.1:25 (LISTEN)
exim4     1484 Debian-exim    4u  IPv6   5089      0t0  TCP [::1]:25 (LISTEN)
inetd     1502        root    4u  IPv4   5110      0t0  TCP *:21 (LISTEN)
cupsd     1586        root    6u  IPv6   5571      0t0  TCP [::1]:631 (LISTEN)
cupsd     1586        root    7u  IPv4   5572      0t0  TCP 127.0.0.1:631 (LISTEN)
dhclient  1871        root    5u  IPv4   7452      0t0  UDP *:68 
clock-app 2041    dodo3773   22u  IPv4  54348      0t0  TCP 192.168.1.5:56829->24.143.207.97:80 (ESTABLISHED)
evolution 2577    dodo3773   50u  IPv4  16408      0t0  TCP 192.168.1.5:59819->74.125.155.109:993 (ESTABLISHED)
evolution 2577    dodo3773   59u  IPv4  16445      0t0  TCP 192.168.1.5:59820->74.125.155.109:993 (ESTABLISHED)
firefox-4 2578    dodo3773   45u  IPv4  55865      0t0  TCP 192.168.1.5:38690->66.102.7.101:80 (ESTABLISHED)

```I have Firefox and Evolution Open right now.

---

### Post by CharlesA on 2010-12-19
Port 21 is usually an ftp server of some sort.

Did you install something like that?

---

### Post by dodo3773 on 2010-12-19
> **CharlesA said:**
> Port 21 is usually an ftp server of some sort.

Did you install something like that?

I searched for ftp in installed applications and I only found 2 packages that seem relevant one is called
"ftp" 
and the other is called 
"proftpd-basic"

Do you think it could be related to one of these? Should I uninstall them and see if the problem is still there?

---

### Post by CharlesA on 2010-12-19
proftpd-basic is an ftp server. Do you remember installing it?

---

### Post by dodo3773 on 2010-12-19
> **CharlesA said:**
> proftpd-basic is an ftp server. Do you remember installing it?

I don't. But I do tinker with my system a lot. So there is a good chance that I did. Probably while installing something else that might have needed it.
I will remove it and reboot and check back in.

---

### Post by bodhi.zazen on 2010-12-19
I do not see anything of concern in that output.

inetd is listening on port 21 , part of exim I am guessing

[https://wiki.ubuntu.com/InetdUsage](https://wiki.ubuntu.com/InetdUsage)

[http://www.gnu.org/software/inetutils/](http://www.gnu.org/software/inetutils/)

What incoming connections are you worried about ? Where do you see them ? Logs ?

---

### Post by dodo3773 on 2010-12-19
> **CharlesA said:**
> proftpd-basic is an ftp server. Do you remember installing it?

I removed it and now instead of 100 there is only 8 (well 10 if you include me and the router). Thank you for your help man. 8 connections is normal right? I remember on a clean install there was a few that I believe Ubuntu was using itself.

---

### Post by dodo3773 on 2010-12-19
> **bodhi.zazen said:**
> I do not see anything of concern in that output.

inetd is listening on port 21 , part of exim I am guessing

[https://wiki.ubuntu.com/InetdUsage](https://wiki.ubuntu.com/InetdUsage)

[http://www.gnu.org/software/inetutils/](http://www.gnu.org/software/inetutils/)

What incoming connections are you worried about ? Where do you see them ? Logs ?
I saw them in a program called etherape. I removed the ftpd-basic package and that seemed to solve it. I have about 8 ip addresses connecting now. I think that that is normal though as far as I know. I am pretty sure they are all Ubuntu related. Does that sound about right to you? I leaved the program installed that pings the Ubuntu server for statistics. I am alright with them knowing that I still use Ubuntu. It is the least I can do. So that should be one right there. How many connections on boot do you think a default install would make? Do you have any idea? I still use Lucid by the way (I wish Maverick worked right on my machine but even with the patched kernel it was still a snail trail ramble ramble ramble).

---

### Post by CharlesA on 2010-12-19
> **dodo3773 said:**
> I removed it and now instead of 100 there is only 8 (well 10 if you include me and the router). Thank you for your help man. 8 connections is normal right? I remember on a clean install there was a few that I believe Ubuntu was using itself.

That's better.

> **bodhi.zazen said:**
> 
inetd is listening on port 21 , part of exim I am guessing

I don't think that exim depends on it, as I am running exim on my box and I didn't have to install an ftp server. :)

---

### Post by dodo3773 on 2010-12-19
> **CharlesA said:**
> That's better.



I don't think that exim depends on it, as I am running exim on my box and I didn't have to install an ftp server. :)

Right on. Marking thread as solved. Thanks again you guys. Hardly do I come to these forums with a real problem that does not find solution.

---

