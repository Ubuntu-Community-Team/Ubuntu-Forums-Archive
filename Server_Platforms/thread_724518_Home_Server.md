---
title: "Home Server"
date: 2008-03-14
forum: Server Platforms
---

### Post by SuperMiguel on 2008-03-14
Well simple question why do i need a homer server?? advantages??? how can i use on my day to day life??? thanks :)

---

### Post by HermanAB on 2008-03-14
Well, if you got to ask, then you don't need one.

However, if you need some ideas for servers:
[LIST]
[*]MP3 music
[*]Web site
[*]Email
[*]FTP
[*]Samba
[*]Print
[*]Scan
[*]Fax
[/LIST]

Cheers,

Herman

---

### Post by Brazen on 2008-03-14
um, well, that's really only something you can answer.  All I can tell you is what I use my home server for.

I use my home server primarily as a file server.  I have a laptop, plus there's my work laptop, and a desktop computer in addition to the server, so it's nice that I can keep all my files in one place and easily access them on any computer.  Plus I use RAID1 in my server so all my data has a little extra protection.  These are things like pictures and home movies, old college papers, music, iso copies of purchased software (in case the cd goes bad), etc.

I also have mysql and apache on it for playing around with web programming and run the web-based torrentflux-b4rt on it.  Torrentflux is nice cuz I can download the large Ubuntu isos as torrents.  I'll get several at a time going then just leave it and my desktop/laptop is free to do whatever else or I can leave and check the download the next day or whatever.

Also, my printer has a built-in network card and print server, otherwise I would use my Ubuntu server for that, too.

---

### Post by Dr Small on 2008-03-14
I use my home server as a webserver, ssh server, fileserver and to stream audio occasionally. But the choice is your's, as to what you wish to use it for.

Dr Small

---

### Post by SuperMiguel on 2008-03-14
so if i have a computer with a AMD athlon 4200+ 2.2ghz, 1gb of ram and 320GB hard drive.... will this be a good configuration for a server??? will it be fast?

---

### Post by Dr Small on 2008-03-14
I have much less than you, and my server runs fast.

---

### Post by SuperMiguel on 2008-03-14
what will install on my server to make a domain, so that my other computers ask for login and password and my server control who logs and who uses my internet line.. like use my server for like mail server, file server and also as a firewall and like a "domain server"??

---

### Post by FakeOutdoorsman on 2008-03-14
> **SuperMiguel said:**
> so if i have a computer with a AMD athlon 4200+ 2.2ghz, 1gb of ram and 320GB hard drive.... will this be a good configuration for a server??? will it be fast?

I use a Pentium II 400 MHz as a web development server, torrent seeder, and storage for automated database backups.  For what it does It doesn't seem any slower than my desktop P4 3 GHz which also has Apache, etc, but it uses 1/3 the power.

Web server installation instructions on the Ubuntu Wiki: [Apache, PHP, mySQL]("https://wiki.ubuntu.com/ApachePHPMySQL")

---

### Post by igknighted on 2008-03-14
> **SuperMiguel said:**
> what will install on my server to make a domain, so that my other computers ask for login and password and my server control who logs and who uses my internet line.. like use my server for like mail server, file server and also as a firewall and like a "domain server"??

If you want something easy to set up, look at SME Server.  It has a setup wizard that should walk you through the things that you asked about, much easier than editing config files (although if you really want to understand it all, editing config files could be a good thing).  It's hard and takes a while to learn, but if you really want to get into servers it's worth it.  But to just get one up and running, SME is the way to go.

---

### Post by Iowan on 2008-03-15
> **SuperMiguel said:**
> Well simple question why do i need a homer server?? advantages??? how can i use on my day to day life??? thanks :)I use my server(s) as training tool(s).  I absorb more through my fingertips than eyeballs, so I learn better by doing than reading - unfortunately, the to-do list is growing faster than the pile of old computers I'm using for trainers.

---

### Post by jonabyte on 2008-03-15
i have one as a file backup server, one as a web server and the last as a test/play server to learn try new things on it

---

### Post by kwacka on 2008-03-16
I use it mainly for streaming, got an old Sharp Zaurus plugged into kitchen radio/cd for internet 'radio' (using xnvcviewer to control box in attic) using wifi. Also wired network to study, internet connections up there as well, plus storage, connected to network media player attached to TV.

I just wish I was in this guy's league!  [http://www.pbs.org/cringely/pulpit/2004/pulpit_20040930_000460.html](http://www.pbs.org/cringely/pulpit/2004/pulpit_20040930_000460.html)

---

### Post by netlogic on 2008-03-16
1. podcast catcher (podget)
2. ftp  with ssl (vsftpd)
3. File Sharing (Samba)
4. dhcp/dns (dnsmasq)
5. pppd dial-in server (from PDA to check email)
6. http (apache)
7. print server (cups)
8. rtorrent (torrent client)
9. freshclam scanner (scan the weaker OS)
10.hellanzb (nzb server)
11. squid (proxy)
12. snort (ids)
13. pxe boot server

=======
9.5 year old server
98megs@amd/266mhz/3 drives total of 600gigs.
Try to do that with Win2008.

---

