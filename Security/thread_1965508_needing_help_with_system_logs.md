---
title: "needing help with system logs"
date: 2012-04-25
forum: Security
---

### Post by donwolfani on 2012-04-25
ok so i was talking to a friend earlier and we both trade tips and tricks we pick up about system administration and security.
so he was telling me that the system by default logs everything i do. every program i run and the like.

is the a way to disable the logging of what programs i run and clear out these logs?  im sure they are useful for beta releases but truth be told i want to save harddrive space as anyone would, as well as the fact that if someone steals my machine or manages to get on it at work or whatever i do not want them going through seeing what i have been doing.  mind you im not hiding things neccesarily but i plainly do not want my system keeping info of how i use it and at what times as there is already talk of cispa killing online privacy so i would atleast like to know how to clear the logs with each reboot in such a way that what i have run program wise stays between me and my system and not in the hands of anyone else who snoops

---

### Post by Ms. Daisy on 2012-04-25
The logs on your system aren't really doing that at all.  I encourage you to open Log Viewer and take a peek. Logs are useful when troubleshooting network and software  problems. You can change the log levels to low or off if you like.   Here's a link to some details about the logs. 

[https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)

But basically here's a snip from a log:
```
Jan 24 15:44:08 MsDaisy-Computer kernel: [ 1296.544822] [UFW BLOCK] IN= OUT=wlan0 SRC=192.168.1.6 DST=69.171.234.32 LEN=60 TOS=0x00 PREC=0x00 TTL=1 ID=1088 PROTO=ICMP TYPE=8 CODE=0 ID=2913 SEQ=1      
Jan 24 15:44:56 MsDaisy-Computer kernel: [ 1344.922839] [UFW BLOCK] IN= OUT=wlan0 SRC=192.168.1.6 DST=69.171.234.32 LEN=60 TOS=0x00 PREC=0x00 TTL=1 ID=1089 PROTO=UDP SPT=47414 DPT=33434 LEN=40    
```You can see from above that it shows my internal LAN IP address and the destination IP address. If you really felt like it you could google the destination IP address and find out I was surfing Facebook.  But it doesn't tell you what I was doing on facebook, who I was messaging, that kind of stuff.

The kind of thing that you're worried about would be a Network Monitoring Tool like wireshark and snort. Those could be configured to log your traffic on the internet and to see the packets sent over TCP/IP, which means someone knowledgeable could see the contents of a message you sent in Facebook.  However, those Network Monitoring Tools do not come in default Ubuntu installations. You would have to install them yourself.

---

### Post by donwolfani on 2012-04-26
thank you so much.  i ahve been going nuts trying to control my privacy of late, to be honest im sure im going overboard but then again thinking in ways like i have been is what ultimately helps me learn the ins and out of network security and being able to control what my machine tells the world yaknow

---

### Post by JKyleOKC on 2012-04-27
Just an additional observation here. If you look at the /var/log directory, you'll see many files with names that end in numbers like .1, .2, and so on. These are archives of previous logs. For instance, I show 138 objects in that folder, some of which are subdirectories that in themselves contain more files.

These archives of previous logs can be quite helpful in troubleshooting, especially in forensic studies if your system gets invaded, to help you locate the means by which it happened. However if you're extremely concerned about the space they occupy, you can delete most of those files. Note that "deleting" actually just moves the files to the "trash" area so it doesn't actually clear the space until you empty the trash bin, though. Also, they are owned by "root" so you'll have to use "sudo" to remove them.

You can also tweak configuration files in /etc/logrotate.d to change the intervals at which the log files are rotated and cleaned up. I've never bothered to do so; the defaults are fine for my needs.

---

