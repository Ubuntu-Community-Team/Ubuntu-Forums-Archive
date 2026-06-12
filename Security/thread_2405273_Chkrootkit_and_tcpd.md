---
title: "Chkrootkit and tcpd"
date: 2018-11-03
forum: Security
---

### Post by peacefull on 2018-11-03
After a security breach and hack into Bionic desktop, secure erase the SSD with hdparm and re-installed minimal Bionic, UFW rules and others. 

Running chkrootkit, I get tcpd INFECTED. 
```
sudo chkrootkit
```

```
Checking `syslogd'...                             not tested
Checking `tar'...                                           not infected
Checking `tcpd'...                                            INFECTED
Checking `tcpdump'...                                   not infected
Checking `top'...                                           not infected

```

and....

```
Searching for suspicious files and dirs, it may take a while... The following suspicious files and directories were found:  
/usr/lib/debug/.build-id /lib/modules/4.15.0-20-generic/vdso/.build-id /lib/modules/4.15.0-38-generic/vdso/.build-id
/usr/lib/debug/.build-id /lib/modules/4.15.0-20-generic/vdso/.build-id /lib/modules/4.15.0-38-generic/vdso/.build-id

```

Google investigation shows this "could" be a false positive. However......

```
$ dpkg -S /usr/sbin/tcpd
dpkg-query: no path found matching pattern /usr/sbin/tcpd

```

a manual search finds tcpdump file which cannot be opened. > "Could not display "tcpdump". There is no application installed for "shared library" files.


A further search does not reveal 
> /usr/lib/debug/.build-id /lib/modules/4.15.0-20-generic/vdso/.build-id /lib/modules/4.15.0-38-generic/vdso/.build-id
/usr/lib/debug/.build-id /lib/modules/4.15.0-20-generic/vdso/.build-id /lib/modules/4.15.0-38-generic/vdso/.build-id


I'm trying to verify if these are false positives or to compare the checksum. 

Can anyone assist with this dilemma?

---

### Post by TheFu on 2018-11-04
tcpd is part of the tcp-wrappers tool.  It has nothing to do with tcpdump.
Everytime I've hunted down any root-kit-searching warning, it has always been a false positive to the point that I've removed the 2 tools.

---

### Post by peacefull on 2018-11-04
Thanks for that, Fu.

I've read others posts and come away believing that it's a false positive, HOWEVER, I'm a bit overly paranoid with a recent hack attack on this machine. Perplexing even more, is a lack of directory or file along the stated path, yet, it reads INFECTED.  

Could this be a warning of an infected wlan card??? 

The question might evoke giggles from the pros, of which I am not.

---

### Post by TheFu on 2018-11-05
> **peacefull said:**
>  
Could this be a warning of an infected wlan card??? 

Not if it isn't a govt after you.

---

### Post by peacefull on 2018-11-05
> **TheFu said:**
> Not if it isn't a govt after you.

Realistic scenario....
The psycho in question has mega bucks and is Machiavellian deceitful. She could easily hire a former military/cop/govment snoop to do the dirty work for her. They would have resources and ability to breach a pc. 

I absolutely hate having to imagine this. Paranoid, yes...but for a very good reason. 

I have another wlan that was bought for a hackintosh conversion (which hasn't been done yet). Supposing I swap out the wlan card, wouldn't the swap eliminate 1 such possibility of spyeware?

---

### Post by TheFu on 2018-11-06
You should buy a chromebook, run chromeOS and never use any other computing device on any network.

Infecting firmware requires expertise in **that specific firmware** and physical access to it.  That is why I said a govt would need to be involved. It isn't a 1-man job. I'm pretty paranoid, but I only worry about the physical hardware being modified during travel. There are much easier ways to attack a computer system than modifying firmware for addon devices. 

I suspect Apple is taking steps to prevent any of their OSes from running on non-Apple hardware in the future.  There was a story about that yesterday confirming that Apple is adding T2 chips for security to some of their new computers.

---

