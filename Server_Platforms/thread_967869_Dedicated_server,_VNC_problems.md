---
title: "Dedicated server, VNC problems"
date: 2008-11-02
forum: Server Platforms
---

### Post by Chelmet on 2008-11-02
Hi all. 

Firstly, I am IT literate, but new to linux, so some things that you may take for granted may confuse me. 

Right, I have a dedicated server, hosted online, running   	ubuntu804-server_64. It is distant and headless, though I have full access by ssh, working fine.

Basically, my problem is that I am trying to run a few apps that *require* a GUI, and cannot be used from the CLI. A bit of research has told me that VNC is basically my only option, as I need to be able to see what's going on on this GUI. Once I have things set up I will be using ftp and http to interact with the server, but just now I need to see things.

I've read several guides on VNC, and I've tried a few clients, but just can't get it working. I think I am missing the fundamental theory behind it. I have been using the 'screen' program to virtualise a monitor, but really don't know what it does. And as to perpetual sessions? I understand the english, but being new to linux, not why a session would not be perpetual in the first place. 

Basically, I have searched myself and failed - can anyone either explain some of this, or point me to a few foundation/tutorial links? I have tried following tutes, but there's always one step I just completely fail to understand. 

NOTE: I just reinstalled the server software, so its a clean install - we're starting from the beginning.

Regards,

Chel

---

### Post by Xipher on 2008-11-02
Actually VNC isn't your only option here.

SSH has a feature known as X forwarding, this allows you to start graphical applications on a remote machine and have the display rendered using your local X server. If you're running windows you will need to install an X server first, one you could look at is
[http://www.straightrunning.com/XmingNotes/](http://www.straightrunning.com/XmingNotes/)

You will also need to enable X forwarding, using putty this is Under Connections -> SSH -> X11

Using openssh you use the -X flag when you connect.

With that you should be able to start any GUI applications from the ssh terminal and they will be rendered locally on your machine.

This isn't exactly a tested tutorial, but if you search for ssh x forwarding windows I think you should be able to come up with a better one if needed.

---

### Post by HermanAB on 2008-11-02
Here you go:
$ ssh -X -C -c blowfish user@server "gedit /etc/fstab"

SSH has a X client built in.  So provided that your local machine is running X, you can run remote GUI programs over SSH without having X on the remote machine.

However, in order to install GUI program on the remote machine, the package manager will likely want to install X, but you need not run X.  I usually install a full desktop system on a server, then just set it to run in level 3.

Cheers,

H.

---

### Post by Chelmet on 2008-11-02
Excellent, thanks for the help.

My mistake was confusing all of the technologies into one, Xserver, VNC, screen, etc. Got it working now.

So, a new problem: I can start my apps, and they run fine, but when I close the terminal, the programs close too - I want then to continue, and the session to be resumable. I read about it in some tute before I got it working, and can't remember any of the commands. Can you help with that please?

---

### Post by lykwydchykyn on 2008-11-02
> **Chelmet said:**
> So, a new problem: I can start my apps, and they run fine, but when I close the terminal, the programs close too - I want then to continue, and the **session to be resumable**. I read about it in some tute before I got it working, and can't remember any of the commands. Can you help with that please?

For that, you do need VNC.  Possibly NXserver might also work, though I have not tried to do resumable sessions with it.

Check out this tutorial:
[http://ubuntuforums.org/showthread.php?t=122402](http://ubuntuforums.org/showthread.php?t=122402)

---

### Post by cariboo on 2008-11-03
You still don't need VNC have a look at screen, there is a howto here:

[http://www.amitu.com/blog/2004/12/screen-howto.html](http://www.amitu.com/blog/2004/12/screen-howto.html)

Jim

---

### Post by Chelmet on 2008-11-03
Okay, again, thanks for the help. I'm glad it *can* be done, its just sorting it now. I'm not the only one using the apps, so I need them to continue running when my computer is turned off.

That link regarding screen is good, in that I'm able to resume a screen, but I'm unsure of the theory, and that's limiting my success. 

How do I open one of the apps on a specific 'screen' ? I know how to detatch and reattach a screen, but this seems to happen independant of my apps running, and I am not getting a GUI for the app when I open it in a specific screen. Any better explanation or links you could post? 

I just want to open an app, turn off my computer, the app to continue running, and when I return some days later be able to pull up the GUI once more. Can screen help me here?

Regards, 

Chel

---

### Post by lykwydchykyn on 2008-11-03
You know, I'm sure there is no end of ways you can finagle X11, ssh, screen, and whatever else to do what you're wanting to do; but VNC will do exactly what you're asking if you follow that tutorial I posted.  

With all due respect to everyone else, I'm not really clear why people are steering you away from it.  It's not the best performer by any stretch, but for the features you're wanting it's a good fit.

---

### Post by Chelmet on 2008-11-04
Okay, it seems I maybe *can* do this the way I was trying, but  couldn't figure it out, so I'm going to try lykwydchykyn's wat, VNC. The link you posted requires a few modifications to the login system via gui - I am running headless, can you tell me the CLI way to do the same? The rest of the guide *looks* fairly self explanatory.

Cheers again   :O)

---

### Post by lykwydchykyn on 2008-11-05
If you've already got xming installed (or a Linux workstation), just ssh into the box and run gdmsetup.  The GUI will pop up on your workstation and you can make the changes.

---

