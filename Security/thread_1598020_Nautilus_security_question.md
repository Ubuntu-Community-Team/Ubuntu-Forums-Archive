---
title: "Nautilus security question"
date: 2010-10-16
forum: Security
---

### Post by drkem99 on 2010-10-16
I am new to Linux and Ubuntu (currently running 10.10 on a Dell Mini 9); I have a question relating to nautilus and possible use of nautilus scripts by someone trying to access files on my netbook. I installed a software package from a recommended non-official source I thought could be trusted; the software itself is quite functional and seems professionally done. However, while it is open and I then look at File Manager I see a string of actions in the history at the bottom of the File menu - primarily "Compress" and "Send to" with a couple of others mixed in. These do not relate to anything I am doing with the software or that I am doing while it is running, and the string of actions increases over time while the software is open but not at other times. The software is primarily a word processor and project organiser and it does do compressed auto backups, but it seems to me that "Send to" implies that nautilus is sending files compressed on my netbook by email to someone else. I am afraid the software has a hidden script for nautilus and is using it to copy files off my netbook. Is there any legitimate reason I would be seeing all of these actions in the Edit history? Any thoughts?

---

### Post by HermanAB on 2010-10-16
Howdy,

It is most probably nothing.

However, it is very easy to look at the network connection and see what is being exchanged with the rest of the world.  Either install wireshark or tcpdump.  Wireshark has a GUI - have fun with that, or use tcpdump:
$ sudo tcpdump -s256 -A -i eth0

Then do something in your suspect program and see what it does.

---

### Post by drkem99 on 2010-10-16
> **HermanAB said:**
> Howdy,

It is most probably nothing.

However, it is very easy to look at the network connection and see what is being exchanged with the rest of the world.  Either install wireshark or tcpdump.  Wireshark has a GUI - have fun with that, or use tcpdump:
$ sudo tcpdump -s256 -A -i eth0

Then do something in your suspect program and see what it does.

Will do; thanks for the suggestion!

---

### Post by drkem99 on 2010-10-16
Wireshark showed no anomalous external traffic during operation of the suspect program but did show a lot of localhost packet traffic (127.0.0.1). The program in question operates under mono (.NET framework) and I suspect the localhost traffic might be related to program operation under mono and to the 'Send to' history items in nautilus that concerned me in the first place. Wish I was smarter...

At any rate, I am reassured that I can use the software safely. Thanks again; great tip!

---

