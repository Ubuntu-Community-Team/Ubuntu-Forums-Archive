---
title: "Do I have to be local to manage &quot;Users and Groups&quot;?"
date: 2009-09-28
forum: Server Platforms
---

### Post by ocr14a on 2009-09-28
Hi. 
Do I have to be local to manage "Users and Groups"?

The reason I'm asking is that I'm getting into my Ubuntu server using NX, and when I go to the Users and Groups applet, the 'unlock' button is greyed out and I can't get in there to manage them.

---

### Post by scrooge_74 on 2009-09-28
Remember that is a admin thing you want to do. I don't know that app you are using, but probably the user dosent have the privileges needed for what you need to do.

Is like in command line if the user dosent have admin privs you can't add people to groups or create users

---

### Post by ocr14a on 2009-09-29
Thanks, Scrooge. 
However, I'm using the same account both locally and remotely. When logged in locally, I can unlock "Users and Groups", but when I am logged in remotely (via NX, which is an XDMCP client/server system), I can't. 

So, what I'm wondering is, is that a limitation of Ubuntu (or Linux ingeneral), or of the system I'm employing to get in remotely?

---

### Post by scrooge_74 on 2009-09-29
I wonder if it just a rights issue with the program, why dont you try to ssh into the box and use NX?

do a ssh -X your_box

log as your local user and then run NX, if you are able to change privs then is the privs through the program in the remote setting. hope this gives you some more clues

---

### Post by ocr14a on 2009-09-29
Hmmm, I'm not really sure if I even understand what you mean here. 

First off, I'm a Windows guy (I know....I can hear the booing coming down the line, but still...). So, I'm a bit lacking in my understanding of Linux stuff. 

That's kinda why I'm using NX to get into a GUI on my 'Server edition' (what?!?!....why did you install a GUI on your server edition?) in the first place. 

As far as I know, NX first opens an SSH connection and then uses it as a tunnel to then open an X session, but I have no idea if that's what's really happenign or not. 

One piece I can add to the mix is this.... 
Once, I tried logging into the server with NX remotely as root. Upon connecting, NX told me that it was in some way downgrading my rights so that I would only be connected as a user and not as an admin. 

That seems like something that NX is doing specifically, and I wonder if it's always the case, or just when logging in as root. 

Of course, if I were to connect with a regular SSH session (with my SSH terminal tool and not with the NX XDMCP GUI), I could manage users and groups via the command prompt. So, I know it's not that it can't be done remotely. The problem is that I want to do this remotely in a GUI (and specifically, in a GUI that gives me a separate X session on the server, not just a VNC connection to an already existing session). 

If it turns out that NX just has this limitation built-in and there's nothign I can do about it, is there anything else out there that will allow me to connect to a separate X session remotely with a GUI interface like this (I think I already researched this issue and found that XDMCP is the closest match to the Windows world's 'Remote Desktop' and/or 'Terminal Services', and that this NX is the best thing to do it for free in the Linux world)?

---

### Post by Jose Catre-Vandis on 2009-09-29
Its not just NX but other VNC type programs (UltraVNC et al) that do the same thing. Looks like you have complete control but you can't do everything (like try changing the screen resolution of your remote server!)

Your best approach is to do as scrooge suggests and ssh in.

First, setup ssh on your server
```
sudo apt-get install ssh
```

For a Windows client, you need to go and find **putty.exe**, which is a small gui program (;)) that will allow you to connect to a ssh session on your server. When you enter your user and password you will be returned to a terminal, and from there you can do anything, but with the command line. To manage users and groups, you will just need to learn a few simple commands: [This is quite a good reference]("http://www.ahinc.com/linux101/users.htm")

---

### Post by ocr14a on 2009-09-29
Thanks, Jose. 
I already have SSH running and as I mentioned before, I can get in that way, but I'm looking for a way to do things via GUI remotely (it's a headless server in a different building on the other side of campus, and I hate having to walk over there to manage it.....though I don't need to do that much). 

I know, I should just learn Linux and get used to working with the command line, but I just don't have time for that with my current work load. 

I will keep looking to see if there is a way around this issue.

---

### Post by scrooge_74 on 2009-09-29
Ok you can try my approaches, since I'm lazy most of the time.

