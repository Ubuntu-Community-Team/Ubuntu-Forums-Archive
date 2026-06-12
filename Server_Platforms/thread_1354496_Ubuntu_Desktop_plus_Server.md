---
title: "Ubuntu Desktop plus Server?"
date: 2009-12-13
forum: Server Platforms
---

### Post by piojunbabia on 2009-12-13
I would like to know if it is possible to install server installation in Ubuntu 9.10 Desktop? I mean I want my Desktop have the powers of Server. I have heard it can be run virtually on Desktop. I have Desktop pre-installed.

Or maybe an alternative: install Apache, PHP and MySql on my Desktop? would that be possible too? 

any but's? and however's? deeply appreciated.... Thank you

---

### Post by falconindy on 2009-12-13
If you want the features of a server with the GUI of a desktop, you're better off using the server install CD and then adding in the 'ubuntu-desktop' package on top of it. The server uses a slightly differently optimized kernel that focuses more on background applications and a little less on snappy desktop response.

---

### Post by piojunbabia on 2009-12-14
is it not the other way around? desktop then server instead?

---

### Post by HighCommander540 on 2009-12-14
> **piojunbabia said:**
> is it not the other way around? desktop then server instead?

Nope, having a installation of desktop that you add server stuff to...Would give you the worst server ever. It would be stupid slow.

But if you really want to run this:

```
sudo tasksel install lamp-server
```

The best way to do it, is what was mentioned. Download and install the server edition. Then install GNOME or I think on Ubuntu it is 'ubuntu-desktop'. Then you will have a GUI. Really unless you want the worst server ever to exist just don't install a GUI at all. Learn to use the terminal.

---

### Post by CharlesA on 2009-12-14
You can run a "server" just fine using the desktop kernel. You just need to install whatever services you need.

As for a server being "worst. server. ever." just because you have a GUI is pure BS. Just cuz you have a GUI, doesn't mean you cannot access the terminal. Having multiple ways of doing things is handy.

---

### Post by piojunbabia on 2009-12-14
> **HighCommander540 said:**
> 

But if you really want to run this:

```
sudo tasksel install lamp-server
```



I am done executing this code. I got an installation procedure. It asked for a new password for root user for Mysql. So is it done? My PC is now a server? how can i access Php? and Mysql? and configure the apache?

---

### Post by toddedw on 2009-12-14
> **CharlesA said:**
> You can run a "server" just fine using the desktop kernel. You just need to install whatever services you need.

As for a server being "worst. server. ever." just because you have a GUI is pure BS. Just cuz you have a GUI, doesn't mean you cannot access the terminal. Having multiple ways of doing things is handy.


He was partially right in that the server kernel is optimized for server applications and stability. Worst server ever might be a little over the top and misleading. This is obviously (well hopefully) not going to be a production server. If he just wants to do local development and sharing of stuff on his home network a desktop kernel should do him just fine.

---

### Post by wojox on 2009-12-14
[Ubuntu Server Guide]("https://help.ubuntu.com/9.10/serverguide/C/index.html")

---

### Post by HighCommander540 on 2009-12-14
> **CharlesA said:**
> You can run a "server" just fine using the desktop kernel. You just need to install whatever services you need.

As for a server being "worst. server. ever." just because you have a GUI is pure BS. Just cuz you have a GUI, doesn't mean you cannot access the terminal. Having multiple ways of doing things is handy.

Um...No, if you have a GUI for the server that will take away lets see...Like 15% of your CPU. The point of a server is to dedicate ever last drop of CPU power to serving up requests. I never said you couldn't access it from the terminal. I am trying to make a point here, that if you are going to install a server. Do it right. Not the stupid noob way. And yeah he may be a noob, by why would you want to teach someone how to do something the wrong way?

> **toddedw said:**
> He was partially right in that the server kernel is optimized for server applications and stability. Worst server ever might be a little over the top and misleading. This is obviously (well hopefully) not going to be a production server. If he just wants to do local development and sharing of stuff on his home network a desktop kernel should do him just fine.

Yeah, that's true. I just hate to see people do things the wrong no productive way.

> **piojunbabia said:**
> I am done executing this code. I got an installation procedure. It asked for a new password for root user for Mysql. So is it done? My PC is now a server? how can i access Php? and Mysql? and configure the apache?

