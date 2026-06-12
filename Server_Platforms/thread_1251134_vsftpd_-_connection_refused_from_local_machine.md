---
title: "vsftpd - connection refused from local machine"
date: 2009-08-27
forum: Server Platforms
---

### Post by Gornjak on 2009-08-27
Hi,

I'm running Ubuntu Server 9.04 in VirtualBox as my webserver. However there's a small problem.

I've installed vsftpd like this:
sudo apt-get install vsftpd

After that I've edited config to allow local connections. But I still can't connect to the server. Even if I try and type "ftp localhost" in console. It always says connection refused.

I've tried from windows using WinSCP and it asks me for user / pass and after that it says that connection is refused.

Any ideas? I kind of need ftp connection to the virtualbox server so I can connect to it with ultraedit.

Thanks for your replies.

Edit: I forgot to launch the server. No comment.
Edit: If any mod can delete this thread you're most welcome to do so.

---

### Post by Trigger on 2009-09-28
Same deal....PLEASE HELP!

---

### Post by superc0w on 2009-10-10
Trigger make sure your server is vsftpd server is started.  It doesn't start by default.

---

### Post by uDavis on 2009-10-27
Exact same issue here. I am finding the vsftpd too secure to install correctly. All I can get is a connection refused.

I'm doing a sudo /etc/init.d/vsftp start  It says it is running but I don't really seem to have a tool to check it.

What I am missing is the configuration needed to run vsftpd correctly. At this point any configuration that simply works would be welcome.

I did the apt-get install
I did the vsftpd start

and that is where all success ends.

I went through this long iptables thing to no effect.

---

### Post by Lars Noodén on 2009-10-28
A tool to test the connection must be run from another machine: nmap or zenmap, the graphical front-end to nmap.  That is, if you need more information from the client that what the ftp client (e.g. ncftp)  is giving.  However, given the situation with FTP and the complexity of setting up FTPS correctly, what job are you trying to do?

OpenSSH-server comes with SFTP built-in and working securely out of the box.  It works like FTP, but is a completely new protocol.  You can even use clients (depending on OS) like  Fugu, Filezilla, Fetch or Cyberduck.  
There are even hacks like sshfs which let you access the other machine via a folder.

vsftpd will let you serve anonymous ftp (no login, read-only) or FTP tunneled over SSL (aka FTPS), neither are provided by OpenSSH-server.

Gornjak,  Trigger,  uDavis can I ask how you found out about vsftpd and the decision to try it?

---

### Post by Iowan on 2009-10-28
[Here]("http://ubuntuforums.org/showthread.php?t=218630") is a How-To page that uses **vsftpd**.

---

### Post by uDavis on 2009-10-28
I had to do this to make it work when I got the same error message.

sudo apt-get remove --purge vsftpd
sudo apt-get install vsftpd

I had made changes to the vsftpd.conf file after trying to follow a lot of loose web advice and apparently hosed my installation. I could never get past the connection refused message until I did the above two commands and started over.

---

### Post by uDavis on 2009-10-28
Lars, it came up in a google search as an easy to use start up FTP server. I'm only doing a command line install and am coming from an IIS env so I am struggling a bit. apt-get, chmod,and nano are all foreign concepts at this point.

I used Nmap from a windows installation to check my Ubuntu ports. In windows the winpcap program should be installed from the winpcap 4.1x downloads

[http://www.winpcap.org/](http://www.winpcap.org/)

For the nmap windows install. Don't check the winpcap install part and it moves along. It produces a vcredist error but that should be ignored. nothing is needed to fix that. It will install itself and be ok.

If by chance the nmap install failes on wanpacket.dll, packet.dll and winpcap.dll.  windows should be booted in safe mode and these three files deleted. Then the nmap install can proceed again.

---

### Post by uDavis on 2009-10-28
Also Lars, I was first trying the proftpd server based on input from these forums but for the life of me I couldn't find the software in the jaunty distribution. Even after opening up all the sources.  I swithed to vsftpd and was able to apt-get it. So just to make my life easier and quicker I'll stick with what I can find.

---

### Post by Lars Noodén on 2009-10-29
Thanks for answering.
If it's not too nosy a question, why specifically FTP?

> **uDavis said:**
> Also Lars, I was first trying the proftpd server 

It's in the package proftpd-basic.

---

