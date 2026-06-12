---
title: "Unknown error from opentracker"
date: 2013-05-20
forum: Server Platforms
---

### Post by Spency on 2013-05-20
Hello,

I run ubuntu server 12.04 with the latest version of amahi installed on top. 

I'm trying to configure a small private bitorrent network using opentracker. Unfortunately there is almost no documentation for this program.

When I try to run the opentracker executable, I get this error: ```
$ ./opentracker
socket_bind6_reuse: Address already in use
```

Searching google has not been fruitful. The only actual installation guides I've found have been here: [http://erdgeist.org/arts/software/opentracker/](http://erdgeist.org/arts/software/opentracker/) and here: [https://forum.suprbay.org/showthread.php?tid=115305](https://forum.suprbay.org/showthread.php?tid=115305)

It installs fine. That's not really the issue, but this is the documentation I've been able to find on it.

The only mentions of the error I've found are here in this IRC log: [http://irclogs.ubuntu.com/2010/10/23/%23ubuntu.txt](http://irclogs.ubuntu.com/2010/10/23/%23ubuntu.txt) 
A guy asked the same question I have, and no one responded to him.

This is a similar looking error but again no answers: [http://webcache.googleusercontent.com/search?q=cache:hV_l2dZ6m0UJ:https://bugzilla.redhat.com/show_bug.cgi%3Fid%3D523540+&cd=2&hl=en&ct=clnk&gl=nl](http://webcache.googleusercontent.com/search?q=cache:hV_l2dZ6m0UJ:https://bugzilla.redhat.com/show_bug.cgi%3Fid%3D523540+&cd=2&hl=en&ct=clnk&gl=nl)

When I run the debug I get the same error:
```
$ ./opentracker.debug
Binding socket type TCP to address [0.0.0.0]:6969...socket_bind6_reuse: Address already in use
```

VERY NOOB QUESTION: To uninstall opentracker, should I just rm -r /etc/opentracker/? 

Please help!

Spency

---

### Post by lykwydchykyn on 2013-05-20
Did you install opentracker using apt-get?

The error you're getting usually happens when some other process already owns the port that your service is trying to use.  You can find out what's using it by running this:
```

sudo netstat -tunap |grep 6969

```

---

### Post by Spency on 2013-05-20
--sorry double post--

---

### Post by Spency on 2013-05-20
When I tried what you gave me, nothing happened. The prompt just returned.

Then I decided to try ```
 $ cd /etc/opentracker
$ ./opentracker 
```

Then something must have happened, because the prompt did not return. Just black emptiness. I gave up after waiting five minutes, and opened a new terminal window and shelled back in.

Then I tried what you gave me again and this is what I got:

```
 
tcp        0      0 0.0.0.0:6969            0.0.0.0:*               LISTEN      13158/opentracker
udp        0      0 0.0.0.0:6969            0.0.0.0:*                           13158/opentracker

```

That sort of seems like it's already running. no?

---

### Post by lykwydchykyn on 2013-05-20
Yes, it is already running.

In Linux, "no news is good news", i.e. you will usually not get a response from a command unless there's a problem.  Well, a well-written command anyway.  If what you're running is a service, it will just "hang" like that, since it's running and isn't interactive in any way.

Again, how did you install?  I'm surprised a service didn't install some kind of start-stop script.

---

### Post by Spency on 2013-05-20
I followed the instructions here: [http://erdgeist.org/arts/software/opentracker/](http://erdgeist.org/arts/software/opentracker/)

I'm struggling to configure or to find out how to even use it.

---

### Post by lykwydchykyn on 2013-05-20
I've never used it, so I can't help you there.  I'm not much of a torrent user, but there are probably some good, well-documented torrent programs in the repositories that you could use.  Have you tried any others?

---

### Post by Spency on 2013-05-21
I have not. ML Donkey seems promising because it has a GUI.

Opentrackers advantage is that it is the least resource intensive tracker software for linux. I might try some of the others, but I want to play around with open tracker a bit more.

Thanks for the help. :-)

---

