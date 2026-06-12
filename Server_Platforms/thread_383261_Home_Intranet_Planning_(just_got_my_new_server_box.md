---
title: "Home Intranet Planning (just got my new server box back home)"
date: 2007-03-13
forum: Server Platforms
---

### Post by hblaw on 2007-03-13
Hi all,

Just got my new server box back home yesterday evening.  I am not new to Linux/Ubuntu but I am really not a tech guy in strict sense, so my questions may sometimes be somewhat off the direction. (I am not native speaker, please ask me for clarification if needed).

**1. Environment.**

I have a router with wireless support, which connects to Internet via ADSL (always online).  My server will connect to the router as a file/web/printer server for my home intranet.  I have got a windows laptop (my gf) and a Mac & Linux laptop (me) simultaneously working at home (quite complex I know). My server has two Ethernet port, and two 80g hard disk (IDE).  All my laptops connect to the network over wireless lan, so I don't want anything unnecessary connected to my laptop (including PC speaker).  I want to use Ubuntu Dapper (6.06).  Assuming that the IP for my server is 192.168.0.100 for intranet, and my Internet IP (router) is 12.34.56.78.

**2. Primary Targets.**

*a) File server: *  Only my intranet can access the file server.

i) Auto-Mount at Boot.  All my laptops can auto-mount a network disk/partition provided by my server upon startup (say, "Network Disk" on the right hand side of Finder, or "G:" in windows).

ii) Mount at Request.  One or more additional partition/disk can be mounted by my laptops as required (say, "Application Backups", when I download some new software and want to save a copy).

iii) Removable media.  When I insert a USB stick/portable hard disk into the USB port of my server, it automatically mounted to certain directory and accessible via network (so I can share a same portable disk simultaneously among my laptops, and can drag large files to my portable disk from server while my laptop is off).

iv) Anti-Virus.  I want a scheduled scan of all files accessible by windows laptop to ensure they aren't contagious.  Twice a week is good enough.

*b) Printer Server.  * Only my intranet can access the printer server.

I have a HP 1020 Laserjet which will be connected to the server.  I want to print from any of my laptop as if the printer were connected to my laptop directly, i.e. I just click print, choose printer, and then it prints.  I do NOT want any special application installed on my laptop (i.e. requiring me to drag my word document to a special directory, or convert it into some rare format, etc.).

*c) Web Server & Applications. *

i) Services.  I want a standard LAMP server for my intranet ONLY, i.e. only laptops in my home can connect to www services provided by my server.  But I want a remote command line access to my server (when I am at work).  It should be secured. (I guess an SSH service with no-password but certificate authentication would do, but don't know exactly how to implement - suggestions?)

ii) Firewall.  Any suggestion for firewall configuration?

iii) BitTorrent.  I want a BitTorrent client installed on my server, and I can access via web (home)/SSH (remote access) to control it.  So it can download large files when I am not at home/at sleep easily, and the downloaded files go automatically to Auto-Mount disks mentioned above (laptop can access them).

iv) Download.  I want a download client for files other than BitTorrent but manageable via web (home)/SSH (remote access), i.e. I can open [http://192.168.0.100/download/](http://192.168.0.100/download/) on my laptop, and there is a textbox, and I copy-paste the download URL and submit, the server will automatically download that URL, and I can upload a text file with multiple URLs, and the server can download all of them.

v) Blog, Album & Forum.  I want a personal diary blog, a www based photo gallery, and a BBS like interface to organize information (so that I can group things into topics, and searchable) with attachment support, any suggestion? (Intranet access only).

vi) Music. My 2.1 speaker will be connected to the server.  I want to download music and store them on the server, and control the server to play aloud, i.e. I can open [http://192.168.0.100/music](http://192.168.0.100/music), and there is a list of music, and I click one of them, and the server can play to the speaker (not to my laptop earphone).  I also want the ability to adjust volume remotely.  [Further step: Is there any service/application that allow me to play on laptop using the speaker, i.e. the speaker is connected to server physically but is connected to my laptop virtually (any driver needed for laptops?) (I know Apple has this technology).]

*d) Backup. *

Directory Auto-Mirror:  I have some very important documents, I want a directory on my hda (say, "important_files") and a directory on my hdb (say "important_files_copy") have exactly the same thing (mirror each other), and I can access one folder from my laptops (by mounting network disk or via FTP) and the server will automatically mirror it to the other directory, and in case of disk failure I can have a safe copy.  Data generated by WWW service (i.e. www directory, mysql databases) and configuration files (if necessary) shall also be included in this mirror.  I have Promise Raid controller, I don't know if it helps (but I don't want my two 80g &#61664; one 80 gig, only a few directories need mirroring).  The size for mirrored directories will not be greater than 10gig.

*e) Security. *

Placing it as the last item doesn't mean it is least important.  The following are some ideas and I don't know whether they are feasible.

i) Administration Port.  Since the server has two Ethernet ports, is it possible to allow only one of them be administration port?  I.e. only SSH from that port (Port A) can execute (higher level) administration function, and connections from another port (Port B) can only login as a normal user with limited administration function.  So that I can only physically connect to Port A at home to do bigger changes (such as install new applications), and Port A will not connect to router.  Port B is connected to router and I can SSH remotely from my office to execute apt-get update & upgrade like function and start a download etc, and services are provided through Port B.  Is all these possible? (I know some user privilege things must be done :)

ii) SSH login.  For remote login, is it possible to just allow the ip address (or range) from my office to access?  Is it possible to allow only a specific computer (say, my computer at work, or my laptop when I am traveling, with MAC address as ID) to login (irrespective of IP address)? I will do very limited function through remote access, i.e. just start downloading something via BitTorrent, watch server traffic report, system info (basic), error report, etc, so is it possible to limit the range of commands one can execute remotely?

**3. Conclusion.**

So, this is what I want to build. Please suggest whatever is in your mind.  If this is successful, I plan to expand with a scanner and maybe some other things.

I think I should get a notebook at hand and write down every step I took to install the server.  It will be fun! HOHO

---

### Post by gombadi on 2007-03-13
Too many questions.

If people answer all or some of the questions in this thread it will get too confusing to follow everything.

I suggest you break it up and ask about each section (file server, web server, applications, print server etc) in a separate thread.

A quick look indicates that yes most of what you want is possible.

Suggest you install it and get ssh access working as you want first.

That means how you want to layout the two 80G disks is the first question/thread you should create.

Have fun.

---

### Post by alamba on 2007-03-13
Quite a setup. Me likes. Like Gombadi said most of it is possible. I'd suggest adding a VPN server and only opening the port for that over your router. Once u're in, you can always ssh into the local IP interface. 

The backup bit can easily be done using a rsync script. I'd also suggest you have a look at backupPC. My server at home goes into all the laptops and desktop on the network on a timely basis and pulls the data and backs it up on the server.

A

---

### Post by hblaw on 2007-03-13
> **gombadi said:**
> Too many questions.

I suggest you break it up and ask about each section (file server, web server, applications, print server etc) in a separate thread.



Sure. I will start to organize it into different threads :) With this post I think asking questions in separate threads won't be that difficult for me.

---

