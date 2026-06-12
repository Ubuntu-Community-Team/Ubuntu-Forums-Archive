---
title: "FTP server testers wanted."
date: 2006-03-11
forum: The Cafe
---

### Post by Swiss on 2006-03-11
I started a free FTP server for upload/download, and want to see if it works.
And if you think its a good idea...

[ftp://5.24.106.15/](ftp://5.24.106.15/)

Username: Streamload
Password: Don't enter one, just enter username!

[COLOR="Red"][B]
Edit: Password: Don't enter one, just enter username![/B][/COLOR]

---

### Post by -Rick- on 2006-03-11
Are you sure that the IP address is correct? Doesn't work here anyway.

---

### Post by Swiss on 2006-03-11
Try [ftp://192.168.0.105](ftp://192.168.0.105)

---

### Post by Swiss on 2006-03-11
Try [ftp://5.24.106.15/](ftp://5.24.106.15/) again, it may be that I was logged in with that account.

If username: Streamload 
isn't working try, Username: Streamload2
There is a Streamload3 as well. :rolleyes:

---

### Post by -Rick- on 2006-03-11
Thats your internal lan IP. Visit something like [http://www.whatismyip.com/](http://www.whatismyip.com/) to know your inet ip.
Also make sure that a router or other firewall isn't blocking and that ports are forwarded.

EDIT: Didn't saw your next reply, still doesn't work

---

### Post by Swiss on 2006-03-11
What did you enter as the password? :)

---

### Post by -Rick- on 2006-03-11
[QUOTE=Swiss]What did you enter as the password? :)[/QUOTE]
Nothing, since I can't connect. Also ping'ing to that ip doesn't give a reply.

---

### Post by WildTangent on 2006-03-11
[http://www.dyndns.com](http://www.dyndns.com)

sign up for an account, and make a dynamic ip address forward

-Wild

---

### Post by Swiss on 2006-03-11
Can you ping 71.124.105.22-?

Ok, WT.

---

### Post by -Rick- on 2006-03-11
[QUOTE=Swiss]Can you ping 71.124.105.22-?
[/QUOTE]
Yup :)

---

### Post by majikstreet on 2006-03-11
doesn't connect for me either.. (maybe i was just impatient..)

---

### Post by Swiss on 2006-03-11
I'll work on it! And see if I can get it working. :rolleyes: 

Does an FTP server sound useful to you guys anyway? (up to 10GB storage;) )

---

### Post by -Rick- on 2006-03-11
[QUOTE=Swiss]Does an FTP server sound useful to you guys anyway? (up to 10GB storage;) )[/QUOTE]
Sure, some space to share/backup stuff never hurts ;)

---

### Post by bjweeks on 2006-03-11
Open ftp's are a script kiddies dream.

---

### Post by Swiss on 2006-03-11
Okay I've got it figured. You will have to have Hamachi, I can't get it to work through a firewall any other way. :(  

[http://www.hamachi.cc/](http://www.hamachi.cc/)


In case you decide to join the network:

Network Name: Streamload FTP
Password: Stream

Then, to get on the FTP server: [ftp://5.20.207.125](ftp://5.20.207.125)

It works. I tested it between some of my computers.

Hamachi HOWTO: [http://ubuntuforums.org/showthread.php?t=106539](http://ubuntuforums.org/showthread.php?t=106539)

---

### Post by -Rick- on 2006-03-11
> 
Hamachi is currently available for Windows 2000/XP and Linux operating systems. Mac OS/X version is in works.

Ugh I don't use either of them. Well good luck...

---

### Post by Swiss on 2006-03-11
What do you use? :-k  ;)

---

### Post by -Rick- on 2006-03-11
[QUOTE=Swiss]What do you use? :-k  ;)[/QUOTE]
I switch between NetBSD and FreeBSD.

---

### Post by majikstreet on 2006-03-11
uhh how do I join your hamachi network?

edit: if you'd rather me jabber you, Swiss, i can do that

---

### Post by Swiss on 2006-03-11
Do you have it installed? Linux or Windows?

---

### Post by majikstreet on 2006-03-11
linux.. i have hamachi installed.

---

### Post by Swiss on 2006-03-11
Look in readme.... 

I am in windows at the moment....

You can PM (me) for more help. I have to go eat dinner. :)

---

### Post by majikstreet on 2006-03-11
I understand the README, but I mean like do I need an ip address?
```

majikstreet@oreo:~$ sudo hamachi -c /etc/hamachi join Streamload FTP
Joining Streamload .. failed, network not found
majikstreet@oreo:~$

```

---

### Post by Swiss on 2006-03-11
Are you on now? You are accessing my files! ;)

---

### Post by majikstreet on 2006-03-11
uhhh no I'm not

---

### Post by Swiss on 2006-03-11
Must've been someone else. Sorry! :(  Have you got it working?

---

### Post by Swiss on 2006-03-11
Try this Network: FTPSR
Password: FTPSR


If that doesn't work, try making your own network and I'll try to join it...

Try this for a GUI:

[http://forums.hamachi.cc/viewtopic.php?t=2488](http://forums.hamachi.cc/viewtopic.php?t=2488)

---

### Post by majikstreet on 2006-03-11
I'm connected to the network (yay) but I can't connect to the FTP.. hmm... but if I do sudo hamachi list I can see 5.24.106.15, but I can't ping it.

---

### Post by Swiss on 2006-03-12
>  	I'm connected to the network (yay) but I can't connect to the FTP.. hmm... but if I do sudo hamachi list I can see 5.24.106.15, but I can't ping it.


I had the computer turned off, its running now, and the FTP is running as well.

---

### Post by majikstreet on 2006-03-12
hm.. still can't ping it.

---

### Post by Swiss on 2006-03-12
Try now, please PM me your Ext. IP so I can add it to my FW safe list.

---

### Post by majikstreet on 2006-03-12
pmed.

---

### Post by Swiss on 2006-03-12
First connect to the network (log in) then ping, you should get thru.

---

### Post by majikstreet on 2006-03-12
```

majikstreet@oreo:~$ sudo hamachi list
   [FTPSR]
     * 5.24.106.15
majikstreet@oreo:~$ ping 5.24.106.15
PING 5.24.106.15 (5.24.106.15) 56(84) bytes of data.
From 5.25.196.38 icmp_seq=2 Destination Host Unreachable
From 5.25.196.38 icmp_seq=3 Destination Host Unreachable
From 5.25.196.38 icmp_seq=4 Destination Host Unreachable

--- 5.24.106.15 ping statistics ---
4 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2999ms
, pipe 3
majikstreet@oreo:~$

```

---

