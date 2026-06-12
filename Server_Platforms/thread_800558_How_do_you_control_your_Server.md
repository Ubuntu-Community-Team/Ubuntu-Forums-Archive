---
title: "How do you control your Server?"
date: 2008-05-19
forum: Server Platforms
---

### Post by vorgusa on 2008-05-19
I am sure this has been talked about a lot, but I was just curious how people create their servers.  Being brought up with Windows I am still more familiar with a GUI environment, even though I am getting more used to Command Line.  I was thinking about creating a 8.04 Ubuntu Server setting it up in a GUI and then putting it in an Init runlevel of 3 so that it would have multi-user and networking without the GUI, would this make it just as efficient as installing it without the GUI or would there still be some effect?  

What does everyone else do?

---

### Post by solcott on 2008-05-20
In Ubuntu, runlevels 2-5 are all the same thing so the GUI would start anyway.

If you are used to using a GUI, but want the machine to be a server and have the GUI only run when you want it to what you could do is install Ubuntu from the Server CD (because it will let you set the servers up MUCH more easily during the OS install) and then do...
```
sudo apt-get install sysv-rc-conf ubuntu-desktop
```

That will add the Ubuntu GUI packages onto your server install, and you can use the 'sysv-rc-conf' command to stop 'gdm' from automatically starting on any of the runlevels.

By default, your server would then boot into text mode and you can log in and type 'startx' to start the GUI and the GUI will shut down when you log off.

---

### Post by amingv on 2008-05-20
I use [Webmin]("http://www.webmin.com/") and ssh.

---

### Post by vorgusa on 2008-05-20
Hmm the sysv-rc-conf command sounds intersting would I use a command like sysv-rc-conf level 3 to get it to get out of the GUI mode?  the example I saw online mentioned a specific program like SSH

---

### Post by solcott on 2008-05-20
When you use sysv-rc-conf it gives you a list of all the things that are configured to start at boot, and you press down until you are at gdm and take the check mark out for each runlevel. I'm pretty sure it's space to uncheck things and then q when you are done.  After you do that the GUI will not start unless you are logged in (in text mode) and type startx to start it by hand.

---

### Post by hyper_ch on 2008-05-20
Well, what do you need to control on the server?

---

### Post by windependence on 2008-05-20
ssh and nano for me. Midnight commander (mc) is nice for a file manager in an ssh session also. That's all you need if you are truly gonna use it as a "server" and not a workstation. most of my servers are headless anyway.

-Tim

---

### Post by windependence on 2008-05-20
> **solcott said:**
> In Ubuntu, runlevels 2-5 are all the same thing so the GUI would start anyway.

Are you sure about this? If so this is not standard Linux behavior.

-Tim

---

### Post by MJN on 2008-05-20
> **windependence said:**
> Are you sure about this? If so this is not standard Linux behavior.
 
-Tim
Solcott is right. You can confirm that levels 2-5 are configured equally using either a runlevel manager or manually inspecting the contents of /etc/rc*.d/
 
Note that there is no 'standard Linux behaviour' - each distribution is free to choose its own implementation, particularly with regards to subtleties of operation such as run-level configuration where such granularity between levels is not required in a general-purpose disctribution.
 
In the case of Ubuntu it follows the Debian model and hence is therefore fairly 'standard'.
 
Mathew

---

### Post by Brazen on 2008-05-20
I think you'll find that setting up your services will be done from the command line and text files anyway.  I would suggest connecting in through ssh and use nano to edit the text files.

You can connect through ssh with Putty from a Windows machine.  That's what I use, and it works fantas-great.  I even have it set up to use Pageant to load ssh keys, so I can even use single-signon to all my linux servers (I admin about 20 of them).

---

### Post by cdtech on 2008-05-20
Keep it simple:
No GUI = light weight (no complicated backup's)

ssh for loging into the server and pico to configure the files.

---

### Post by dashnak on 2008-05-20
> **amingv said:**
> I use [Webmin]("http://www.webmin.com/") and ssh.
Me too...

---

### Post by marcog42 on 2008-05-20
I, too, use webmin and ssh/nano.  Mostly ssh/nano.  Webmin comes in handy, since my system is headless, for stuff I have no idea how to configure manually and can't be buggered to read about at the time.

---

### Post by windependence on 2008-05-20
> **MJN said:**
> Solcott is right. You can confirm that levels 2-5 are configured equally using either a runlevel manager or manually inspecting the contents of /etc/rc*.d/
 
Note that there is no 'standard Linux behaviour' - each distribution is free to choose its own implementation, particularly with regards to subtleties of operation such as run-level configuration where such granularity between levels is not required in a general-purpose disctribution.
 
In the case of Ubuntu it follows the Debian model and hence is therefore fairly 'standard'.
 
Mathew

Well it might be standard *Linux* behavior, but certainly not standard Unix behavior. So what is the difference then between runlevel 3 and 5 if the GUI is loaded in 3? And what is the point then?

-Tim

---

### Post by MJN on 2008-05-20
Linux != Unix
 
I'm not sure what you mean by your other question. Can you elaborate? There is no difference between runlevel 3 and 5 in this distribution - the GUI is loaded in levels 2-5, i.e. either and all levels. You are of course free to alter this behaviour as discussed, this is just the out-of-the-box default.
 
Mathew

---

### Post by windependence on 2008-05-20
> **MJN said:**
> Linux != Unix
 
I'm not sure what you mean by your other question. Can you elaborate? There is no difference between runlevel 3 and 5 in this distribution - the GUI is loaded in levels 2-5, i.e. either and all levels. You are of course free to alter this behaviour as discussed, this is just the out-of-the-box default.
 
Mathew

Ay nevermind, I am from the *BSD world now where things are orderly.

I am aware Linux is not Unix. Why would they screw up the normal runlevels this way? I guess there are things I like about the Debian way and things I like about the Red Hat way. This just makes little sense to me. Some of us expect runlevel 3 to be multi-user, no GUI that's all.

-Tim

---

### Post by vorgusa on 2008-05-21
If the run levels are different for each distro why do the init config files say runlevel 3 Multi-user and network and runlevel for say Multi-user, networkin, and Xterm???? shouldn't they adjust the run levels to correct this?

Ohh yeah.. are the runlevels corresponding to the rc1.d rc2.d etc??


btw I have already installed the Server and decided to use Xubuntu since it is small.  I was a little surprised when I told it to install using aptitude that I do not get a full Xubuntu, it is a GUI with a terminal and I can type firefox to bring up a window... I was thinking I would get the system drop down window.. which is what I was hoping for.

The reason I brought up this Topic was because many of the GUI programs can make it easy to change a lot of things I do not know about or are overly complicated.  I am not a Linux Guru, but I still try to mainly use CLI.

---