Yeah, if you entered a password. That is the password for your MySQL root user. Everything should be setup to run Apache, PHP, and MySQL on your localhost. If you want access from elsewhere you need to do some more stuff.

---

### Post by Thocrun on 2009-12-14
Why not just install the LAMP like before then open terminal and use that just like a server(using the server guide-unless it is a different version of Linux Apache MySQL or Php?

---

### Post by CharlesA on 2009-12-14
> **HighCommander540 said:**
> Um...No, if you have a GUI for the server that will take away lets see...Like 15% of your CPU. The point of a server is to dedicate ever last drop of CPU power to serving up requests. I never said you couldn't access it from the terminal. I am trying to make a point here, that if you are going to install a server. Do it right. Not the stupid noob way. And yeah he may be a noob, by why would you want to teach someone how to do something the wrong way?

So the "stupid noob way" is to install a GUI? Ok. 

I've got a GUI installed on my server, even tho I mostly just SSH into it to run commands. I might not even bother installing Gnome when I redo the server for 10.04, since I can just tunnel webmin and my raid management software over SSH and admin it that way.

---

### Post by piojunbabia on 2009-12-15
> **Thocrun said:**
> Why not just install the LAMP like before then open terminal and use that just like a server(using the server guide-unless it is a different version of Linux Apache MySQL or Php?
Yes, yes, yes... noob way is the only thing i need now because... I am still learning its basics... so now i need a sort of "gui" 

> **HighCommander540 said:**
> Um...No, if you have a GUI for the server that will take away lets see...Like 15% of your CPU. The point of a server is to dedicate ever last drop of CPU power to serving up requests. I never said you couldn't access it from the terminal. I am trying to make a point here, that if you are going to install a server. Do it right. Not the stupid noob way. And yeah he may be a noob, by why would you want to teach someone how to do something the wrong way?
i understand your point now, i need a server didicated system, but not now if im still learning..this one's for pracice/educational purpose only (in my part)...

> **HighCommander540 said:**
> 
Yeah, if you entered a password. That is the password for your MySQL root user. Everything should be setup to run Apache, PHP, and MySQL on your localhost. If you want access from elsewhere you need to do some more stuff.

Okay. so how am i supposed to do that? is my apache now activated? how do i..... can you give me some manuals for php and mysql start-ups that is good for me? thank you....

---

### Post by HighCommander540 on 2009-12-15
> **CharlesA said:**
> So the "stupid noob way" is to install a GUI? Ok. 

I've got a GUI installed on my server, even tho I mostly just SSH into it to run commands. I might not even bother installing Gnome when I redo the server for 10.04, since I can just tunnel webmin and my raid management software over SSH and admin it that way.

Yes, it is. You realize that you rhetorically asked if it was the noob way and then answered your own question, by saying when you do it correct because of what you have learned you are going to get rid of it...I am not trying to be mean or anything. I am just trying to teach the right way the first time. Instead of learning two different ways. Anyone can use a GUI.

> **piojunbabia said:**
> Yes, yes, yes... noob way is the only thing i need now because... I am still learning its basics... so now i need a sort of "gui" 

i understand your point now, i need a server didicated system, but not now if im still learning..this one's for pracice/educational purpose only (in my part)...

Okay. so how am i supposed to do that? is my apache now activated? how do i..... can you give me some manuals for php and mysql start-ups that is good for me? thank you....

First, its ok to be a noob we all were at one point. The thing I am trying to get across is that most of the stuff you are going to be editing and setting up are through the terminal anyway. So really you should just learn to do it with the terminal instead or relying on a GUI.

When I first learned to set up my own server someone recommended this to me. And yes it took me a bit to get my server running correctly, but ever since then everything is easy as hell. And I know what do to when stuff goes wrong.

---

### Post by piojunbabia on 2009-12-15
i would be needing another computer for that. My family is using this PS for games and school stuffs and they need GUI for that. I can try not using GUI but they(my family ) cant use this computer.. well i can always access the terminal anytime. All i just need at the moment is the how-to of the server stuffs.. when i can do it now, then il be ready for a real server. I might buy a new PC for that. But i cant really do it now. Anyway, thank you for pushing me to the right and best thing, but i just cant have it right now and i wont for others sake.

---

