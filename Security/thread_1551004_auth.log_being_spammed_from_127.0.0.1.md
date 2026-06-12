---
title: "auth.log being spammed from 127.0.0.1"
date: 2010-08-11
forum: Security
---

### Post by msandoy on 2010-08-11
I'm running a 10.04 headless server, with SSH, FTP and SQUID. I have Denyhosts installed, and it seems to be working quite well. My question is, the past few days, I have had quite alot of messages like: Aug 11 22:23:53 asuseee sshd[10724]: refused connect from 127.0.0.1 (127.0.0.1).
This is due to the fact that Denyhosts has banned the address. 
There is also alot of did not receive identification string from 127.0.0.1 and some Bad protocol version identification from 127.0.0.1.
Is this a bot trying to spoof it's way in via a fake loopback address?
There is no indication that the server has been compromised.

---

### Post by wacky_sung on 2010-08-12
It can be a possible of DDOS / dictionary attack on your system running SSH / FTP.Those are the potential attacks in which people trying to crack the password.

---

### Post by msandoy on 2010-08-12
Well, this is the output of grep for 127.0.0.1 in auth.log:
```

@asuseee:~$ grep 127.0.0.1 /var/log/auth.log
Aug  9 12:55:07 asuseee sshd[6898]: Did not receive identification string from 127.0.0.1
Aug  9 12:55:07 asuseee sshd[6900]: Bad protocol version identification 'O3\030\213\244\266\313\270w\215\035\2037\344n`C\265\303\312<\253\224U"\325B\220_\023\2737I\231\216\330D\247\222\227\267.\256@\277\024\340\267\267\035\364A\214\264\347\243\016~\271\a\351\261s\312\023\262\320I\230\375;\373\216Qi SN\252\322\244Wg\275\232\036JK\a:JV\372K\177\321\366\354>\202' from 127.0.0.1
Aug  9 14:25:45 asuseee sshd[6909]: Did not receive identification string from 127.0.0.1
Aug  9 14:25:45 asuseee sshd[6910]: Bad protocol version identification '\001c\222!+?\250\236|F\357\222\311\273\033\036`<g\371\355\200K\354m_R4\203\253:\203-\312\301\355b\206\353e>r\361:\360\251[P\026E_\362\331a\216\234t\256\320\215\026=\276\254\315\231&\362x\260\262\aI\335\216\243\373\177-[\003\264\357' from 127.0.0.1
Aug  9 15:57:36 asuseee sshd[6916]: Did not receive identification string from 127.0.0.1
Aug  9 15:57:36 asuseee sshd[6918]: Bad protocol version identification 'e\272\223/WY\341\343<_%C\240$' from 127.0.0.1
Aug  9 18:59:47 asuseee sshd[6931]: Did not receive identification string from 127.0.0.1
Aug  9 18:59:47 asuseee sshd[6932]: Bad protocol version identification '5\003\240\307\bT3\355\352\265=D\034\300\255\226OL\2779|~\212\f\343\232\244)\004\361m\300|\217I#\215\254\254w\367\341\363\217-\317c\235#\244\\\bA\032\333D\347\365=\351\276G\024"\275\267\a\003\373,t\243\367\205$\033H\001\354\347\345\036\366F7\376Q\374\210\340\256\264\276V\336m\234\3157{' from 127.0.0.1
Aug  9 19:32:18 asuseee sshd[6938]: Did not receive identification string from 127.0.0.1
Aug  9 19:32:18 asuseee sshd[6939]: Bad protocol version identification 'n\307v\315\204\037\326\263lYCO\225C"\242n\272\252m\004\205\031:\177\216,c\352\353\343\241\375\225\346\032\301\352M\251\002R\264\373\346!w\257\314\020\307,S\345\200\255$\244\35793-\2248\353\300\265\255\200v\304\\0X~\036%D\245\246\251\200\241\234\031\304\340\332>\205\005\232p\236I\205\375\245S\360' from 127.0.0.1
Aug  9 21:35:13 asuseee sshd[7378]: Did not receive identification string from 127.0.0.1
Aug  9 21:35:13 asuseee sshd[7380]: Bad protocol version identification ']\270OQ\314`\205 \360\005\222\225\202?\256\216k\337\235\216|\244\006\2218\321\016M>\324\202r!\360\353\366R*(e\222^\304c\005d'R]\016\330\352\361\3000\327\210\266\221?i\351' from 127.0.0.1
Aug  9 23:05:43 asuseee sshd[7385]: refused connect from 127.0.0.1 (127.0.0.1)
Aug  9 23:05:48 asuseee sshd[7387]: refused connect from 127.0.0.1 (127.0.0.1)
Aug 10 00:03:07 asuseee sshd[7392]: refused connect from 127.0.0.1 (127.0.0.1)
Aug 10 00:03:12 asuseee sshd[7394]: refused connect from 127.0.0.1 (127.0.0.1)
Aug 10 07:06:36 asuseee sshd[17994]: refused connect from 127.0.0.1 (127.0.0.1)
Aug 10 07:06:41 asuseee sshd[17996]: refused connect from 127.0.0.1 (127.0.0.1)
Aug 10 08:30:53 asuseee sshd[18005]: refused connect from 127.0.0.1 (127.0.0.1)
Aug 10 08:30:58 asuseee sshd[18007]: refused connect from 127.0.0.1 (127.0.0.1)
Aug 10 09:54:41 asuseee sshd[18012]: refused connect from 127.0.0.1 (127.0.0.1)
Aug 10 09:54:46 asuseee sshd[18014]: refused connect from 127.0.0.1 (127.0.0.1)
Aug 10 12:44:11 asuseee sshd[18027]: refused connect from 127.0.0.1 (127.0.0.1)
Aug 10 12:44:16 asuseee sshd[18029]: refused connect from 127.0.0.1 (127.0.0.1)
Aug 10 19:49:28 asuseee sshd[18083]: refused connect from 127.0.0.1 (127.0.0.1)
Aug 10 19:49:33 asuseee sshd[18085]: refused connect from 127.0.0.1 (127.0.0.1)
Aug 10 21:13:57 asuseee sshd[18102]: refused connect from 127.0.0.1 (127.0.0.1)
Aug 10 21:14:02 asuseee sshd[18104]: refused connect from 127.0.0.1 (127.0.0.1)
Aug 10 21:41:42 asuseee sshd[18109]: refused connect from 127.0.0.1 (127.0.0.1)
Aug 10 21:41:47 asuseee sshd[18111]: refused connect from 127.0.0.1 (127.0.0.1)
Aug 10 22:10:06 asuseee sshd[18112]: refused connect from 127.0.0.1 (127.0.0.1)
Aug 10 22:10:11 asuseee sshd[18114]: refused connect from 127.0.0.1 (127.0.0.1)
Aug 10 22:38:32 asuseee sshd[18119]: refused connect from 127.0.0.1 (127.0.0.1)
Aug 10 22:38:37 asuseee sshd[18121]: refused connect from 127.0.0.1 (127.0.0.1)
Aug 10 23:06:52 asuseee sshd[18122]: refused connect from 127.0.0.1 (127.0.0.1)
Aug 10 23:06:57 asuseee sshd[18124]: refused connect from 127.0.0.1 (127.0.0.1)
Aug 10 23:33:57 asuseee sshd[18129]: refused connect from 127.0.0.1 (127.0.0.1)
Aug 10 23:34:02 asuseee sshd[18131]: refused connect from 127.0.0.1 (127.0.0.1)
Aug 11 00:02:26 asuseee sshd[18132]: refused connect from 127.0.0.1 (127.0.0.1)
Aug 11 00:02:31 asuseee sshd[18134]: refused connect from 127.0.0.1 (127.0.0.1)
Aug 11 01:24:34 asuseee sshd[18585]: refused connect from 127.0.0.1 (127.0.0.1)
Aug 11 01:24:39 asuseee sshd[18586]: refused connect from 127.0.0.1 (127.0.0.1)
Aug 11 09:40:48 asuseee sshd[10207]: refused connect from 127.0.0.1 (127.0.0.1)
Aug 11 09:40:53 asuseee sshd[10209]: refused connect from 127.0.0.1 (127.0.0.1)
Aug 11 10:37:48 asuseee sshd[10214]: refused connect from 127.0.0.1 (127.0.0.1)
Aug 11 10:37:53 asuseee sshd[10216]: refused connect from 127.0.0.1 (127.0.0.1)
Aug 11 11:34:40 asuseee sshd[10221]: refused connect from 127.0.0.1 (127.0.0.1)
Aug 11 11:34:45 asuseee sshd[10223]: refused connect from 127.0.0.1 (127.0.0.1)
Aug 11 13:52:55 asuseee sshd[10232]: refused connect from 127.0.0.1 (127.0.0.1)
Aug 11 13:53:00 asuseee sshd[10234]: refused connect from 127.0.0.1 (127.0.0.1)
Aug 11 15:45:21 asuseee sshd[10243]: refused connect from 127.0.0.1 (127.0.0.1)
Aug 11 15:45:26 asuseee sshd[10245]: refused connect from 127.0.0.1 (127.0.0.1)
Aug 11 17:09:13 asuseee sshd[10250]: refused connect from 127.0.0.1 (127.0.0.1)
Aug 11 17:09:18 asuseee sshd[10252]: refused connect from 127.0.0.1 (127.0.0.1)
Aug 11 19:04:46 asuseee sshd[10261]: refused connect from 127.0.0.1 (127.0.0.1)
Aug 11 19:04:51 asuseee sshd[10263]: refused connect from 127.0.0.1 (127.0.0.1)
Aug 11 22:23:51 asuseee sshd[10722]: refused connect from 127.0.0.1 (127.0.0.1)
Aug 11 22:23:56 asuseee sshd[10724]: refused connect from 127.0.0.1 (127.0.0.1)
Aug 12 01:09:05 asuseee sshd[10849]: refused connect from 127.0.0.1 (127.0.0.1)
Aug 12 01:09:10 asuseee sshd[10851]: refused connect from 127.0.0.1 (127.0.0.1)
Aug 12 02:31:18 asuseee sshd[10875]: refused connect from 127.0.0.1 (127.0.0.1)
Aug 12 02:31:23 asuseee sshd[10877]: refused connect from 127.0.0.1 (127.0.0.1)
Aug 12 07:34:58 asuseee sshd[21481]: refused connect from 127.0.0.1 (127.0.0.1)
Aug 12 07:35:03 asuseee sshd[21483]: refused connect from 127.0.0.1 (127.0.0.1)
Aug 12 09:55:10 asuseee sshd[21505]: refused connect from 127.0.0.1 (127.0.0.1)
Aug 12 09:55:15 asuseee sshd[21507]: refused connect from 127.0.0.1 (127.0.0.1)

