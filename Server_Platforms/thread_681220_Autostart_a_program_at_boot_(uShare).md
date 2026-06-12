---
title: "Autostart a program at boot (uShare)?"
date: 2008-01-28
forum: Server Platforms
---

### Post by Eluzion on 2008-01-28
I have a file server setup with uShare to stream videos off my XBox 360. I was curious how I could go about auto starting uShare at boot?

---

### Post by Eluzion on 2008-01-28
I tried:

sudo update-rc.d ushare defaults

But it says:

 System startup links for /etc/init.d/ushare already exist.

Yet when I start the server, uShare does not automatically start up.

---

### Post by ogi010 on 2008-05-06
I would like to know more about this too.  Not being able to do this really defeats the purpose of ushare for me to a point, I would like to be able to stream stuff from my xubuntu server w/o worrying about firing up my other computer and manually starting ushare.

Ogi

---

### Post by n0kS on 2008-06-07
after this:
sudo update-rc.d ushare defaults

just make this:
sudo chmod +x ushare

bye :)

---

### Post by x20mar on 2008-06-10
Hi I just tried ```
sudo chmod +x ushare
```

and I made sure that everything in ushare.conf was the way I wanted it and restarted the server. But it still won't run unless I have the following command running as someone is logs in:

```
ushare -n linus -c /data -x -i eth0
```

But I won't someone having to log in every time they want to stream stuff from the 360. Any Suggestions?

---

### Post by preedlexco on 2008-06-10
I too am having the same issue.

I can start ushare from terminal using the following:
sudo /etc/init.d/ushare start


Even though all the sny links in correct rc#.d ushare still does not start at boot. 

I have also set the rc#.d links to default by running:
sudo update-rc.d ushare defaults

Strange thing is that other apps that have the same Required-start, I have no issues with.

I've double checked that everything is executable.

Any ideas?

---

### Post by jombeewoof on 2008-07-03
I just tested this and it's 100% guaranteed to work on my setup. ;)

just add
```
#! /bin/bash
ushare &
```

to /etc/rc.local

Runs ushare as root on vty1 directly before login prompt, if you're using a graphical login, you'll never see it unless you ctrl+alt+F1 

If you have various switches for ushare, put them before the &

---

### Post by sroutier on 2008-07-03
Hey guys,

I am having the same problem... uShare works fine. It's even configured with init.d !! But it will not start automatically.... Or rather it will not stay up. I know it starts, becasue I have a PID file in /var/run for uShare but there is no uShare in the process list.... If I start it manually using:
$ sudo /etc/init.d/ushare start it all works. 

I even disabled apparmor, just in case... Still will not stay up... And I can't see anything in /var/log.

What gives ? Any clues... 

Thanks for the help.

---

### Post by jombeewoof on 2008-07-03
I had it working on a previous install, but I wrote a startup script that ran when I logged in. 
To get it to run when you're not logged in you have to run it in rc.local
I don't know why it won't start like it should, but there is an easy way around it.

From what I'm reading, if I get add & to the end of the command it will run in the background.

Just a guess, but I think why it's not working is the service is running, but the program hasn't indexed the shared directory. 
When you run "ushare" all by itself, not even as root it parses the shared directory and displays the total amount of files that are shared, this might have something to do with why it doesn't work running from init.d

Like I said though, that's just a guess.

---

