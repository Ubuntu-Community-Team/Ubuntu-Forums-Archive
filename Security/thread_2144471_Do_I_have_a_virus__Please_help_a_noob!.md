---
title: "Do I have a virus ? Please help a noob!"
date: 2013-05-12
forum: Security
---

### Post by suckerpunch5 on 2013-05-12
I first noticed a problem when I tried to go to ebay. I got a message "Firefox cant establish a connection to the server at feedhome.vip:8080" So as I read around I learned this sort of behavior can be a virus . So I tried to install clamav "$sudo apt-get install clamav clamtk" response "Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)"  "Unable to unlock the administration directory (/var/lib/dpkg/), are you root?"  So then I tried the ubuntu software center. I found clamav, clicked install, entered my password, and then got the message "failure to download package" Or something like that. So, now what?  I typed this on my ps3, btw.  sucked

---

### Post by matt_symes on 2013-05-12
Thread moved to **Security Discussions**.

---

### Post by suckerpunch5 on 2013-05-12
So, to continue updating, I opened the terminal in safe mode.  From there I was able to install clamav.  Then I went back into the computer and updated the virus definition files with freshclam.  I scanned every file on the computer.  $ sudo clamscan -r --bell -i /  At the end, it said it detected no viruses, but quite a few errors.  Here is the output.

----------- SCAN SUMMARY -----------
Known viruses: 2287386
Engine version: 0.97.8
Scanned directories: 39095
Scanned files: 170079
Infected files: 0
Total errors: 13628
Data scanned: 13488.74 MB
Data read: 60204.58 MB (ratio 0.22:1)
Time: 4661.738 sec (77 m 41 s)

Is it possible to give me the symptoms previously mentioned, and have no viruses?  In other words, is clamav any good?  Can I trust it?  Could a virus somehow fool it?  If so, how would I know?  Again, any help would be great.

---

### Post by hansdown on 2013-05-12
Welcome to the forum, suckerpunch5.

The server was likely down at the time you tried to connect.

The reason you got the install error, is because clamav, and clamtk are two seperate programs.

```
 "$sudo apt-get install clamav clamtk"
```

Clamav searches for windows malware, so if it says 0 viruses found, that is good.

---

### Post by suckerpunch5 on 2013-05-13
Following up once more, I think I resolved my Firefox problem.  I went back and cleared all my cookies, basically everything I could delete about history, and now it connects to ebay fine.

---

### Post by Starfleet on 2013-05-14
Yes, it's unlikely you had an infection. In 8 years of using Linux Ubuntu, I've yet to come across a virus or malware infection that can infect it. And I go where Windows users fear to tread looking for problem websites and web based infections as part of my job! I run a small network with Linux and have also installed it on too many computers to remember and security in Linux is just sublime compared to what Windows users have to put up with. Once you get used to it, you'll trust it. But be aware there are some scripts that can still affect your browser when on line, although it's still really hard for someone to infect you in that way. So take all the usual security measures that you would take if you were running Windows. 'No-scripts' is a good precaution in firefox. Using that you are really very safe compared to Windows.

---

### Post by Shakey Hands on 2013-09-15
Hi,

I have the same problem. but nothing above worked for my computer. 
Ive tried installing clamav from safe mode but it fails. this message appears

W: not using locking for read only lock file /var/lib.dpkg/lock
E: unable to write to /var/cache/apt/
E:The package lists or status file could not be parsed or opened



what does that mean? Please help.

---

### Post by Shakey Hands on 2013-09-15
im running ubuntu 12.04 64-bit.
i dont think i have any kind of java block, because i didnt realise i needed one. Yes, im a noob.

thanks adam

---

### Post by Shakey Hands on 2013-09-15
I do have dual boot windows and ubuntu. however, i do not have windows connected to the net and have not used it for weeks.

---

### Post by Shakey Hands on 2013-09-15
As far as i can tell, their is no advise on the net that can help me, or i their is i cant/understand it. 
I have the **Ukash malware** bug.

---

### Post by cariboo on 2013-09-15
Try creating a new firefox profile

```
Firefox -no-remote -ProfileManager
```

to see if the browser exploit still exists.

---

