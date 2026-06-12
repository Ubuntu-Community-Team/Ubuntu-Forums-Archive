---
title: "Apache Loads Slow - High Server Load"
date: 2006-11-16
forum: Server Platforms
---

### Post by DannyG on 2006-11-16
Hi,

I currently pay for a VPS, its with a company called slicehost.com. The VPS is basically a naked server with a minimal installation of Ubuntu Server.

So I have installed Apache onto it with PHP and MySQL following [this guide]("http://www.howtoforge.com/perfect_setup_ubuntu_6.06"), and have also installed Postfix and Courier-IMAP/POP3 and ProFTD using that guide.

Everything works perfectly, no technical problems at all. However, when I try and access my website there is a 3-5 second pause where the status bar shows "Wating for dannyg.co.uk..." before it loads. When I restart the server, this problem disappears and the site loads lightning fast, but after a couple of hours it back to normal

So I check my status script ([http://www.dannyg.co.uk/status/](http://www.dannyg.co.uk/status/)) it shows that I have a very high memory and swap usage. I am only running Apache with 3 MySQL database connections, a single client psyBNC Bouncer and an empty Teamspeak server. My website is NOT busy, so I doubt my volume of traffic is the problem.

It's worth noting that when I restart, the memory load drops to about 40% and the swap usage is non-existent.

When I check my "5 Highest CPU Processes" in my Status Script I have the following:

CPU% | CPU TIME | PROCESS NAME
0.0 00:00:03 /usr/sbin/apache2 -k start -DSSL
0.0 00:00:00 proxymap -t unix -u
0.0 00:00:00 smtpd -n smtp -t inet -u -c -s 2
0.0 00:00:04 /usr/sbin/apache2 -k start -DSSL
0.0 00:00:03 /usr/sbin/apache2 -k start -DSSL


Anyone got any idea's on why my server load is so high, and is the problem with my website taking a bit longer to load pages?

Or is this normal?

Thanks,
Daniel.

---

### Post by tturrisi on 2006-11-17
I suspect bad ram on the server.  When I looked, your status page said:
Memory Used:  92%  0.23GB / 0.25GB

The odd part of that ratio is 0.23GB used out of a total 0.25GB.  That means it is using approx 230 MB out of 256 MB.  Some application or service is leaking memory or some ram is bad.

If there are any php-mysql scripts that load up at startup then there could be poorly coded scripts can leak memory.  For azample, a script that is missing msql_close function can bleed memory.

Were it my server I'd first have the physical ram checked out, then if no joy I'd plow into the apache2 configs and cull the mods_enabled removing unneeded mods.  And I'd opt for at LEAST a gig of ram.

---

### Post by paul.maddox on 2006-11-18
Yes, it certainly looks like RAM is your main problem here.
Looking at your stats page, it seems like the server is using a lot  of swap space. It will only start using swap space when RAM is not available to use so ideally you don't want any swap space used.

I notice you have quite a bit installed on the box considering you only have 256MB RAM.

Are you using the default apache config? You could try decreasing the number of child processes started by default in the configuration if your server is not going to be busy.

How big are your MySQL databases? MySQL will try and cache the databases to memory to avoid disk operations where possible. You may need to edit the MySQL config file (my.cnf) to decrease the cache size to match your memory size.

Alternativly, phone up your VPS provider, give them a little bit of charm on the phone and see if you can get the ram upped to 512 MB or ideally 1GB.

---

### Post by madmonk3y on 2007-06-12
psybnc could be the problem too.  There is some issue with psybnc and recent versions of glibc.  I post about it here:

[http://ubuntuforums.org/showpost.php?p=2829953&postcount=1](http://ubuntuforums.org/showpost.php?p=2829953&postcount=1)

Try the above link.  If you want to install PsyBNC knowing that and why it won't work correctly, here's the packages you need to be able to make menuconfig and have the compile complete (with warnings and future instability):

[http://ubuntuforums.org/showpost.php?p=2830116&postcount=5](http://ubuntuforums.org/showpost.php?p=2830116&postcount=5)

---

