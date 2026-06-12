---
title: "GUIs and Servers, time and time again."
date: 2009-03-09
forum: Server Platforms
---

### Post by netztier on 2009-03-09
Hi all

[SIZE="1"]Forum Mods - can we have this post (or some of it) as sticky, please?
[/SIZE]

It happens at least twice a week that a question about "**GUI on Ubuntu Server?**" pops up in the forums.

The questions have been answered again and again, and the debate is sometimes quite controversial, and both the "pro" and the "contra" sides have good and valid points to make. So anyone interested in installing a GUI on their Ubuntu Server installation, please read:

[https://help.ubuntu.com/community/ServerGUI](https://help.ubuntu.com/community/ServerGUI)

Personally, I think that you should *not* run a GUI on a server. This is Ubuntu, this is Linux, this is the universe of UNIX-like operating systems on servers. Some concepts of the "Windows world" just don't hold here.

If you absolutely need a GUI, install the Desktop version of Ubuntu and then add the server programs to it - you can run Apache, Samba, BIND, MySQL, LDAP etc perfectly well on Ubuntu Desktop. Integration & maintenance of the typical GUI components like NetworkManager, Avahi etc. are just far better with the Desktop installation. If you need multiple text consoles in parallel, look at **screen** instead of installing a GUI and desktop environment.

regards

Marc

---

### Post by hyper_ch on 2009-03-09
:)

---

### Post by daboroe on 2009-03-09
nice write up. nice link :)

---

### Post by windependence on 2009-03-10
Fantastic! Finally, a good link we can post without writing so much. :)

-Tim

---

### Post by volkswagner on 2009-03-10
Plus one.  How about joining a domain as a close second.

I wish the forum had a better search result.  I searched this forum for "time and time again" and got the standard 250 most recent posts. LAME

Nice write up.

Bump to keep it on page one.

;)


EDIT: It just occurred to me, if the forums had a more accurate query yield, maybe this thread would be mute.

---

### Post by mistypotato on 2009-03-10
Hello,

You "learned" folks have NO idea what we noobs go through :P

I just installed the X11 server GUI from the webpage mentioned in this thread on a fresh 8.10 server install.

After installing it and rebooting, I was expecting the computer to open into some kind of a GUI...not the same black & white console prompt.

I wonder if in many cases the repeated questions are due to lack of documentation or expected results?   No problem...but it did make me come here and ask yet ANOTHER GUI QUESTION  :P


I can't figure out how to get into the GUI I just installed per instructions in THIS thread :lolflag:


Hey,...don't flame..don't blame :KS

---

### Post by yther on 2009-03-10
I agree!  A stick would help... for those who read stickies, of course.  ;)

Also, the forum "search engine" does suck.  Would it have cost more money to include "AND" matching or something?  :?  I never use it any more, I use Google instead with "site:ubuntuforums.org" added.

---

### Post by mistypotato on 2009-03-10
The search issue is PURELY a vBulletin issue.

The good folks at ubuntu can't do much about it.


As far as the asking "again and again"....

Do you REALLY think any kind of sticky, How-To, documentation or "hand-holding" is going to ever stop that?

ANd really, what's the point?  it's part of the excitement (for us noobs anyway).... a "live" answer to our own personal question... it's not just the content....it's the J-O-U-R-N-E-Y.    

Same reason why some people prefer window seats on an airplane.
And if the person next to you bothers you that bad, simply ask for a seat change ;)

A few flights ago as a passenger, I had a woman with two toddlers with colds so bad they were snnezing, coughing and draining mucus like crazy sitting next to me.....rather than be miserable and complain.........I changed seats.  :KS:KS:KS:KS:KS

---

### Post by hyper_ch on 2009-03-10
> **mistypotato said:**
> You "learned" folks have NO idea what we noobs go through :P
You think we were all born with that knowledge?

> **mistypotato said:**
> I wonder if in many cases the repeated questions are due to lack of documentation or expected results?
It's more the "I want this and that now without being required to invest time and effort and learn something"-mentality.

---

### Post by HermanAB on 2009-03-10
Hmm, I agree that instead of wasting time with installing a GUI on the server version, just install the regular Ubuntu version.

---

### Post by mistypotato on 2009-03-10
Herman....you missed the pooooooint.....

Maybe we want to "learn" the server....at our own ...painfully slow pace :P

---

### Post by redmk2 on 2009-03-10
> **mistypotato said:**
> Herman....you missed the pooooooint.....

Maybe we want to "learn" the server....at our own ...painfully slow pace :P

Could it be that both Herman and mistypotato have both missed the point and are right on point?  Differing views of the same goal.

If I use the classic definition of a server IE: a process waitiong to serve a client request.  Then a server could be on either the "Server Edition" OS or it could just as well be on the "Desktop Edition" OS.

Thi is what I have always called servers:

```

Server = httpd  Apache
       = slapd  LDAP
       = named  DNS
       = sshd   SSH
       = smbd   Samba
...etc

```