I usually either vnc over ssh (like when I want to use a virtual XP running in the server and Im not in my own network).

VNC over ssh so I can then have complete control or:

You switch terminals ALT+Ctrl+F1 
log as your usual user then

xinit /usr/bin/xterm -- :1

Then you do your ssh -XC yourserver and then you can invoke your prefer GUI desktop (I use xfce)

The downside to this is that you can't use your regular desktop while using this method, the moment you hit ALT+CTRL+another_F_or_F7_to_go_back_to_your_desktop you lose the conection.

But I usually just invoke over a forwarded X session over ssh what ever app I want to use (most likely k3b to burn a disk or gscan2pdf to convert some images)

---

### Post by ocr14a on 2009-09-29
Scrooge,
thanks. I would like to experiment with your approaches. 
Woudl you be willing to lay them both out like this?...

approach 1 
step
step
step
...


approach 2 
step
step
step
...

---

### Post by scrooge_74 on 2009-09-29
Lets see

Approach 1

A. ssh -XC into_server
B. start vnc4server (if not already running)
C. launch vncviewer (or any other vnc client) here it depends how you got the viewer config (to have a full desktop session or just something running)

Aproach 2

A. Switch consoles (you are in F7) CTRL+ALT+F1
B. Log in   :D
C: Issue this command: xinit /usr/bin/xterm -- :1
D. ssh -XC your_server
E. start your X session

That should do it for both options

---

### Post by ocr14a on 2009-09-29
Thanks!  :) 

OK....I'm gonna try #1 first... 

So, I'm assuming (stupid here) that when you type this...
ssh -XC into_server

...and if my Ubuntu server's name is goodie, then my command line would be 

ssh -XC goodie

Is that right?

If so, next question.....I don't even have a VNC server set up yet. WHat's the best one (I know, that's a can of worms, and I should just do my own search, but...)?

---

### Post by ocr14a on 2009-09-29
OK, another stupid question.... 
I'm not sure how to start vnc4server, though I did install it just now. Is this something else I should probably read up on, or can you give me the short version....like a simple command to send it?

---

### Post by scrooge_74 on 2009-09-29
lol

Good thing this is open source and we dont charge by the chat or the hour :p

This is my command for my particular taste of size of monitor 

 vnc4server -geometry 1000x750 -depth 24

But that is just me it depends on the size of your monitor, after it starts (you should do it as your regular user), it will give you a message about the server something that ends in vnc4server:1  <---you want that last number cause you need it in the vnc client in your case the address of the server you want to connect will be localhost:1 

If you were doing it on a secure network where you dont need the ssh part it would be the IP_of_server:1


I read the other post after I posted, in order to just ssh name of server, you need to declare it in /etc/hosts

you need to give the real IP and next to it the name, so your client machine knows who you talking about

---

### Post by ocr14a on 2009-09-30
Thanks. 
Payment will be in beer at one of our local breweries if you ever get to the Boulder area. (what?...no beer drinking smilies?!?) 

Ok...so, this is one place where I see that, although it is more complex, Linux is better than Windows (among all kinds of ways, I know). 

In Windows, when I start the VNC server, that's it.....it just turns it on....there's only one instance possible and once it's started, that's it. 

In Linux though, if I'm understanding it corretly, I could potentially start up many VNC server *sessions*, and you're giving me instructions to start one....

....and when I connect to it, I am specifically connecting to that particular session, not just simply connecting to the VNC server like in Windows. 

I know I had heard of this years ago, but never had any point of experience with it to really know what they were talking about. 

Cool  :) 

So now... When I ssh into the server, what does "-XC" mean? 
I checked and that's not a commandline option with my ssh client. Sorry, bud.  :redface:


As for the ssh connection and name thing....yep, I get that already......I'm doing all of this over a private network on the same subnet.....so, hostname alone woreks fine.....once I try it over the internet, I will use the FQDN.

---

### Post by scrooge_74 on 2009-10-01
I hope to take you on that beer one day :D

ssh -XC means -X to forward X server (that is how you get yo see the pretty graphics coming from the server and you PC/laptop you use as client is only doing the display) all work is being done in server.

-C means to use compression if you have a slow connection, for me I use it when out of home, my adsl there is 1 MB but you can't ask it to just let you see an XP session running on a virtual server over the internet and expect to be quick :D without it

