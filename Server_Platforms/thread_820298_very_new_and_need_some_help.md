---
title: "very new and need some help"
date: 2008-06-06
forum: Server Platforms
---

### Post by focus_uk on 2008-06-06
1st of all,i do not know anything about ubuntu software,i have only used windows before,i have a few questions and hope some of you guys can help me out..
1st of all i want to run a server,but i see you do a server and desktop ver,as am new to this then i think it would be best to try and run a website from the desktop ver,i think i need a gui to work with,is the desktop ver just as scure as the server ver,or how would i get the desktop ver as scure,
i have lot of questions be i think i will start with these at 1st.Thanks and i wait for some replys

---

### Post by Sef on 2008-06-06
Moved to server platforms.

---

### Post by cpetercarter on 2008-06-06
Do you really want to run a website off your desktop computer? There are at least two major problems - you need to set your firewall so that the world can access your computer; and you need to run your computer, connected to the internet, 24/7. This is the case no matter what operating system you use.

Website hosting packages are very cheap nowdays. Many have extras like a free domaine name thrown in. If you have not run a website before, I would start there.

If you install Ubuntu on your desktop, you can then install apache, php, mysql etc. You can use these to set up a "localhost" website on your computer, which you can use for development purposes and for generally getting to know how these things work.

Hope this is helpful. I switched from Windows to Ubuntu for my desktop a couple of months ago, and it has been a sweet experience.

---

### Post by focus_uk on 2008-06-06
Thanks for the reply,yes i have settup a website before but on windows,but am now lookin into a ubuntu webserver with a forum,all the guys in the know say f****d windows and get a linux server up and runnin.so here i am..

---

### Post by hyper_ch on 2008-06-06
it is recommended to use a descriptive thread title and not a generic "noob here" or "need help".

---

### Post by focus_uk on 2008-06-06
> **hyper_ch said:**
> it is recommended to use a descriptive thread title and not a generic "noob here" or "need help".

sorry about that..is it prosable to change it.

---

### Post by hyper_ch on 2008-06-06
nope, but remember it for the next one ;)

---

### Post by kamaji792 on 2008-06-06
I don't fully now the answer to this question but I don't think there is much difference over all between the desktop and server versions of ubuntu.  It is just the way they are set up to appear after you have done an install.

The server does not install a desktop so you do all your interaction with a terminal.  The desktop does not tend to install any server applications like mySql (database) and Apache (web server).

It is probably simpler to go from a desktop installation and then install any other services you may want like a web server.  Especially if you are coming from windows.

All that said try and do as much as possible with terminals as it will stand you in good stead when you switch to a server without a desktop.

My guess is you don't want a real server but want one for development/testing locally.  In which case a desktop setup should be fine.

All the best and keep us posted.

---

### Post by hyper_ch on 2008-06-06
the desktop version won't help you at all setting up the server... if you want a fully functional server, have a look at the perfect server howtos over at [http://www.howtoforge.com](http://www.howtoforge.com)

Falko makes with his howtos a server setup that is suited for an ISP meaning the hosting of multiple independant websites.

---

### Post by focus_uk on 2008-06-06
Thanks for the replys,and yes i do want a fully server runnin headless,its only goin to be uesd for an website and forum,i guess the server ed probly be the sest way to go,am now thinkin its goin to be alot more hard to learn but worth the time in learnin it,

---

### Post by hyper_ch on 2008-06-07
just follow the perfect howtos that you have at howtoforge.com.

---

### Post by kamaji792 on 2008-06-07
As you are new to ubuntu and have only used Windows before.  I still think to start with you should go desktop.  Then you have a friendly GUI to make you feel comfortable and help you climb the hill.  Once you have sorted out what you want to do and how to do it then re-build yourself a server without a GUI.

I re-build Linux boxes regularly.  Partly because it is so easy to do so.  Server are even quicker to build because you don't have to install a desktop :P

Even if you go for a headless box you can try **webmin**, though I have never tried it.  I use ssh, usually from a Windows box.  After a while you begin to think the GUI is a crutch.  Yes a while back it did help but now it is just slowing you down.

Any way all the best and enjoy :D

---

### Post by hyper_ch on 2008-06-07
how does the gui help in running a server?
If all the hardware works out of the box I see not how a gui can help there.....

---

### Post by focus_uk on 2008-06-07
ummmm very intrestin this linux is..been doin some readin up.i guess for me the best way to learn is jump at deepend with a test box,like i say i have only use windows and had to learn that in the pass,i think over the years i got used to the gui and got lazy,took the easy opt for everything,i guess it like goin back to the old dos days,tryin and error lol.one thing am unsure about is where do i input the data,in windows i use command propt.in linux desktop is it in termal.i have just install desktop on a little box for now just to have a look around,but it the server ed that i will be workin on in afew days after little mess about the desktop ver.Thanks

---

### Post by hyper_ch on 2008-06-09
well, typical "setting" up of a server at home is like this:

(1) attach monitor, keyboard, mouse to the box

(2) install the basic server

(3) install openssh-server

(4) configure network (for static ip)

(5) remove monitor, keyboard and mouse

----------------------------------

(6) Login from a desktop computer and start working on the other things...

from windows use putty, from linux use the terminal with "ssh USER@SERVERIP"

---

### Post by umattu on 2008-06-09
A gui on a server, IMO is a waste of resources BUT it won't hurt anything. If you would like to test the waters you could always install the ubuntu server and then once your running install gnome
```
sudo apt-get install gnome-desktop
``` 
This will give you a GUI to work from. 

There is, as mentioned before, webmin which is a great administrative tool. I'd recommend it to anyone!

Personally I would recommend that you install the server, and learn  how to do things the "old fashioned way" straight from the terminal. Not depending on a graphical interface is a GREAT skill to possess.

---

### Post by Jordanwb on 2008-06-09
> **kamaji792 said:**
> As you are new to ubuntu and have only used Windows before.  I still think to start with you should go desktop.  Then you have a friendly GUI to make you feel comfortable and help you climb the hill.

I've used windows for about 12 years. I had a harder time using Ubuntu Desktop than using Ubuntu Server, because all Server is is commands.

The thing I would suggest you do first is try to understand the basics of file structure in Linux. After that it's a cakewalk (at least it was for me).

---