For those using the OS to run servers only there is no need for a GUI.  In this case I agree with Herman et al.  In addition you have an optimized kernel for the heavy usage. 

For those learning and experimenting with configuration eg: non production, The Desktop edition of the OS will work just fine.  It supports all of the server daemons.

Both the hard core (production Server OS) and the newbies (Desktop Edition) have valid points.

---

### Post by hyper_ch on 2009-03-10
actually the definition you have given above is for a "service/daemon" and not server as by server the box itself is referred to. And classic servers are gui-less. Only microsoft makes guis on servers...

---

### Post by koenn on 2009-03-10
> **mistypotato said:**
> 
Maybe we want to "learn" the server....at our own ...painfully slow pace :P
Fine, but a GUI isn't going to help you. You can have all of gnome and ubuntu-desktop on your server, and you'll still end up editing a config file in a text editor. There's no apache setup wizard, Samba wizard, etc ... 
So what's the point of that GUI when all you can use it for is to run a terminal emulator and a text editor ?
OK, browsing through a file manager slightly helps if you don't know your way around, but you'll find that 99% of the time, you're working in /etc anyway, so ... 


@OP : excellent write-up.

---

### Post by koenn on 2009-03-10
> **hyper_ch said:**
> actually the definition you have given above is for a "service/daemon" and not server as by server the box itself is referred to. And classic servers are gui-less. Only microsoft makes guis on servers...
actually server can be used as a synonym for service or daemon. As in "client-server architecture", which is strictly about software. Or as in X-server, ...

> server

1) In information technology, a server is a computer program that provides services to other computer programs (and their users) in the same or other computers.[http://whatis.techtarget.com/definition/0,,sid9_gci212964,00.html](http://whatis.techtarget.com/definition/0,,sid9_gci212964,00.html)

---

### Post by redmk2 on 2009-03-10
> **hyper_ch said:**
> ... And classic servers are gui-less. Only microsoft makes guis on servers...

Look at OpenSolaris. I have used Solaris since Solaris8 and there is a GUI for it.  None the less GUI's are for OS's and not servers.  the term services is a Microsoft convention.

---

### Post by Brazen on 2009-03-10
First of all, it would be much better to install Ubuntu Server and then add on a gui with "sudo aptitude -R install ubuntu-desktop".  That way you get the optimized server kernel and you don't get the automagical packages that can cause conflicts in your server setup.

Second of all, I think people need to make a distinction between a "learning" server and a "production" server.  Personally, I think you are an embarassment to the linux community if you put a server into production usage with a gui on it.  That may sound harsh, but the point needs to be made.  If you are just using this server for a learning experience, then it's not such a big deal.  Personally, I think you would be better off learning to do things The Right Way(tm) from the beginning, and not get comfortable with bad habits, but I'm pretty forgiving to beginner naivety - just don't put that learning server into production *shakes finger*

---

### Post by hyper_ch on 2009-03-11
> **koenn said:**
> actually server can be used as a synonym for service or daemon. As in "client-server architecture", which is strictly about software. Or as in X-server, ...

[http://whatis.techtarget.com/definition/0,,sid9_gci212964,00.html](http://whatis.techtarget.com/definition/0,,sid9_gci212964,00.html)

Well, go onto google and enter:  define:server

Most of them refer to the machine itself.

---

### Post by netztier on 2009-03-11
> **mistypotato said:**
> 
Do you REALLY think any kind of sticky, How-To, documentation or "hand-holding" is going to ever stop that?


After 5 years of desktop support and 8 years in 2nd and 3rd level of network support, frankly: no, I don't. ;-)

People don't read man pages, they don't read manuals, don't read FAQs (but rather ask the questions again), so why should they read stickies? 

Still, being somewhat of a positive thinker, and I wanted to make an effort to point out that the Ubuntu people at canonical indeed *have* a stance about GUI-on-Server and that they deliberatly decided *not* to have one installed by default.

> **mistypotato said:**
> 
A few flights ago as a passenger, I had a woman with two toddlers with colds so bad they were snnezing, coughing and draining mucus like crazy sitting next to me.....rather than be miserable and complain.........I changed seats.

Right. If I were to map that to our current discussion, I'd come up with: Stop complaining about Ubuntu Server's lacking of a GUI, change seats and start using Ubuntu Desktop (which even is a window seat)? ;-)

regards

Marc

---

### Post by netztier on 2009-03-11
> **daboroe said:**
> nice write up. nice link :)

Just to avoid any misunderstandings: I am *not* the author of [https://help.ubuntu.com/community/ServerGUI](https://help.ubuntu.com/community/ServerGUI) , nor did I ever contribute to it.

I happened to find it when I was looking for some FAQ about Ubuntu Server where Canonical explicitely stated that and why Ubuntu Server did not come with a GUI.


regards

Marc

---

### Post by 720iD on 2009-05-28
> It happens at least twice a week that a question about "GUI on Ubuntu Server?" pops up in the forums.
hey, great to know i am not the only one, ha ha, i just posted a topic then i found this thread. indeed the forum search sucks big. 

thanks for this thread.

---

