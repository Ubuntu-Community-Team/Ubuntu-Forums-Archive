---
title: "Server setup recommendations request..."
date: 2006-06-23
forum: Server Platforms
---

### Post by sean talbert on 2006-06-23
I've installed a LAMP server to which I added ubuntu-desktop. This is being used for development on my home network (Linksys Wireless Access Point Router with 4-Port Switch). Not being too familiar with Linux, I'm looking for a few recommendations to get it completely set up:

Remote Desktop - I'd like to access the server from my WindowsXP box on the same network, and I was able to do this using Ubuntu's Remote Desktop and a VNC viewer on Windows (Home edition, no Remote Desktop). This works fine (hogs the CPU a bit) and isn't a problem since both are in the same room... just wondering if there is a better or more secure way to do this.

FTP - I need to set up FTP so that I can upload files from outside my LAN. Following the instructions in [http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p6](http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p6) ("apt-get install proftpd proftpd-common ucf"), I tried installing proftpd, but the package wasn't found. Any idea why? Any recommendation for another FTP? I was able to find the gFTP package. I've read that vsftp is good.

Security - My LAN is behind the router firewall, but I also have ZoneAlarm on my WindowsXP box to see what's going out and coming in. The router allows http traffic from outside my LAN to come in to the server, but I'm wondering if I should have something else (like ZoneAlarm) on there.

MySQL - I've used, and like, the MySQL Administrator for Windows, but I was unable to find this package. Is there one, or should I just download from MySQL ("Linux (non RPM package) downloads" or "Linux x86 generic RPM (statically linked against glibc 2.2.5) downloads" from [http://dev.mysql.com/downloads/administrator/1.1.html)?](http://dev.mysql.com/downloads/administrator/1.1.html)?) 

Thanks for your help

---

### Post by sean talbert on 2006-06-24
Remote Desktop - I setup openssh-server, and I've seen comments about tunneling VNC through SSH, but can't find more info on it. Links?

FTP - I setup vsftpd with local login, but I'd like to specify a list of allowed users rather than anonymous or local. Is there a way to do this? Also, is it possible to allow uploads but not downloads?

Security - Saw a comment about firestarter. Any good, is it necessary?

---

### Post by sean talbert on 2006-06-24
[QUOTE=sean talbert]Remote Desktop - I setup openssh-server, and I've seen comments about tunneling VNC through SSH, but can't find more info on it. Links?

FTP - I setup vsftpd with local login, but I'd like to specify a list of allowed users rather than anonymous or local. Is there a way to do this? Also, is it possible to allow uploads but not downloads?

Security - Saw a comment about firestarter. Any good, is it necessary?[/QUOTE]


Still have the questions above, but was able to get mysql-admin installed by adding universe and multiverse to my /etc/apt/sources.list.

---

### Post by houstonbofh on 2006-06-25
> **sean talbert]I've installed a LAMP server to which I added ubuntu-desktop. This is being used for development on my home network (Linksys Wireless Access Point Router with 4-Port Switch). Not being too familiar with Linux, I'm looking for a few recommendations to get it completely set up:
[/QUOTE]
As many answers as there are people.  Pick the one you like.
[QUOTE=sean talbert]
Remote Desktop - I'd like to access the server from my WindowsXP box on the same network, and I was able to do this using Ubuntu's Remote Desktop and a VNC viewer on Windows (Home edition, no Remote Desktop). This works fine (hogs the CPU a bit) and isn't a problem since both are in the same room... just wondering if there is a better or more secure way to do this.
[/QUOTE]
This is such a loaded term.  But first, what is "remote desktop?"  Or, more importantly, what part of it do you need?  First, let me admit my bias said:**
> 
FTP - I need to set up FTP so that I can upload files from outside my LAN. Following the instructions in [http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p6](http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p6) ("apt-get install proftpd proftpd-common ucf"), I tried installing proftpd, but the package wasn't found. Any idea why? Any recommendation for another FTP? I was able to find the gFTP package. I've read that vsftp is good.

Synaptic shows how repositories work quite well.  Also a google search can help.  For example, Looking for a Perl Library Net::Pcap [http://www.google.com/search?hl=en&q=ubuntu+net%3A%3Apcap](http://www.google.com/search?hl=en&q=ubuntu+net%3A%3Apcap) the third one down is [http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=libnet-pcap-perl&version=breezy&arch=i386](http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=libnet-pcap-perl&version=breezy&arch=i386) which shows that it in in Ubuntu, but in "Universe."
[QUOTE=sean talbert]
Security - My LAN is behind the router firewall, but I also have ZoneAlarm on my WindowsXP box to see what's going out and coming in. The router allows http traffic from outside my LAN to come in to the server, but I'm wondering if I should have something else (like ZoneAlarm) on there.
[/QUOTE]
Zone Alarm is for a operating system insecure by design.  Debin is the opposite.  You can install Firestarter, but there are no insecure open ports unless you install them so why bother?
[QUOTE=sean talbert]
MySQL - I've used, and like, the MySQL Administrator for Windows, but I was unable to find this package. Is there one, or should I just download from MySQL ("Linux (non RPM package) downloads" or "Linux x86 generic RPM (statically linked against glibc 2.2.5) downloads" from [http://dev.mysql.com/downloads/administrator/1.1.html)?](http://dev.mysql.com/downloads/administrator/1.1.html)?)[/QUOTE]
From google... [http://packages.ubuntulinux.org/hoary/admin/mysql-admin](http://packages.ubuntulinux.org/hoary/admin/mysql-admin)  Enable universe.

---

### Post by sean talbert on 2006-06-26
Thanks houstonbofh. I used VNC on Windows with Ubuntu's Remote Desktop while I was getting everything setup. SSH is fine going forward. Thanks for the firewall info and the link to the packages index. Still wondering about FTP. From above... 

FTP - I setup vsftpd with local login, but I'd like to specify a list of allowed users rather than anonymous or local. Is there a way to do this? Also, is it possible to allow uploads but not downloads?

---

### Post by spifbv on 2006-06-26
[QUOTE=sean talbert]Thanks houstonbofh. I used VNC on Windows with Ubuntu's Remote Desktop while I was getting everything setup. SSH is fine going forward. Thanks for the firewall info and the link to the packages index. Still wondering about FTP. From above... 

FTP - I setup vsftpd with local login, but I'd like to specify a list of allowed users rather than anonymous or local. Is there a way to do this? Also, is it possible to allow uploads but not downloads?[/QUOTE]

If you have ssh running, just use sftp (or WinSCP on a Windows client) to transfer files instead of ftp.  It's much more secure.

With regard to something equivalent to ZoneAlarm, you might want to try snort.  It's an intrusion detection system that will pick up on any attacks against your system across the network.

---