```
This is alot of activity, even after the address was blocked by Denyhosts. Normally the attacks stop from outside addresses after blocking. There is no successful operations from this address anywhere in auth.log. What does these messages about bad protocol version identification mean?

---

### Post by wacky_sung on 2010-08-12
How about looking into [this]("http://serverfault.com/questions/25420/strange-sshd-log-message-every-minute")?

---

### Post by msandoy on 2010-08-12
I checked my /var/log/secure file, but there is nothing like this there. It only contains the usual ftp breakin attempts.

---

### Post by wacky_sung on 2010-08-13
Have you look into your firewall rules?Perhap it is coming from there.

---

### Post by msandoy on 2010-08-14
This is a pretty simple out of the box install of 10.04 server. In addition to the basic install, it has Openssh, squid, gadmin-proftpd, rtorrent and Denyhosts. I'm not sure what firewall settings are in place on a basic server install. Nothing has been blocked until now. I have tried using a normal desktop version for this purpose, but those are totally closed by default, and I would have to open each and every port manually. On the server, everything works out of the box. All filtering is done by my router.

---

### Post by wacky_sung on 2010-08-14
It is possible of a DDOS attack since you got everything in default without any firewall.

---

### Post by yashar on 2010-08-14
if this is attack why the time of refuses are not continues and big gaps between times? is there a firewall to prevent login for a period of time after connection refused?

isnt this because of squid?

---

### Post by msandoy on 2010-08-14
I really have to say, this is very strange. The connection attempts have just stopped. No attempt fram 127.0.0.1 in two days now. I have not done anything different. The same programs are still running. I have not installed anything or removed anything. I have only been busy reading log files. I have gone trough the log files for squid, but I cant find any denied connections or any other record that stands out. All seems to be normal. The only thing I have done, is an update as follows:
```

Start-Date: 2010-08-12  17:28:39
Upgrade: gnome-keyring (2.92.92.is.2.30.3-0ubuntu1, 2.92.92.is.2.30.3-0ubuntu1.1), libpam-gnome-keyring (2.92.92.is.2.30.3-0ubuntu1, 2.92.92.is.2.30.3-0ubuntu1.1), libgp11-0 (2.92.92.is.2.30.3-0ubuntu1, 2.92.92.is.2.30.3-0ubuntu1.1), libgcr0 (2.92.92.is.2.30.3-0ubuntu1, 2.92.92.is.2.30.3-0ubuntu1.1), libldap-2.4-2 (2.4.21-0ubuntu5.2, 2.4.21-0ubuntu5.3)
End-Date: 2010-08-12  17:28:55

```
There must have been something in one of those files prior to the update.

---

