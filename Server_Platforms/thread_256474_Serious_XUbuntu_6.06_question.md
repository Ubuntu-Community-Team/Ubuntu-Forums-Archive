---
title: "Serious XUbuntu 6.06 question"
date: 2006-09-13
forum: Server Platforms
---

### Post by orthopteroid on 2006-09-13
First of all, I'm loving your distro! I recently installed XUbuntu 6.06 from cd. After installing the likes of chkrootkit, rkhunter, firestarter and other tools I noticed some strange things:

- rkhunter reported a 'ps' hidden LKM trojan
- rkhunter reported suspicious hidden folder /dev/.static (among others)
- firestarter reported outgoing connections on random ports (ports change between reboots)
- 'netstat -l' reported listening sockets on random ports (ports change between reboots)

Additionally it seems that some process is not configured right: '/dev/.static/dev/core' is being rewritten every second.

I thought: "Ick - I installed something bad!", so I rebooted with just the cd. And although I don't have those other tools I liked so much I discover the cd version shows the hidden folder in the /dev/ tree as well as similar 'netstat -l' output:

ubuntu@ubuntu:~$ netstat -l
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 localhost:43811         *:*                     LISTEN
tcp        0      0 localhost:34732         *:*                     LISTEN
tcp        0      0 localhost:ipp           *:*                     LISTEN
udp        0      0 *:bootpc                *:*
Active UNIX domain sockets (only servers)
Proto RefCnt Flags       Type       State         I-Node Path
unix  2      [ ACC ]     STREAM     LISTENING     15477    @/tmp/hald-local/dbus-RYsFNn7xCq
unix  2      [ ACC ]     STREAM     LISTENING     15920    @/tmp/dbus-AYW3u6nzEh
unix  2      [ ACC ]     STREAM     LISTENING     15895    /tmp/ssh-SvRyvi5857/agent.5857
unix  2      [ ACC ]     STREAM     LISTENING     17082    @/tmp/fam-ubuntu-
unix  2      [ ACC ]     STREAM     LISTENING     15416    /var/run/dbus/system_bus_socket
unix  2      [ ACC ]     STREAM     LISTENING     18006    /tmp/orbit-ubuntu/linc-18d8-0-57fc0ee079c84
unix  2      [ ACC ]     STREAM     LISTENING     14707    /tmp/.gdm_socket
unix  2      [ ACC ]     STREAM     LISTENING     15478    @/tmp/hald-runner/dbus-7HYtXL0tlF
unix  2      [ ACC ]     STREAM     LISTENING     14815    /tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     15336    /var/run/cups/cups.sock
unix  2      [ ACC ]     STREAM     LISTENING     13802    /var/run/acpid.socket
unix  2      [ ACC ]     STREAM     LISTENING     18155    /tmp/orbit-ubuntu/linc-18d2-0-32ea4cebf3bf8
unix  2      [ ACC ]     STREAM     LISTENING     16114    /tmp/.ICE-unix/5999

So are servers listening on random sockets and hidden folders in /dev containing coredumps normal for XUbuntu or is there an, ahem, problem with the 6.06 iso?

Can someone place my mind at ease?

Regards

---

### Post by orthopteroid on 2006-09-13
Oh ya, I also did a nessus check and found an http server in the high port range...

---

### Post by orthopteroid on 2006-09-13
From doing extra digging, I notice that the open sockets might be something to do with 'hpiod'? To show the pid's and their open sockets I used the command:

# lsof | head -n 1; lsof | grep "TCP\\|UDP"
COMMAND    PID       USER   FD      TYPE     DEVICE    SIZE       NODE NAME
hpiod     4337      hplip    0u     IPv4      10605                TCP localhost:50042 (LISTEN)
<snip>

Looks on the up and up, but 'telnet localhost 50042' shows the mysterious 'msg=MessageError result-code=5' message that I've not yet seen an explanation for. More worrying is that earlier tonight I disabled firestarter and saw this port (or perhaps it was another) accept a connection from a machine in the aol domain...

Also, the core file appears to link to /prok/kcore which I've seen someone explain as being 'just memory' that shows up as changed when you access it. Well, might be the case, but why have it located within a bunch of hidden folders inside /dev. If beneign, then someone here hopefully can explain that.

Is anyone else here using XUbuntu 6.06 seen the stuff I'm explaining here, or am I off wandering in a forest by myself?

---

### Post by orthopteroid on 2006-09-14
For the inquisitive, here is a link with some very good insight on which tools to use and when to use them to track down a possible intrusion:

[http://www.linuxquestions.org/questions/showthread.php?p=2085521](http://www.linuxquestions.org/questions/showthread.php?p=2085521)

Perhaps I don't have an intrusion now, but know I have in the past (ie someone else's commands in my .bash_history!) and expect to have to reinstall the os again in the future (which is the only way to deal with a LKM rootkit, I understand). To make this easier I now use 2 drives: hda1 and 2 for the os and swap, hdb1 for /home (so I keep all my user prefs and docs).

regards

---

