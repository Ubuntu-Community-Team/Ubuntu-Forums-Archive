---
title: "wget hangs when trying to download"
date: 2005-11-20
forum: Repositories &amp; Backports
---

### Post by JuhazOne on 2005-11-20
My wget seems to hang every time I try to download anything from the net. For example:
> > wget [www.ubuntuforums.org](www.ubuntuforums.org)
--23:55:30--  [http://www.ubuntuforums.org/](http://www.ubuntuforums.org/)
           => `index.html'
Resolving [www.ubuntuforums.org](www.ubuntuforums.org)...

And that's all. It hangs and doesn't respond to ctrl+c.
(Actually, my computer seems to have some weird problem that occasionally some processes hang so that even root can't kill them with kill -9 <pid>. This happens with wget, too. As far as I know, this is unrelated, though.)

I tried to give wget an ip only. Here's what happens:
> > wget [http://64.21.33.9/](http://64.21.33.9/)
--00:15:16--  [http://64.21.33.9/](http://64.21.33.9/)
           => `index.html'

And wget hangs.

If it weren't for the problem with the ip's, one might suppose that there's a problem with DNS. My Opera browser also seems to lag quite a bit (up to 15 seconds) occasionally when I try to browse a new server.

Note that wget doesn't hang when it doesn't try to access the Internet. Typing ```
wget --help
``` or ```
wget --version
``` work just fine.

I'm using kernel 2.6.12-9-386. Wget is version 1.10 and apt-get says it's the newest version. My wget is normally aliased to wget -c -nc but unaliasing it has no effect. The wget binary is located at /usr/bin/wget if that's useful info for someone. I'm behind a NATted network and I use DHCP.


Any ideas what could be wrong?

---

### Post by oskude on 2005-11-20
hmm,

i get the "index.html" with "wget www.ubuntuforums.org"...
can you open [www.ubuntuforums.org](www.ubuntuforums.org) with firefox ?
what does ping and traceroute say for ubuntuforums.org ?

---

### Post by JuhazOne on 2005-11-20
Firefox works just fine. So does ping.

> > ping [www.ubuntuforums.org](www.ubuntuforums.org)
PING [www.ubuntuforums.org](www.ubuntuforums.org) (64.21.33.9) 56(84) bytes of data.
64 bytes from wailuku.xlogicgroup.com (64.21.33.9): icmp_seq=1 ttl=48 time=126 ms
64 bytes from wailuku.xlogicgroup.com (64.21.33.9): icmp_seq=2 ttl=48 time=125 ms
64 bytes from wailuku.xlogicgroup.com (64.21.33.9): icmp_seq=3 ttl=48 time=125 ms
64 bytes from wailuku.xlogicgroup.com (64.21.33.9): icmp_seq=4 ttl=48 time=126 ms

--- [www.ubuntuforums.org](www.ubuntuforums.org) ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3002ms
rtt min/avg/max/mdev = 125.916/126.049/126.293/0.383 ms

traceroute hangs and becomes unkillable. It seems this problem is more common than I thought.

OpenOffice Writer ( /usr/lib/openoffice/program/soffice.bin ) hangs like this, too. It shows the splash screen, then hangs and the process becomes immortal.

Is this a bug in some library or something...?

---

### Post by JuhazOne on 2005-11-23
Problem solved by updating the kernel from 2.6.12-9-386 to 2.6.12-10-686.

---

### Post by JuhazOne on 2005-12-23
Oh crap... the problem is back again. And my kernel is still the same 2.6.12-10-686 that previously fixed the problem.

---

### Post by JuhazOne on 2005-12-26
So far the affected programs seem to be:
[LIST]
[*]wget
[*]nmap
[*]traceroute
[*]sudo
[*]OO writer
[/LIST]

Many of them are network-related but some are not.

Anyone got any ideas...?

---

### Post by GTvulse on 2005-12-26
[quote=JuhazOne]
Anyone got any ideas...?
[/quote]

Yes, all those are symptoms of a dying network interface. If your NIC is an integrated ethernet, it could even be the tell-tale sign of a dying mainboard. OR, your CPU is overheating... Sorry to be the bearer of bad news...

---

### Post by shin on 2005-12-26
Imho could be a problem with disk. I don't really know much about linux scandisks etc but maybe give it a try. Or maybe some kind of filesystem damage. I don't think it is network or cpu related problem.

---

### Post by JuhazOne on 2005-12-30
[QUOTE=dradul]Yes, all those are symptoms of a dying network interface. If your NIC is an integrated ethernet, it could even be the tell-tale sign of a dying mainboard. OR, your CPU is overheating... Sorry to be the bearer of bad news...[/QUOTE]

It's possible in the sense that the NIC is old. More than five years at least, possibly even more.

Is there a way I could be sure without having to try another NIC?

---

### Post by GTvulse on 2005-12-31
[QUOTE=JuhazOne]It's possible in the sense that the NIC is old. More than five years at least, possibly even more.

Is there a way I could be sure without having to try another NIC?[/QUOTE]
You would have to run a hardware test. There are some benchmarking software packages that could help (I haven't used any in a long time, I don't recall the name of any either :-P ). Do make sure that you don't try something like pinging a public web site for a long time or something of the sort, you'd only get yourself in trouble (as in being the source of a DoS attack).

---

### Post by JuhazOne on 2006-01-07
Ok. So I got it all working again now.

I asked the people on #ubuntu (@freenode) about this and they (too) suggested I'd try another NIC. I decided to try the one that's integrated into my motherboard (haven't been using it since Windows doesn't like it). Well, the network adapter got detected and configured automatically and wget & friends work now. :)

It is unsure whether the problem was with the NIC itself or its drivers.

The NIC was Intel Pro/100+. When I last looked (a long time ago), Windows detected it as "Intel Pro/100+ Management Adapter 82559 10/100MB". I believe it was bought in March 2000.

---

### Post by JuhazOne on 2006-01-18
Oh crap........

Guess what? The problem is back once more.

This time I'm ditching my current installation of Ubuntu and starting from scratch again. Will see if it helps.

---

### Post by stream303 on 2006-01-23
[QUOTE=JuhazOne]
...  If it weren't for the problem with the ip's, one might suppose that there's a problem with DNS. My Opera browser also seems to lag quite a bit (up to 15 seconds) occasionally when I try to browse a new server.[/QUOTE]

I'd take a look at your **/etc/resolv.conf** file

If you are running DHCP, I'll bet that the nameservers are pointing to an internal DNS of your router, which causes the delay as it times-out.  Does it look something like this?

domain yourisp.net  (or search yourisp.net)
nameserver 172.16.0.254

The private ip address is a giveaway that the system is timing out while trying to use the internal dns of a router, etc, and not your actual isp's dns first.  We can fix this issue by editing /etc/dhcp3/dhclient.conf 

I wrote a quick page about this issue at:
[http://www.greertech.com/nixnotes/dhcpfix.html](http://www.greertech.com/nixnotes/dhcpfix.html)

Let me know if this works for you...

---

