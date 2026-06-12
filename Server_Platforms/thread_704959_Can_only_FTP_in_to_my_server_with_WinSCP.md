---
title: "Can only FTP in to my server with WinSCP"
date: 2008-02-22
forum: Server Platforms
---

### Post by xyvian on 2008-02-22
Ok, so my problem has been bugging me for a while now (and the people who use my ftp server). I am using Ubuntu Server 7.10 and have, through the help of Webmin, gotten proFTPd installed and configured to my liking. I am limiting bandwidth that people can use. HOWEVER I can only seem to use WinSCP to ftp in to it. I don't want to have to use WinSCP because the UI is a bit complex for the people I have set up and it doesn't seem to have resume support. Havn't much looked into that aspect, but have been getting complaints.

 When I use other clients (i have used filezilla and smartftp) it will connect to the server and, however it will get stuck at the line that says "Command: PASV" and will either sit there indefinitely or time out.

I have tried googling this problem and even perused these forums but it seems like nobody has this issue. I can post my config file if needed but I am in a bit of a rush right now otherwise I would.

Any help would be very appreciated.

---

### Post by faulkes on 2008-02-22
Please see this thread:

[http://ubuntuforums.org/showthread.php?t=692355](http://ubuntuforums.org/showthread.php?t=692355)

I believe this particularly addresses the problem you are encountering.

Faulkes

---

### Post by HermanAB on 2008-02-23
Do you have a firewall enabled?  Did you enable FTP with connection tracking?

---

### Post by smileypaul on 2008-02-25
I have the exact same problem with all of my proftp servers .. oh anger rising!!

I have tried everything, including forwarding all of the necessary ports etc for passive mode.

I found the only thing that worked for me was to have all of my cleints use FileZilla FTP.. its free, its easy to use, and its reliable.. but im still VERY upset that my other clients just hang at the PASV command.. 

I have a company that is looking for FTP hosting, my first that would absolutley *REQUIRE* that all ftp-clients connect, and i may have to refuse their business.. or switch to VSftp and see if that helps..

ugg.. please keep me updated on this if you find a better solution.

---

### Post by Mr. C. on 2008-02-25
Run a packet sniffer (eg.tcpdump) listening on the appropriate Ethernet interface on the FTP server.  Capture all packets to or from the connecting host.  Examine the packet capture (eg. wireshark) and look for the client sending the PASV command and the server's reply to that command.

PASV output is not standardized; the client must handle what is output by the server.  Only a packet sniffer will give you definitive answers about what data is crossing the wire.

mrC

---

### Post by xyvian on 2008-02-26
wow, so many responses already! sorry, I have been away since I last posted but I will definitely get on top of the suggestions.

I will hopefully be able to work on it tonight and give a response as per my results.

Xyvian

---

