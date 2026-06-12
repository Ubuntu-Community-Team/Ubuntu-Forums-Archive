---
title: "My server keeps stopping a process if I close SSH."
date: 2007-08-14
forum: Server Platforms
---

### Post by kavon89 on 2007-08-14
This is what I've tried:

```
nohup bash ~/scripts/cs_server &
```

It's not running in Steam.

I tried a vncserver and with my desktop, vncviewer. Last night I got vncviewer to ask for the password to connect to 192.168.1.40, which is my server box, but it said Connection refused. I opened port 5900, which is for vnc.

I can run the cs_server script in SSH, and it sets up without finishing and giving a new command line. the window becomes the server, I can do say "test" commands and change the CS 1.6 server's hostname. I just can't get it to stay on if my PC is off or if I close that window.

Some people recommended *screen*, I just don't know how to use it. The Beginner forum seems to not be as knowledgeable about this stuff.

---

### Post by deuce868 on 2007-08-14
[http://www.google.com/search?hl=en&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aofficial&hs=L6z&q=+with+screen+linux+command&btnG=Search](http://www.google.com/search?hl=en&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aofficial&hs=L6z&q=+with+screen+linux+command&btnG=Search)

---

### Post by bodhi.zazen on 2007-08-14
Try these links :

[http://www.linuxjournal.com/article/6340](http://www.linuxjournal.com/article/6340)
		[http://www.linuxjournal.com/articles/lj/0105/6340/6340t1.html](http://www.linuxjournal.com/articles/lj/0105/6340/6340t1.html)

	[http://gentoo-wiki.com/TIP_Using_screen](http://gentoo-wiki.com/TIP_Using_screen)

---

### Post by Brazen on 2007-08-14
I would tend to want to find out why it is not working in the first place.  For one thing, are you using Dapper?  If not, I would bet if you used Dapper on your server, everything would work the way it should.  But I don't know anything about Steam and CS and whatever, so maybe this is a problem with them and not with Ubuntu.

Anyway, screen would also work for you.  Install it with this ```
sudo aptitude -y install screen
```or if you don't have aptitude (which you should, "sudo apt-get -y install aptitude"```
sudo apt-get -y install screen
```
and then```
screen
nohup bash ~/scripts/cs_server &
```and then exit the screen with control-"a" and then hit "d".  Then just exit your ssh and cs_server should still be running.

---

### Post by Brazen on 2007-08-14
Also, have you tried running cs_server with sudo?```
sudo nohup bash ~/scripts/cs_server &
```

---

### Post by MJN on 2007-08-15
> **kavon89 said:**
> This is what I've tried:
 
```
nohup bash ~/scripts/cs_server &
```
 
What does nohup.out say? It may hold the clue as to why the process is exiting.
 
Mathew

---

