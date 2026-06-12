---
title: "What Server OS to use on an Ubuntu network"
date: 2012-11-01
forum: Server Platforms
---

### Post by Nick_C on 2012-11-01
On an Ubuntu network what do you all use as your server OS?  I know there is an 'Ubuntu Server' but is that the best option or are there other alternatives.

---

### Post by lisati on 2012-11-01
It can depend on what you want to do. For what I use mine for (email, web pages) Ubuntu server works well.

---

### Post by markbl on 2012-11-01
Around here of course we are all generally going to recommend Ubuntu server. However, Ubuntu is based on debian and for a simple server (e.g. as a virtual guest) I often just use the standard debian [netinst](http://www.debian.org/distrib/netinst) download because it is tiny download and more minimal install.

---

### Post by jerome1232 on 2012-11-01
I just use Ubuntu Server 10.04 LTS, I like the fact that it is not a rolling release and will stay fairly static, I run it headless, no gui.

---

### Post by LHammonds on 2012-11-02
I don't have any Ubuntu/Linux desktops.  I have a Windows Active Directory network with Windows XP/7/8 PCs but I do have several Ubuntu Servers.

What server you use depends on your needs.  For file servers, I use Windows Server because of the integration with AD and the ease-of-use when it comes to my Windows clients and permissions.

I use vmware's ESXi (Linux) to host my virtual servers.

I use IBM's AIX (UNIX) to host my billing/scheduling services.

I use Windows server to host my public web site (built using .NET) and private Intranet (built using .ASP).

I use Ubuntu server for my database (MySQL), web apps (Apache+PHP), FTP (vsftpd), Minecraft, Network monitoring (Nagios), Print and VOIP (mumble) services.

**EDIT:** Oops, forgot to mention that I do have a print server running on Zentyal (based on Ubuntu)

LHammonds

---

### Post by Lars Noodén on 2012-11-02
The default answer is going to be Ubuntu Server.  You could also use Debian or OpenBSD.  But which services to you plan to run on your server?  That above all else might influence which OS to put on your server.

---

### Post by HermanAB on 2012-11-03
Depends...

If you don't mind fighting the good battle on the command line, then a Debian/Ubuntu server is fine.  

However, if you wish for wizards and want to go click happy as on a Windows server, then you should use the more mature Linux versions such as Suse, Mageia, Red Hat, Scientific and so on.

On a Mageia/Mandriva/PCLOS/Suse server, you never need to use the command line and you can move mountains with a few mouse clicks.

---

### Post by thnewguy on 2012-11-03
I found Zentyal is pretty good. It's basically Ubuntu Server, but comes with optional LXDE desktop and web-based control panel. It makes for a really fast, easy setup and you can choose whether to work from the command line or the web portal when doing remote work.

---

