---
title: "Cannot shut down remote machine / server"
date: 2010-03-21
forum: Server Platforms
---

### Post by ade234uk on 2010-03-21
I am running a local webserver mainly for development. I have everything set up. The issue I currently have is that I cannot shut down the machine from the command line. I can issue the command but the machine remains on. I also cannot get to the desktop via VNC.

The reason for this, is that there is no monitor attached so Ubuntu says that it is trying to run in Low Graphics Mode. I found this out as I plugged the monitor in to my server.

So question is, how do I get around this? 
How can I set up Ubuntu to get past this, or do I need to install Ubuntu Server?

I would prefer a solution to getting past Low Grpahics Mode so I dont need to set everything up again.

---

### Post by jfparis on 2010-03-21
Ubuntu Server might have been a better solution. The main issue with running the desktop version of ubuntu on a server is that is comes with a lot of gizmos that are useless on a server and that also consume resources (mem cpu disk). A linux server can be easily managed with ssh and you don't need to have a gnome desktop that you will access with VNC or whatever.

So if you want to keep the desktop version you will have to look around and remove the desktop components that are useless in your situation. That should be possible but it might take time.

There are also some differences with the scheduler used by the kernel. 

My call would be to reinstall the server version right now. Might be quicker than cleaning and the longer you wait and install new apps on that server the more painful and time consuming it will be when you have to reinstall

Now regarding your problem maybe you can try this

```

service gdm stop

```gdm is the log-in screen. If you terminate this service that will shutdown the desktop. Might be some component there that are waiting for you to click before restarting

Then issue the shutdown again
```

shutdown -r now

```If that help, you can try to disable gdm permanently. Try **either** of 

```
apt-get remove gdm
``````
update-rc.d -f gdm remove
```The first line uninstalls gdm (never try don't know what is going to happen) and the second one just removes gdm from the list of services that are automatically started

---

### Post by ade234uk on 2010-03-21
Thank you for the info. Your right, I will try these commands and then look at installing Ubuntu server. I will be better off in the long run.

---

### Post by amauk on 2010-03-21
You *should* be able to use the shutdown / halt / reboot CLI commands on either desktop or server

the Desktop edition should shutdown exactly like the server edition when using the command line
if it doesn't, then something is wrong

Btw, you can make a desktop install into a server install (and vis-versa and lots more in between) by using the task selector
```
sudo tasksel
```

unselect the desktop entry and select the server entry

Do this locally, rather than over SSH, as this uninstalls networkmanager, and you'll lose network connectivity half-way through

---

