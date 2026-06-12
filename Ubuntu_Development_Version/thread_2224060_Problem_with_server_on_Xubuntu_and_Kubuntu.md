---
title: "Problem with server on Xubuntu and Kubuntu"
date: 2014-05-14
forum: Ubuntu Development Version
---

### Post by grahammechanical on 2014-05-14
Check out this thread

[http://ubuntuforums.org/showthread.php?t=2224000](http://ubuntuforums.org/showthread.php?t=2224000)

I have something similar on a Xubuntu Trusty upgraded to 14.04 and then to Utopic and also on a fresh install of a Kubuntu Utopic daily image of 02 May. I get "connecting to security.ubuntu.com. Could not resolve gb.archive.ubuntu.com" and it does not mater if I disable security updates (which I could do in Xubuntu but not in Kubuntu) or change the server to Main server or another server in the UK or even US. The problem remains = cannot update/upgrade.

I do not get this in Ubuntu Utopic not even when it is on the devel repositories. In Ubuntu nslookup gb.archive.ubuntu.com gives

> Non-authoritative answer:
Name:    gb.archive.ubuntu.com
Address: 91.189.88.153
Name:    gb.archive.ubuntu.com
Address: 91.189.92.200
Name:    gb.archive.ubuntu.com
Address: 91.189.92.201
Name:    gb.archive.ubuntu.com
Address: 194.169.254.10




But in these two Utopic installs of Xubuntu and Kubuntu I get "Connection timed out: No servers could be resolved." And it does not matter what mirror I have in software sources.

EDIT: Just install Lubuntu Utopic from 5th May daily image. Installed updates at the same time and with an ethernet connection to the router. And Lubuntu Utopic has the same problem. Firefox will not load its start page or any of the pre-defined bookmarks or any web page. The Network Manager icon is missing. Edit network connections says I am connected by wired. But cannot find any useful way of making a wireless connection.

And Yes, the router is connected to the ISP as proved by posting this from Ubuntu Uptopic. I have never had this problem with any install of the flavours in previous development cycles. 

Regards.

---

### Post by ventrical on 2014-05-14
Wow... 

 In the last 2 cycles we have only got small biscuits of breakage but this is like a rack of ribs ! :) lol

Regards..

---

### Post by grahammechanical on 2014-05-14
I just installed Ubuntu Utopic from daily image 5th May and the same problem. Network Manager is there and I am connected to the router by both ethernet and wireless but Firefox cannot make an Internet connection and the same "could not resolve gb.archive.ubuntu.com" error message. And yet the installation process updates from the archives. I have seen the router led flashing indicating stuff being downloaded.

---

### Post by cariboo on 2014-05-14
I see a similar problem on all my installs, during installation the distro has zero problems connecting to the mirrors, but after the installation is complete, they suffer from the dnsmasq problem. Once I do the work around to get a working network connection, everything works the way it should. There was an initial problem with some of the Canadian archives, but changing to Main seems to have solved that problem too.

---

### Post by Elfy on 2014-05-14
[https://bugs.launchpad.net/ubuntu/+source/dnsmasq/+bug/1319536](https://bugs.launchpad.net/ubuntu/+source/dnsmasq/+bug/1319536)

reported that for the time being

---

### Post by ventrical on 2014-05-14
zsynced utopic-desktop-amd64.iso (ubuntu)  and got the same thing that Graham is talking about. The dnsmasq bug.

---

### Post by ventrical on 2014-05-15
Go this in updates:

```

Get:102 http://ca.archive.ubuntu.com/ubuntu/ utopic/main dnsmasq-base i386 2.70-2 [270 kB]

```

---

### Post by Elfy on 2014-05-15
> **ventrical said:**
> Go this in updates:

```

Get:102 http://ca.archive.ubuntu.com/ubuntu/ utopic/main dnsmasq-base i386 2.70-2 [270 kB]

```

Got that here - really should uncomment the line I commented - see if it works or not.

---

### Post by Elfy on 2014-05-15
> **Elfy said:**
> Got that here - really should uncomment the line I commented - see if it works or not.

I still get 100% usage for dnsdmasq and no connection at all.

---

### Post by ventrical on 2014-05-15
> **Elfy said:**
> Got that here - really should uncomment the line I commented - see if it works or not.

Is not this thread similar to - after update - blows out network?

---

### Post by Elfy on 2014-05-15
> **ventrical said:**
> Is not this thread similar to - after update - blows out network?

seems so - you'll see me saying much the same there :p

---

### Post by grahammechanical on 2014-05-16
I was not around yesterday = shopping with the wife. So, it was today that I used recovery mode to update my Xubuntu, Kubuntu and Lubuntu installs with this dnsmasq bug. Aftward I was able to use these installs normally. So, I guess the bug is fixed. We got a new dnsmasq-base package.

---

