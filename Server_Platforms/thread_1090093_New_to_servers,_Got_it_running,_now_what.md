---
title: "New to servers, Got it running, now what?"
date: 2009-03-07
forum: Server Platforms
---

### Post by Don1500 on 2009-03-07
I followed the instructions perfectly and everything went well. 

I can enter the IP into Firfox from my main machine and I get "It Works!".

I can ssh to the server and run it remotely from my main machine.

Now I want to log on as a user with my browser and search the drives for programs, music, whatever. How do I get in as a user and use a gui desktop?

---

### Post by mrsteveman1 on 2009-03-07
You want a graphical desktop on your server that you want to access from a remote machine?

You'll have to actually install one of the desktop environments if one isn't already installed, and then you'll have to turn on screen sharing from inside that desktop environment. That is the simplest way to get a remote desktop type setup.

---

### Post by hyper_ch on 2009-03-08
what do you want this machine to do? It seems to me you don't want a server.

---

### Post by scottuss on 2009-03-08
If you want to just browse files on it, on your client machine go to Places > Connect to Server > Select SSH from the Service Type drop down box then enter your server details into the form. When you connect it will pull up the directories on your server.

The Server box is the IP address for the server, don't specify a folder and just use a username set up on your server.

That's what you want to do isn't it?

---

### Post by Don1500 on 2009-03-08
> **scottuss said:**
> If you want to just browse files on it, on your client machine go to Places > Connect to Server > Select SSH from the Service Type drop down box then enter your server details into the form. When you connect it will pull up the directories on your server.

The Server box is the IP address for the server, don't specify a folder and just use a username set up on your server.

That's what you want to do isn't it?

Thanks, that's what I needed.

---

### Post by scottuss on 2009-03-08
> **Don1500 said:**
> Thanks, that's what I needed.


No problem :)

---

### Post by hyper_ch on 2009-03-08
ah... just accessing the server.

You could also install on your desktop sshfs then you could mount the server into your local filesystem.

You'd create a little shell script like this:

```

#!/bin/bash
sshfs user@server_ip:/home/USER /home/USER/Desktop/SERVER -o uid=1000 -o gid=1000

```

Just enter the according path on the server and your local filesystem and set the correct uid and gid.

And if the server is always running you could even mount the server into your local filesystem at boot with the fstab

---

### Post by Don1500 on 2009-03-08
Actually it's a building block to understanding the structure of the linux server. I take small bites and chew until I understand exactly what is going on. I got the server working now I am trying to understand how to controll every aspect of it. The first step was to get my desk top to talk to the server (an old laptop.) Next I'll get the server to display html. Then go from there. It might take a while but I'll know how to make it dance when I'm done. 

BTW I set up my first LAN in 1983 (StarLan) on DOS. But I haven't done any of this for years. I have the time and the hardware now so I thought I'd get back into it.

---

### Post by Iowan on 2009-03-08
You've no doubt discovered that the standard server install comes without GUI.  As an old DOS user, the CLI should present you with a curiously familiar environment - although many of the basic commands have changed somewhat.
Have you seen [this]("https://help.ubuntu.com/community/ApacheMySQLPHP") help page?

---

### Post by Don1500 on 2009-03-09
Thanks, I'll go over that tonight (at work now).

---

