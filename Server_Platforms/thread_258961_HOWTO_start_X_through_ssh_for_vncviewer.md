---
title: "HOWTO: start X through ssh for vncviewer?"
date: 2006-09-16
forum: Server Platforms
---

### Post by utdjohn on 2006-09-16
Hey all,

I want to run a headless server (S1) and generally will only connect via ssh from my laptop (S2) to utilize S1.  However, I want the option of firing up the Xserver and connecting to S1 through VNC.

Right now, I still have a keyboard, mouse, monitor on S1.  Therefore, I can start X locally.  Then, on S2 I can use vncviewer to connect to the X session. (this works because of course I've enabled remote desktop options).

My problem is that I want to be able to start X on S1 without being locally connected (because soon I would remove the keyboard, monitor etc.).  But I am not able to do this successfully.  I'd think I could just ssh into S1, then run "sudo startx".  This appears to work (of course I don't see anything but loggin messages).  But then when I try to run vncviewer, it says "connection refused" and "unable to connect" as if the server has not started.  It seems like it is almost working, except the X session I am starting through ssh isn't quite doing the job.

How can I remotely fire up X in such a way that I can then connect with vncviewer?

Below I put the information it shows when I run X just for version info.  I also get some warnings and errors but these are typical, even when I run it locally.  The only message which I don't typically see is the one about "creating new authority file", but it doesn't seem to be complaining about anything... No errors, but I can't VNC in.

thanks!
john

> john@bauer:~$ sudo startx
xauth:  creating new authority file /home/john/.serverauth.4957

X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 i686
Current Operating System: Linux bauer 2.6.15-26-386 #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006 i686
Build Date: 16 March 2006
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
...
(messages that I always get)


---

### Post by bernied on 2006-09-16
You need to serve up vnc from S1, for this you don't start X exactly, in fact I don't think you even need to have X installed. I confess I don't understand this properly, even though I use vnc. My general idea of this is that the vnc server acts like X, but not the same (X uses UDP, vnc does not).

You need to have a vnc server installed on S1, get it configured, then start it up. Then you open vncviewer on S2.

Back in a sec with some details...

---

### Post by bernied on 2006-09-16
The package you probably want is x11vnc.
The config file is probably /etc/vnc.conf
You may not have to change it much for a workable install.

(I say probably because my server is a gentoo system)

---

### Post by bernied on 2006-09-16
You usually start the vnc server with the 'vncserver' application, which calls x11vnc. For more details see 'man vncserver' or google.

---

### Post by utdjohn on 2006-09-16
Well, I am thinking that I *do* want X though... I want to have access to the same normal desktop that I'm used to seeing when I use X normally (ubuntu/gnome).  Will I see this through a vncserver when not running X?  In other words, the reason I might want to have this access is if I want to use some of the "easy to use" tools, such as the menus under System/Administration, or maybe the graphical package managers, etc.  So if I can access all of that by simply running the vncserver, then it would be a good solution for me.

As it is, everything would be "perfect" if I could just get X started up remotely... Any ideas on why that didn't work for me?

thanks!

---

### Post by bernied on 2006-09-16
vncserver will give you exactly what you are asking for - it will be your X desktop. It's just possible that it is already installed, as it may be what the remote desktop stuff uses to transmit vnc.

I've never used the remote desktop stuff before, so I don't know why it doesn't work when you fire up you X session remotely. Maybe it is upset when it can't find a local screen.

Look for clues in the log files on S1 - look in the /var/log/ directory. The first file to look at is 'messages'.

---

### Post by bernied on 2006-09-16
Does remote desktop normally ask the local user for permission before allowing a remote vnc connection? Or have you set it up to always allow a connection? - my understanding is that this would not be very secure.

---

### Post by bernied on 2006-09-16
You might have vino installed - it comes up in my package manager as the vnc server for gnome.

---

### Post by bernied on 2006-09-16
Maybe vnc4server is the right package for you - it's in the universe repository.

---

### Post by utdjohn on 2006-09-16
Bernied,

Great -- I just did an apt-get on "vncserver", and was able to run that and get the desired effect!  Just like you said, I get my normal gnome desktop.

In case anyone else is reading this, I also got a nicer display like this:
vncserver -geometry 1024x768 -depth 24
Then, I put this command in a script called "start-vncserver", and put it in my /etc/init.d directory, and used "rcconf" to add this service to my current runlevel configuration.  Except this doesn't quite yet work... when I booted up, this service didn't seem to have been run.  And I haven't yet figured out why. (anyone know offhand?)

Thanks for encouraging me in that direction Bernied.

John

---

### Post by utdjohn on 2006-09-16
Oh, to add to that, I can see that it has been run:
ps -aux | grep vnc yields:
root      4072  0.0  0.4   4256  2528 ?        S    17:44   0:00 /usr/bin/perl /usr/bin/vncserver -geometry 1024x768 -depth 24 :1

But what it looks like when I normally run it is:
john      4112  1.1  0.5   5240  2976 pts/0    S    17:46   0:00 Xrealvnc :1 -desktop X -auth /home/john/.Xauthority -rfbwait 120000 -rfbauth /home/john/.vnc/passwd -rfbport 5901 -fp /usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType -co /usr/X11R6/lib/X11/rgb

Clearly my method of running it isn't getting through somehow.

Ok I will try to capture logs by redirecting it... and see if there are some errors.

---

