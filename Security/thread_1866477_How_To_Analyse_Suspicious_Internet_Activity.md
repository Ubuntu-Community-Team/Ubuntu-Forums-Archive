---
title: "How To Analyse Suspicious Internet Activity"
date: 2011-10-21
forum: Security
---

### Post by SparTacux on 2011-10-21
.....IN REAL TIME

Hypothetical Situation..

A user has full IP logging and has log viewer opened and  is using Firefox ( or another browser ) on his computer. He then spots a couple of IP Addresses going out that aren't normally there for the web site he visits. He also has some sort of disk monitor program running and it shows quite some unusual activity of reading from his disk. Rather than disconnecting he decides he wants to monitor the activity and only has a small window of opportunity( say a few seconds ) to capture has much as he can.

1....What commands would you run on the terminal to capture as much as you can that may help in deciding if the activity is abnormal?

2....Could you put the commands in a script and have some sort of 'hot switch' to run those commands at the click of a mouse

3...Are there any programs out there you could run as soon as you spot unusual activity.

---

### Post by SparTacux on 2011-10-21
I'm thinking along the lines of looking at open files, processes running, memory dumps, packet capture on port 80, etc. There may be more than this hence the question..

---

### Post by bodhi.zazen on 2011-10-21
tcpdump
snort
wireshark

---

### Post by SparTacux on 2011-10-22
I haven't used wireshark or tcpdump yet  but I suspect there are command line options for starting those programs from the terminal and can be put in some sort of script or batch file that can be run on a click of a mouse in case of an 'emergency'.

I'm just thinking along the lines of a zero day vulnerability and methods used to grab the necessary details to verify if a program is not working the way it should. Obviously capturing the network traffic is one of the areas to look at but what about the program itself - the files it opens, use of memory, etc.

I doubt the guys who spot these vulnerabilities and identify them are going through the source code alone looking for programming mistakes - they must have other tools at their disposal?

---

### Post by The Cog on 2011-10-22
tcpdump is a command-line app that is installed by default. How about
> sudo tcpdump -w tcpdump.cap
to write all the packet data to a file.
You can examine the file later with wireshark to see full packet decodes. Wireshark is a graphical app in the repositories.

---

