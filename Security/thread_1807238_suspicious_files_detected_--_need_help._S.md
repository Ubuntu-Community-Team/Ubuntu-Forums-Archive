---
title: "suspicious files detected -- need help. :S"
date: 2011-07-18
forum: Security
---

### Post by TuLesto on 2011-07-18
Greetings all, recently LastPass was hacked. I only found out yesterday which kind of pulled me into a password changing frenzy. I also checked for key-loggers with chkrootkit and rkhunter (am I using the right tools?) -- I did get this feedback from chkrootkit: > The following suspicious files and directories were found:  
/usr/lib/firefox-3.6.18/.autoreg /usr/lib/jvm/.java-6-openjdk.jinfo /usr/lib/pymodules/python2.6/.path /usr/lib/xulrunner-1.9.2.18/.autoregCould someone help me out with this? I have no idea what I am looking at. I'll be doing some of my own research after supper.

UPDATE 1
Done supper :) googling now. 
UPDATE 2
No information about this on google. I'm wondering if it is suspicious at all...

---

### Post by cipherboy_loc on 2011-07-18
Surprised that I am the first, but rkhunter and chkrootkit are known for giving false positives. If it isn't documented on google as being part of an exploit, I wouldn't worry too much about it. If you really want to, check the type of file with the file command:

```

file  /usr/lib/firefox-3.6.18/.autoreg /usr/lib/jvm/.java-6-openjdk.jinfo  /usr/lib/pymodules/python2.6/.path /usr/lib/xulrunner-1.9.2.18/.autoreg                      

```Unless it is an executable file of some sort (like an ELF) or a script (check the permissions with `ls -l  /usr/lib/firefox-3.6.18/.autoreg /usr/lib/jvm/.java-6-openjdk.jinfo  /usr/lib/pymodules/python2.6/.path /usr/lib/xulrunner-1.9.2.18/.autoreg` minus the quotes), I probably wouldn't worry about it.



Cipherboy

---

### Post by Dangertux on 2011-07-18
I agree with the poster above me IMO it is a false positive.

---

### Post by TuLesto on 2011-07-19
> **cipherboy_loc said:**
> Surprised that I am the first, but rkhunter and chkrootkit are known for giving false positives. If it isn't documented on google as being part of an exploit, I wouldn't worry too much about it. If you really want to, check the type of file with the file command:

```

file  /usr/lib/firefox-3.6.18/.autoreg /usr/lib/jvm/.java-6-openjdk.jinfo  /usr/lib/pymodules/python2.6/.path /usr/lib/xulrunner-1.9.2.18/.autoreg                      

```Unless it is an executable file of some sort (like an ELF) or a script (check the permissions with `ls -l  /usr/lib/firefox-3.6.18/.autoreg /usr/lib/jvm/.java-6-openjdk.jinfo  /usr/lib/pymodules/python2.6/.path /usr/lib/xulrunner-1.9.2.18/.autoreg` minus the quotes), I probably wouldn't worry about it.



Cipherboy


Wow, thanks! I'm glad somebody replied at all. It didn't seem like this thread was getting much attention. I appreciate your help very much and am glad that someone can back it up. Thanks again. :)

---

### Post by bodhi.zazen on 2011-07-19
Root kits and the tools to detect them are sophisticated and only you can determine what is "normal" for your system.

You need to know what these tools show you in a Known good installation.

You need to know what packages you have installed. For example I do not have those files on my system at all, nor would I expect them based on the packages I have installed.

See [https://wiki.ubuntu.com/rkhunter](https://wiki.ubuntu.com/rkhunter) and when you find warnings, use google to confirm or deny that they are a problem or a false alarm.

If you are not going to do the foot work, do not bother to run the tools.

All security tools, from snort to rkhunter, have rule sets to bring files or behavior to your attention for investigation.

For example, if you use a packet sniffer, you can capture all your network packets. How then would you know which ones are a problem ? Enter snort, snort filters through the thousands of packets and "alerts" you to those you should investigate.

root kit detection is the same, only it applies to the files on your hard drive rather then network packets.

---

