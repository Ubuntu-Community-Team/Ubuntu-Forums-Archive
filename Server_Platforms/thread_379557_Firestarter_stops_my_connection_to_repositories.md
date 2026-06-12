---
title: "Firestarter stops my connection to repositories"
date: 2007-03-08
forum: Server Platforms
---

### Post by bravemosquito on 2007-03-08
When I run Firestarter from System > Administration (Gnome) she's beginning to stop my connection to repositories:

91.189.89.6 (archive.ubuntu.com)

and I cannot download desired packages or updates. What's goin' on here :shock: 



p.s. check out my other thread about Firestarter >> [http://ubuntuforums.org/showthread.php?t=378662](http://ubuntuforums.org/showthread.php?t=378662)

---

### Post by bapoumba on 2007-03-08
Have you set up particular outbound or inbound policies ?

---

### Post by bravemosquito on 2007-03-08
Yes, because I'm behind a small-hardware router. I've already added internal GW ip - 192.168.x.x, allowed for inbound and outbound traffic (but there's no problem with i-access w/o this policy).

There is some interesting situation on my other ubuntu-box: I cannot gain Internet access until I add same ip to Firestarter :?

For two boxes I just used **iptables --flush** command, for cleaning current chains and to start from scratch.

---

### Post by towsonu2003 on 2007-03-08
hmm, I was having trouble using archive.ubuntu.com myself... and with me as well, firestarter is blocking my connection to there. I experience the similar thing with a few other sites. I wonder what's going on...

ps. did "iptables --flush" work?

---

### Post by bravemosquito on 2007-03-09
No, but I saw something strange - in Firestarter's log panel the update server is blocked because of  attempt to connect through a port with my machine. It is normal, but why Firestarter a.k.a iptables drops the incoming connection?

---

### Post by towsonu2003 on 2007-03-09
> **bravemosquito said:**
> update server is blocked because of  attempt to connect through a port with my machine. It is normal, but why Firestarter a.k.a iptables drops the incoming connection?

exact problem with mine... I have no clue why this is going on... it shouldn't drop the connection bc it is first requested by an outgoing connection... that is, when you request a connection with a webserver and that server tries to connect to you, it's not an incoming connection. it's just the continuation of an outgoing connection, which is allowed (obviously) in my iptables and in yours most probably as well...

I'm having similar problems with these two sites:
[http://www.caybasipekusu.com/](http://www.caybasipekusu.com/) (a local village website)
[http://www.cyberciti.biz/](http://www.cyberciti.biz/) (a linux blog thingy)

I contacted [http://www.cyberciti.biz/](http://www.cyberciti.biz/) webmaster, but he didn't know what was going on. pls let me know if you can find a solution, this is annoying (which, I'm sure, you know as well :) )

---

### Post by X-626 on 2007-03-11
I also had the exact same problem.  Couldn't connect to *most *repositories (I used some other mirrors) and some other sites.  However, I was able to fix mine using the Firestarter GUI.  I just went to Preferences, Advanced Options, and unchecked "Block traffic from reserved addresses on public interfaces" and it worked.  Hopefully, that's what the problem  is for all of you as well.

---

### Post by towsonu2003 on 2007-03-11
excellent -works for me, thanks :)

PS. what's that option good for? there's no documentation for it

edit: bug submitted for more documentation on that box at [http://bugzilla.gnome.org/show_bug.cgi?id=417223](http://bugzilla.gnome.org/show_bug.cgi?id=417223)

---

### Post by X-626 on 2007-03-11
Glad it helped.  To be honest, I have no idea what that does, exactly.  I just experimented with a few settings, and that one was the only one that, when unchecked, actually fixed the problem.  I'm sure someone else knows exactly what it does, though.

---

### Post by bapoumba on 2007-03-11
Hello :)
I'm using Firestarter, without any problem, and this box has never been checked, as far as I know. May be something during the installation process ?

---

### Post by X-626 on 2007-03-11
I really don't know.  I've had Firestarter installed for many months, now.  I never had a problem with it until about a month ago.  I never really messed around with the GUI much, so I don't know if it had been checked the whole time for me or not (but it shouldn't have been, since I was able to connect to repositories before).  I do find it strange that it seemed to happen all of a sudden, though.  Anyway, I'm just glad it's working now.  I wish I knew what that setting actually does, though.

---

