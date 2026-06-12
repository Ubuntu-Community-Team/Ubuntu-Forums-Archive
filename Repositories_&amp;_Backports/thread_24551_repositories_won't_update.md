---
title: "repositories won't update"
date: 2005-04-07
forum: Repositories &amp; Backports
---

### Post by godsdog on 2005-04-07
Hi all,
I'm pretty new to Ubuntu but not a total newbie to Linux

I'm running Warty 4.10 with these repositories:
           (cut and pasted from /etc/apt/sources.list)

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted

Today I ran apt-get update and the first line says:
 [Connecting to archive.ubuntu.com (1.0.0.0)
which is obviously wrong, so I aborted and tried to ping "http://archive.ubuntu.com" and got :"unknown host"
I upgraded packages after the initial install but not since then.

I've looked at some of the logs but don't see anything that looks like it might point to the problem.
I'm clueless as to what might be wrong.
Any ideas?
Forgive me if this has been covered here but search terms I've tried so far return no matches.

TIA
gd

---

### Post by primeirocrime on 2005-04-07
I had that problem before. The way I solved it was to put my ISP DNS in resolv.conf instead that of the router that ubuntu automaticaly gets.


so ...

at the terminal I wrote 

$ sudo gedit /etc/resolv.cof

then I comented the line with the nameserver provided with:
[color=black]
#[/color]nameserver  [whatever number]

and then add your ISP dns, they should come up somewhere in your router.

nameserver  [first dns]
nameserver [second dns]

---

### Post by maqi on 2005-04-07
There's nothing wrong with what apt-get is doing. Just let it go instead of aborting and see what happens.

As to the ping: I suspect that the server (like many) is configured to ignore ICMP echo requests (or pings). But the server IS there all the same :)

maqi

---

### Post by godsdog on 2005-04-07
[QUOTE=primeirocrime]I had that problem before. The way I solved it was to put my ISP DNS in resolv.conf instead that of the router that ubuntu automaticaly gets.


so ...

at the terminal I wrote 

$ sudo gedit /etc/resolv.cof

then I comented the line with the nameserver provided with:
[color=black]
#[/color]nameserver  [whatever number]

and then add your ISP dns, they should come up somewhere in your router.

nameserver  [first dns]
nameserver [second dns][/QUOTE]

Thanks!
I'll give it a shot and see what happens

---

### Post by godsdog on 2005-04-07
[QUOTE=maqi]There's nothing wrong with what apt-get is doing. Just let it go instead of aborting and see what happens.

As to the ping: I suspect that the server (like many) is configured to ignore ICMP echo requests (or pings). But the server IS there all the same :)

maqi[/QUOTE]

I forget the exact message but when I did let it finish once,  nothing was downloaded... something about a connection error. At first I thought DNS problem but I get web pages ok.

---

### Post by godsdog on 2005-04-08
Primeirocrime,

That did the trick!  :-P 

Thanks
gd

---