### Post by bernied on 2006-09-16
If you set this script up the way you did, it will run as root, as you can see from the ps | grep. but your X server is probably configured to not accept root logins, so probably won't start from a root command. This can be changed but is probably not a good idea, and probably not what you want. 

If you do insist on running the vnc server at startup, you need to tell your script to run as john, but I don't know how to do that. If you're googling look for 'set uid' or similar. It's really not necessary if the server is staying on as you can leave the vnc session running and come back to it anyway.

I also recommend tunneling through ssh (just tunnel port 5901 if you're using the default) if you're going to use this away from home. But if you are opening up your ssh to the wider world, be sure you have a good password or, even better, public/private key security. 
(especially if your user is john - hope your password isn't smith)

---

### Post by bernied on 2006-09-16
And (because I like vnc so much and like having access away from home) the best thing about vnc and ssh is that you can run them both from windows machines. The ssh for windows is called PuTTY and I recommend TightVNC as a vncviewer for windows. But check out tunneling and tighten your ssh security (you will get loads of attempts to break in) before you do this away from home, you don't want an open vnc connection out in the real world. And remember that you will be limited by the upload speed on your internet connection.

---

### Post by utdjohn on 2006-09-16
Bernied, you were precisely correct.  When I echoed the program output, I could see that vncserver didn't know where the password file was, and when I echoed $HOME, which it needs, it was "".  Now I added a HOME=/home/john, and it can now find the password file, and works correctly!

---

### Post by utdjohn on 2006-09-16
I do see one thing that is not quite what I desired with this setup -- that is, I am limited in my options in the menus.  When I pull down System/Admin, I only have 5 choices.  I can't do other stuff such as add/remove software too.  I take it that my options are limited b/c of vnc, but is there anyway to fix this?  It looks like maybe I'm not able to do anything which would require su access.

---

### Post by bernied on 2006-09-16
This last thing is news to me - you should be able to run stuff as root inside vnc. I'm not familiar with gnome but if you can find the name of any of the applications that are missing try something like:
gksudo app &
where app is the name of the application (I think gksudo is the graphical sudo in gnome).

---

### Post by utdjohn on 2006-09-16
Ok, the problem wasn't that I didn't have privledges, but that I had too many (sorta).  I was running the vncserver as root which was a bad thing.  

So I thought I could fix this by changing the "HOME=.." to "sudo -u john vncserver ..".  However, apparently doing a "sudo" to john doesn't set the HOME either (which surprises me), so I have to do both of these things.  Now it seems to be fully working...

---

### Post by motin on 2006-10-08
I didn't read it all, but appropriate guides would be:

HOWTO: Set up VNC server with resumable sessions - [http://ubuntuforums.org/showthread.php?t=191564](http://ubuntuforums.org/showthread.php?t=191564)

OR 

HOWTO: FreeNX on Dapper LTS 6.06 - [http://ubuntuforums.org/showthread.php?t=241651&highlight=freenx+howto](http://ubuntuforums.org/showthread.php?t=241651&highlight=freenx+howto)

FreeNX is probably what you want.

---

### Post by luckylucky on 2006-10-11
I don't know you particular needs, but maybe this will help...

Do X forwarding through ssh.  I have a headless server at home (I unplugged monitor & keyboard, just a stand alone box now) and if I want to access some application via GUI then I log into the server with X forwarding, then call up the app I want to work with and then it looks like it is running on my local computer, but in fact it is running on the remote server.

I wrote a bit of a "how to" here:
[http://ubuntuforums.org/showthread.php?t=257074](http://ubuntuforums.org/showthread.php?t=257074)

In short, to do X forwarding ssh into your S1 computer with the "-X" flag (note "X" is capitolized)
ssh -X user@your-IP-or-FQD

then if, for example, you want to run FireFox then type:
firefox
and you'll get your browser appear as though it is local, but it is actually running from your remote computer, just displayed on your local screen.

if you want to run nautilus to explore the files on your computer then type:
nautilus

I believe you can even run krdc this way too, though not so sure about krfb.  

Bottom line is you can run virtually any GUI program from your remote machine achieving pretty much the same effect as running VNC, however it is far more secure, and in some ways easier to do.

**[SIZE="5"][COLOR="Red"]BIG TIP:[/COLOR][/SIZE]**

Here is a cool tip...

A way to accomplish VNC like use through ssh, but even running your full desktop then do the following:

When you boot up your laptop in Ubuntu, at the login screen don't log in.  Select to go into terminal shell mode.

Then log into your remote with the -X flag:
ssh -X user@your-IP-or-FQD

Then type:
gnome-session

After a few seconds the remote computer's gnome desktop will appear, and it behaves like a local desktop session, but infact it is from the remote machine (evidenced by the fact that it acts a bit slower).

Hope these solutions have you some alternate ways to access your other computer.  BTW, IMHO, for many purposes this is better than VNC for working on the remote machine (again, depending on what you're trying to do).

P.S.  Obviously you'll need to install openssh on the remote machine, and configure your firewall(s) to allow port 22 to that machine (or better yet, a different non-standard port for extra security).

---

### Post by prasopsuk on 2008-06-29
Thank so all. it's working.
i want to copy file from remote and paste to local drive,but i can't.
how to do?
thank you.

---

### Post by slowtrain on 2008-07-17
Just a comment on LuckyLucky's recommendation to use ssh -X:  I've tried both that and VNC and found that VNC is much faster.  Not sure why that would be.  Perhaps there's some way to speed up ssh -X?  (Actually, I'm using ssh -Y, but that should be even faster than -X)

---

