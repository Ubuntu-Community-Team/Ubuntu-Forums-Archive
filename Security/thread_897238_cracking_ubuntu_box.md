---
title: "cracking ubuntu box"
date: 2008-08-21
forum: Security
---

### Post by matt79 on 2008-08-21
Ok I was talking to a teacher about servers and the domain names when he asked me what type of server I had. I told him linux (I did not say which branch of linux although for your info I am running ubuntu hardy) He said that he could crack any linux box in 8 seconds. Now he teaches cisco A+ and security and I am sure some other stuff. He also I think does some programing. My question is....is it really that easy to crack linux? if so how, and how to I help prevent my server from being attack? Please use details.:lolflag:

---

### Post by AusIV4 on 2008-08-21
If he has physical access to a system, he could reboot it to single user mode and give himself an administrative user (unless GRUB is locked down properly).

Otherwise, he's probably just spreading FUD to promote Windows. Linux is used in lots of essential applications, and if it were possible to hack into any linux system in 8 seconds, we'd have heard of it by now.

---

### Post by damis648 on 2008-08-21
> **AusIV4 said:**
> If he has physical access to a system, he could reboot it to single user mode and give himself an administrative user (unless GRUB is locked down properly).

Otherwise, he's probably just spreading FUD to promote Windows. Linux is used in lots of essential applications, and if it were possible to hack into any linux system in 8 seconds, we'd have heard of it by now.

+1. It is really not that easy.

---

### Post by aysiu on 2008-08-21
Ask him to crack Google's Linux servers in 8 seconds. That'll give him a lot of street cred.

---

### Post by damis648 on 2008-08-21
> **aysiu said:**
> Ask him to crack Google's Linux servers in 8 seconds. That'll give him a lot of street cred.

+9999999 :lolflag:

---

### Post by SEMW on 2008-08-22
> **matt79 said:**
>  He said that he could crack any linux box in 8 seconds.
Hey, that's nothing; I can crack any linux box in no more than a second or two.

Given a large enough hammer.

(Assuming it's not a reinforced steel box or something, anyway.  Well, you talk about System Hardening...)

---

### Post by Mister.Vash on 2008-08-22
Go back to the teacher and ask for more details on how he would proceed to do this.  And what exactly his definition of cracking a box is - is it gaining access, gaining root access, a denial of service, bringing down apache or another application, etc.

If it's physical access to the box you don't need to worry, as that can be done easily.

If he says he can do it across the network, bring it in and let him try.  Either he can't and you are fine, or he can and you might need to patch.


The vast majority of time, they really don't know what they are talking about in this regards - getting more details from the person is really the best way to start.  And usually if the can't or won't give you additional information, they can't do it.

---

### Post by Dr Small on 2008-08-22
With physical access, it is very possible to crack a box within 8 seconds. Of course, I would encrypt the hard drive, give root a password, remove the Single Mode from GRUB, set a BIOS boot password and then challenge him :)

---

### Post by aysiu on 2008-08-22
I wouldn't really consider booting into recovery mode "cracking."

Of course it's great to clarify exactly what the boaster means, but I think the general understanding of what it means to "crack" a server is based on compromising the system remotely since it is a *server* after all.

---

### Post by matt79 on 2008-08-22
Ok, he said he could do it through the net. I know you can boot into recover mode if you have phyical access to the server. He is a windows fan (He is certified in windows server 2003). I told him to crack my box but he said if he showed me then I would know how to do it:-) However, if you guys are sure google uses a linux server I will ask him how they could if it is so unsecure.:) Right now I run my website of my ubuntu server so he could try if from the school. The only ports that I have open for the outside world (the internet) is port 22 and 80. I have a strong password on the ssh port. So the question can access be gained through the HTTP port?

---

### Post by aysiu on 2008-08-22
> **matt79 said:**
> 
I told him to crack my box but he said if he showed me then I would know how to do it:-) He doesn't have to show you how he does it. Just ask him to change the root password and change the homepage to say "Ha ha, you were cracked in 8 seconds, Linux fanboy" within a minute. If he can do that, believe him.

