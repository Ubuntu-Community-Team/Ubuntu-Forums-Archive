---
title: "sudo apt-get update    problem"
date: 2005-09-22
forum: Ubuntu Backports
---

### Post by QueenGambit on 2005-09-22
i've been trying: sudo apt-get update   for 2 days but no luck. 
Yesterday, the output was:

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe chmlib 0.35-5
  Could not connect to us.archive.ubuntu.com:80 (82.211.81.151), connection timed out [IP: 82.211.81.151 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/c/chmlib/chmlib_0.35-5_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/c/chmlib/chmlib_0.35-5_i386.deb)  Could not connect to us.archive.ubuntu.com:80 (82.211.81.151), connection timed out [IP: 82.211.81.151 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

i tried it again today and the ouput is a bit different but still doesnt work:

E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory

Any idea?  :---) 
Help me plz people.

---

### Post by katu on 2005-09-22
The first error seems to be a connection problem, i.e. maybe the us repository was down. You could try connecting to a different repository, try editing /etc/apt/sources.list 
and change for instance the:
us.archive.ubuntu.com    for one of the mirrors that can be found here:
[https://wiki.ubuntu.com/Archive](https://wiki.ubuntu.com/Archive)

I made a quick check and it also seems that:
uk.archive.ubuntu.com  to works.

The second message shows up, when you try to use apt, when it is already running on a different terminal, meaning you're trying to open a second session of apt. Check if you don't have an open session somewhere.
Hope this helps,
Katu

---

### Post by QueenGambit on 2005-09-22
[QUOTE=katu]The first error seems to be a connection problem, i.e. maybe the us repository was down. You could try connecting to a different repository, try editing /etc/apt/sources.list 
and change for instance the:
us.archive.ubuntu.com    for one of the mirrors that can be found here:
[https://wiki.ubuntu.com/Archive](https://wiki.ubuntu.com/Archive)

I made a quick check and it also seems that:
uk.archive.ubuntu.com  to works.

The second message shows up, when you try to use apt, when it is already running on a different terminal, meaning you're trying to open a second session of apt. Check if you don't have an open session somewhere.
Hope this helps,
Katu[/QUOTE]

Thanks for helping, Katu!
But still it didnt work
I've tried uk archive as u said, also some other archives but every time it gets to 30% or 80% it just stays still and says that "couldnt connect to uk.archieve.ubuntu.com"
I also tried several backports as well other than [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) but it seems not to solve the problem.
Here is my sources.list:
## Uncomment the following two lines to fetch updated software from the network
deb [http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

I've just moved in university campus since last week. Dont know if that problem is realated to university proxy/firewall? I dont think it is.

---

### Post by katu on 2005-09-22
your sources.list is ok. It works on my computer. It might be a thing with the connection. 
Can you ssh out someplace? I'm asking, because I encountered a network once where you could only use webbrowsers through a proxy. Connecting through ssh and, as it turned out, apt-get was disabled... the effect as I remember was a bit similar to what you're getting.

It's a longshot, but if that is the case, you should talk to the administrators and ask them about this...
sorry I can't be much more help,
Katu

---

### Post by QueenGambit on 2005-09-23
[QUOTE=katu]your sources.list is ok. It works on my computer. It might be a thing with the connection. 
Can you ssh out someplace? I'm asking, because I encountered a network once where you could only use webbrowsers through a proxy. Connecting through ssh and, as it turned out, apt-get was disabled... the effect as I remember was a bit similar to what you're getting.

It's a longshot, but if that is the case, you should talk to the administrators and ask them about this...
sorry I can't be much more help,
Katu[/QUOTE]
 Finally I get it done. 
The thing is my campus network requires every outgoing web-traffic to be tunnelled through a web cache proxy. Therefore before we can apt-get, we have to run the command:

export http_proxy="proxy_address"

I appreciate ur help, Katu.

---

### Post by hakimu on 2005-10-10
to get rid of the permission problem run apt-get update as root, or simply

    **sudo apt-get update**

if you get the other errors, probebly is somthing wrong with the proxy setting

    **export http_proxy="http://proxyIPAddress:ServerPortnumber"**

and the you can run sudo apt-get update

Hope it works:cool:

---