---

### Post by ocr14a on 2009-10-01
OK....sorry to be such an idiot, but do I run that command then at the command prompt after I have connected with ssh to the server?

---

### Post by ocr14a on 2009-10-01
Oh my.......I tried things, but have messed something up. It's not really bad, but definitely something I need help with. 

I'm sure it's obvious to you...

I ran the commands as follows....

I logged into the server with my SSH app, 

then I ran "ssh -XC servername" at the commandline, 

then I ran "vnc4server -geometry 1000x750 -depth 24" at the same commandline, 

then I opened vncviewer on my XP workstation, and tried to connect to servername:1 

It got rejected by the server's firewall. So I then had to go and create an exception in the server's firewall to allow VNC traffic in, 

then I tried again to connect with the VNCviewer, and it connected, but not like I thought it should... 

It was a grey box with a white command prompt kinda like when I open a terminal on the server or log in with ssh. 

I didn't know what to do there. So, I just closed it. 

At that point, I figured I'd just report back to let you know how far I got and see what to do next. 

However, now I can no longer connect to the server with NX. 

I'm assuming that if I can get this VNC-over-SSH thing to work, I won't need to get in vix NX anymore (especially since the reason I'm trying the VNC-over-SSH thing is due to the deficiency of the NX way of getting in there in the first place), but for now, until I get the VNC-over-SSH thing working, I will need to get in via NX. 

I know this is not your problem at all....I'm messing around with something that I should probably study up on, but I appreciate your willingness to do the hand-holding that you've been doing here.   :)

---

### Post by scrooge_74 on 2009-10-01
You are on the right track, what you had is the standard vnc window, if you typed gnome-session (if you have gnome install) or startxfce4 (xfce4) it would have started a gui session, you could also just start a program there like firefox.

Here are a few links that helped me on my way to master how to use vnc

[http://www.vanemery.com/Linux/VNC/vnc-over-ssh.html](http://www.vanemery.com/Linux/VNC/vnc-over-ssh.html)
[http://linux4research.blogspot.com/2008/01/config-vnc-on-debian.html](http://linux4research.blogspot.com/2008/01/config-vnc-on-debian.html)
[http://ubuntuforums.org/showthread.php?t=1271295](http://ubuntuforums.org/showthread.php?t=1271295)
[http://www.mythicalbeast.co.uk/linux/vncserver_howto.html](http://www.mythicalbeast.co.uk/linux/vncserver_howto.html)

In your /home/user folder in the  server there are  hidden files in ~/.vnc  where you can manage if you want the grey box or not or what apps you want to start automatically when you log into vnc

---

### Post by ocr14a on 2009-10-02
OK, cool. 

So, I went back to try it again, but when I ran the second command, "vnc4server -geometry 1000x750 -depth 24", 
this time I got the following message...

"xauth:  /home/reinhold/.Xauthority not writable, changes will be ignored" 

Any idea what I can do to get passed this (or are you done with this one?)? 

  :)

---

### Post by scrooge_74 on 2009-10-03
you got me on that one, I don't recall having that message, could it be you dont have permits to run xserver? which I don't think since you already use the gui there. But it looks like a permits issue

Log into it and just try vnc4server, in theory it should ask you to put a password so you can have some security while using vnc

---

### Post by ocr14a on 2009-10-05
Actually, I don't know why this worked or how it got messed up in the first place, but I went in and edited the permissions on /home/username/.Xauthority and it's fine again. 

:)

---

### Post by scrooge_74 on 2009-10-06
glad to see you figure it out

---

### Post by ocr14a on 2009-10-06
For the other thing (which you were helping me with), I think I will set up another Ubuntu server to play with it. 

Once I have that all up and running, I may come back to this thread to ask more, but I'll give you a break    :)

---

### Post by scrooge_74 on 2009-10-06
Cool, that is one reason I learned to virtualize so I could break stuff :D

---

### Post by ocr14a on 2009-10-06
Indeed.....same here (VMware). 
Well, not exactly....I started with it many years ago just as a tool to use on my workstation so I could test new software, etc, but now, I have my department's entire IT infrastructure running on a couple ESX boxes (and just about to add a handful of ESXi boxes to the mix).

---