> However, if you guys are sure google uses a linux server I will ask him how they could if it is so unsecure.:) I've seen many indications they use Linux clusters. I've seen absolutely no indication that they don't.

---

### Post by matt79 on 2008-08-22
I will try Tuesday, that is the next time I see him. I will post what he says. :-)

---

### Post by qstraza on 2008-08-22
haha this is funny :p

to answer your question about port 80, depends what are you running on apache, if php with mysql or sth simular than it is posible, but still not so easy;)

---

### Post by solitaire on 2008-08-22
It's easy to crack a linux box! 

I did it yesterday! 

All it took was me to drop the box out the 2 story window, one cracked linux box.... :):):)

But could i could not boot it once cracked...:(:(:(

---

### Post by qstraza on 2008-08-22
you cant take the word "crack" literary :p
put some h4ck1n spirit in it:p

---

### Post by The Tronyx on 2008-08-22
I am calling FUD on this one (from your teacher).

---

### Post by jakupl on 2008-08-22
He probably just blurted something out. There is certantly no way in h*** he can do it in 8 sec... or even do it. He has no idea of the security.
My guess is that he does not know linux well enough to say anything.

---

### Post by matt79 on 2008-08-22
Well I would have to agree with you all. I do not see how he could, but he creates and teaches security for the school. Could some one give me a little more info on how php could make your server more proned to attack?

---

### Post by The Tronyx on 2008-08-23
> **matt79 said:**
> Well I would have to agree with you all. I do not see how he could, but he creates and teaches security for the school. Could some one give me a little more info on how php could make your server more proned to attack?

Directory traversal attacks.  
[http://www.securityfocus.com/infocus/1864](http://www.securityfocus.com/infocus/1864)
[http://www.acunetix.com/websitesecurity/directory-traversal.htm](http://www.acunetix.com/websitesecurity/directory-traversal.htm)

---

### Post by Chayak on 2008-08-23
Funny how there were no briefings at Blackhat or Defcon for this magic attack.

Blackhat isn't so bad about getting your machines attacked, but Defcon is known for having the most hostile network in the world.  I know a few individuals who set up honeypots to try to catch 0days that the attendees were using.  It was pretty easily summed up to the windows machines getting exploited within minutes of connecting them to the network.  The linux machines survived fairly well.  The Ubuntu server and desktop didn't fall.

I took my laptop with Ubuntu 8.04 to both and I was on the network all the time on each.  I had tripwire and a multitude of other things running and I'm confident it wasn't compromized.  Though that still doesn't mean I didn't reinstall it the moment Defcon was over, better safe than sorry.

---

### Post by damis648 on 2008-08-23
> **jakupl said:**
> he probably just blurted something out. There is certantly no way in h*** he can do it in 8 sec... Or even do it. He has no idea of the security.
My guess is that he does not know linux well enough to say anything.

+1

---

### Post by qstraza on 2008-08-24
well my server was hacked last week. Im not sure how, cuz there wasnt any data in /var/logs. But im pritty sure i was hacked, cuz my system load went up and peercast was installed and running. I was running ubuntu 7.10 with upgrades up to date. And with the following daemons which are open to the out side world, apache2 sshd, x11vnc, proftpd. And on apache2 gallery2 and phpmyadmin, i think i got hacked via apache2...

---

### Post by matt79 on 2008-08-24
> **qstraza said:**
> well my server was hacked last week. Im not sure how, cuz there wasnt any data in /var/logs. But im pritty sure i was hacked, cuz my system load went up and peercast was installed and running. I was running ubuntu 7.10 with upgrades up to date. And with the following daemons which are open to the out side world, apache2 sshd, x11vnc, proftpd. And on apache2 gallery2 and phpmyadmin, i think i got hacked via apache2...

Did you look in /var/log/apache2 ?

---

### Post by qstraza on 2008-08-25
yea, there was no clue at all

---

### Post by matt79 on 2008-08-25
You know what they might have done is make a script that erased all the infomation on what they did. Check the crontab file.

---

### Post by qstraza on 2008-08-25
> **matt79 said:**
> You know what they might have done is make a script that erased all the infomation on what they did. Check the crontab file.

I already reinstalled the ubuntu...
It would be nice how that happened at the first time.. ;)

---

### Post by Oldsoldier2003 on 2008-08-26
> **qstraza said:**
> I already reinstalled the ubuntu...
It would be nice how that happened at the first time.. ;)

Unfortunately without a forensic review you'll never know what happened You'll only be able to make gueses at what really happened. You did the right thing though- when in doubt always take the safe route, wipe it and reinstall.

---

### Post by Dr Small on 2008-08-26
> **Oldsoldier2003 said:**
> Unfortunately without a forensic review you'll never know what happened You'll only be able to make gueses at what really happened. You did the right thing though- when in doubt always take the safe route, wipe it and reinstall.
Or, disconnect the ethernet/wireless and then analyse :)

---

### Post by qstraza on 2008-08-26
> **Oldsoldier2003 said:**
> Unfortunately without a forensic review you'll never know what happened You'll only be able to make gueses at what really happened. You did the right thing though- when in doubt always take the safe route, wipe it and reinstall.
well this is what i made since i reinstalled
[http://ubuntuforums.org/showthread.php?t=900686](http://ubuntuforums.org/showthread.php?t=900686)

But cron.daily is executed at ~5am. So if intruder comes it, he can still remove any log he wants. Any ideas? Probably i have to focus on "preventing to come in" issue :p

---

### Post by Oldsoldier2003 on 2008-08-26
> **Dr Small said:**
> Or, disconnect the ethernet/wireless and then analyse :)

Very True. I'm a bit more paranoid though :) My thoughts on how to handle the situation probably aren't very practical for the average user, I was taught to handle a compromise this way:

1. isolate the breached system from the network
2. remove the suspect hard drives
3. install a new HDD and reinstall the OS w/patches
4. give the suspect HDD to IT Forensics where they'll clone it and do their investigation on the cloned drive.

In absence of forensics support (self support or commercial/IT dept whatever) the safest thing to do is wipe and reinstall IMHO. Most folks just don't have the skill or time to do a forensic examination and I would never feel comfortable about recommissioning a system that has been breached unless the OS was completely wiped and reinstalled.

---

### Post by koenn on 2008-08-26
> **qstraza said:**
> well my server was hacked last week. Im not sure how, cuz there wasnt any data in /var/logs. But im pritty sure i was hacked, cuz my system load went up and peercast was installed and running. I was running ubuntu 7.10 with upgrades up to date. And with the following daemons which are open to the out side world, apache2 sshd, x11vnc, proftpd. And on apache2 gallery2 and phpmyadmin, i think i got hacked via apache2...

I read about vnc being easily cracked, so it's not really a good idea running it exposed to the internet. In fact, it's not a good idea exposing any admin tool to the internet. Services such as ftp and http, OK (if they're set up right), cause that's what servers are for to begin with, but it's not smart to enable remote administration (vnc, remote desktops, phpmyadmin) from the internet - better tunnel that through something secure (ssh with public key authentication, vpn, ...)

---

### Post by qstraza on 2008-08-26
I have to read vnc over ssh thing. Any links? ;)

---

### Post by koenn on 2008-08-26
> **qstraza said:**
> I have to read vnc over ssh thing. Any links? ;)

introduction to tunnels & vpn - should help you understand the concept
[http://users.telenet.be/mydotcom/howto/linux/tunnel.htm](http://users.telenet.be/mydotcom/howto/linux/tunnel.htm)

vnc through ssh tunnel: howtos, instructions, examples
[http://www.google.com/search?q=ssh+tunnel+vnc](http://www.google.com/search?q=ssh+tunnel+vnc)

---

### Post by jerome1232 on 2008-08-26
So I'm curious did the professor ever take the OP up on cracking his Ubuntu box.

---

### Post by Dr Small on 2008-08-26
> **jerome1232 said:**
> So I'm curious did the professor ever take the OP up on cracking his Ubuntu box.
Probably not, because he can't show off his 'eliteness' in front of a 'n00b'...

---

### Post by qstraza on 2008-08-27
> **koenn said:**
> introduction to tunnels & vpn - should help you understand the concept
[http://users.telenet.be/mydotcom/howto/linux/tunnel.htm](http://users.telenet.be/mydotcom/howto/linux/tunnel.htm)

vnc through ssh tunnel: howtos, instructions, examples
[http://www.google.com/search?q=ssh+tunnel+vnc](http://www.google.com/search?q=ssh+tunnel+vnc)
thanks.

Yea we went off topic, my bad... ;)

where is "hackzor in 8 seconds"? :p

---

### Post by Oldsoldier2003 on 2008-08-27
> **qstraza said:**
> 
where is "hackzor in 8 seconds"? :p

probably writing a custom timer program where displayed seconds = realtime hours (or days, or months lol!)

---

### Post by qstraza on 2008-08-28
i think im starting to believe that 8 second hacking thing.
```
6658 ? S 0:00 ping -q -c 3 88.229.26.145
6664 ? S 0:00 ping -q -c 3 99.252.199.36
6675 ? S 0:00 ping -q -c 3 81.103.102.134
6678 ? S 0:00 ping -q -c 3 58.96.66.60
6695 ? S 0:00 ping -q -c 3 83.252.105.173
6712 ? S 0:00 ping -q -c 3 200.77.223.50
6715 ? S 0:00 ping -q -c 3 98.199.237.7
6718 ? S 0:00 ping -q -c 3 124.197.62.40
6722 ? S 0:00 ping -q -c 3 84.113.230.238
```

this is what i found while typing ps x.

I blocked the port of vnc.
Only running daemons were apache2 (gallery2, phpmyadmin) sshd and proftpd.

I rebooted the box, but it doesnt show on net, so i cant ssh in and im not near it, so... f*ckin lame.

---

### Post by qstraza on 2008-08-28
box came online (maybe fsck runned during boot time)


Any volunteers who are willing to help me? By this i mean ssh-ing in.

This is my output of ps x.
```
q@lj:~$ ps x
  PID TTY      STAT   TIME COMMAND
 5728 ?        Ss     0:00 /bin/sh /usr/bin/x-session-manager
 !5926 ?        Ss     0:00 /usr/bin/ssh-agent /usr/bin/gpg-agent --daemon --sh --write-env-file=/home/q/.gnupg/gpg-agent-info-Litus x-session-man
 !5927 ?        Ss     0:00 /usr/bin/gpg-agent --daemon --sh --write-env-file=/home/q/.gnupg/gpg-agent-info-Litus x-session-manager
 5971 ?        S      0:00 dcopserver [kdeinit] --nosid
 6042 ?        S      0:00 kded [kdeinit] --new-startup
 6128 ?        S      0:00 kwrapper ksmserver
 6130 ?        S      0:00 ksmserver [kdeinit]
 6131 ?        S      0:00 kwin [kdeinit]
 6134 ?        S      0:01 kdesktop [kdeinit]
 6136 ?        S      0:00 kicker [kdeinit]
 6137 ?        S      0:00 kio_file [kdeinit] file /tmp/ksocket-q/klaunchergEmxEa.sla
 6138 ?        S      0:00 kio_media [kdeinit] media /tmp/ksocket-q/klaunchergEmxEa.s
 6140 ?        S      0:00 kio_uiserver [kdeinit]
 6141 ?        S      0:00 kio_trash [kdeinit] trash /tmp/ksocket-q/klaunchergEmxEa.s
 6167 ?        S      0:00 kaccess [kdeinit]
 6190 ?        S      0:00 kmix [kdeinit] -session 10d8cecf96000111065458100000063760
 6191 ?        S      0:00 katapult -session 10d9d39668000112680660600000081280032_1169282257_747766
 6192 ?        S      0:00 konqueror [kdeinit] --preload
 6202 ?        S      0:00 aspell -a -S -C -Tutf8 --encoding=utf-8
 6214 ?        S      0:00 knotify [kdeinit]
 6216 ?        SN     0:00 kio_thumbnail [kdeinit] thumbnail /tmp/ksocket-q/klauncher
 6231 ?        S      0:00 konqueror [kdeinit] --preload
 !6452 ?        S      0:00 kdontchangethehostname Litus lj.rojal.si
 !6453 ?        S      0:00 sh -c xauth list
 !6454 ?        S      0:00 xauth list
 6455 ?        S      0:00 kio_file [kdeinit] file /tmp/ksocket-q/klaunchergEmxEa.sla
 6474 ?        S      0:00 sshd: q@pts/1
 6475 pts/1    Ss     0:00 -bash
 6567 pts/1    R+     0:00 ps x

```

Are processes marked with "!" normal? I put the "!" to mark the lines.

---

### Post by foez on 2008-08-29
I dont get it, you running kde on your server ?
What do you use defending your server ?
Ufw ? tcpwrapper ? moblock ? disabled root on ssh ?
And he can probably sniff your conection trough the classrooms network to your networked computer ?
Second he can do some social engineering on you ? Lot's of reasons just to test you how smart you are. He probably is just testing you and wants you to learn. 
But hey, this is just my thought...

---

### Post by qstraza on 2008-08-29
> **foez said:**
> I dont get it, you running kde on your server ?
What do you use defending your server ?
Ufw ? tcpwrapper ? moblock ? disabled root on ssh ?
And he can probably sniff your conection trough the classrooms network to your networked computer ?
Second he can do some social engineering on you ? Lot's of reasons just to test you how smart you are. He probably is just testing you and wants you to learn. 
But hey, this is just my thought...
iptables rules and of course root is disabled. I also run cs server, any known security risks on that? Or maybe any solution?

I run kde, cuz sometimes i need it.

---

### Post by foez on 2008-08-30
The security of every computer stands or falls by the acts of the one running it. For a server I would never use a desktop environment.
Add different security layers to your server like iptables and the tcpwrapper. Run a harden script like bastille, disable root login, and add an intrusion detection like integrit together with tiger. ( both are easy to use). Then if thats done be sure you run nothing as root. For a game server add a user and be sure to run the game daemon as that user. 
Never run uncrypted connections to your network box unless your in a lan where every computer is trusted. (With a few tools you can even sniff ssh and ssl connections and gather passwords). I remembered that the novell network was compromised a few years ago because some of the engineers ran a gameserver ;-)
If you take all this security measures in mind there is no way that the professor can enter your machine. Once again I think that he's bluffing trying to make you study harder ...

---

### Post by qstraza on 2008-08-30
> **foez said:**
> The security of every computer stands or falls by the acts of the one running it. For a server I would never use a desktop environment.
Add different security layers to your server like iptables and the tcpwrapper. Run a harden script like bastille, disable root login, and add an intrusion detection like integrit together with tiger. ( both are easy to use). Then if thats done be sure you run nothing as root. For a game server add a user and be sure to run the game daemon as that user. 
Never run uncrypted connections to your network box unless your in a lan where every computer is trusted. (With a few tools you can even sniff ssh and ssl connections and gather passwords). I remembered that the novell network was compromised a few years ago because some of the engineers ran a gameserver ;-)
If you take all this security measures in mind there is no way that the professor can enter your machine. Once again I think that he's bluffing trying to make you study harder ...
thanks for those apps, i allready installed bastille, looks pritty nice.
Any ideas on how to make apache2 secured?

---

### Post by matt79 on 2008-09-22
> **jerome1232 said:**
> So I'm curious did the professor ever take the OP up on cracking his Ubuntu box.

No he did not. I really have not talked to him much since. He can stick to his windows systems and I will stick to my linux.:guitar:

---

