---
title: "server, cannot open display"
date: 2013-06-16
forum: Server Platforms
---

### Post by JamesDonaldChilds on 2013-06-16
I have ssh via putty on a windows machine and successfully ssh'ed in, I have been using gedit/gparted successfully all last night and this morning, I was literally just using it a few minutes ago. Out of no where, for no apparent reason when I try to launch gedit I can no longer access it, as it says not not open display.

"xxx@xxx:~$ sudo gedit
'PuTTY X11 proxy: wrong authorisation protocol attemptedPuTTY X11 proxy: wrong authorisation protocol attemptedPuTTY X11 proxy: wrong authorisation protocol attemptedPuTTY X11 proxy: wrong authorisation protocol attemptedCannot open display:
Run 'gedit --help' to see a full list of available command line options."


That is the error spitting out.

I have putty as SSH and Xming as xserver which IS running and was working perfectly earlier.

There is another user ssh'ed in on his own account, but he does not have an xserver on his computer and is not using gui applications. What is the problem?! This is the second time this has happened and I had to reformat the first time because I could not find an answer. Any help appreciated.

EDIT: I solved my issue, thanks everyone for your help. I had a drive mounted to my /home/usr and .Xauthority did not want to set on the disk for some reason, I don't know why but un mounting my drive from my home directory fixed the issue.

---

### Post by SeijiSensei on 2013-06-16
Does this only happen with sudo?  I haven't run X over SSH with putty, but using the normal SSH client with "ssh -X" you will have permission issues if you start the session as an ordinary user but then switch to being the root user with sudo.  The authorization cookie you got as the original user isn't valid for a different user, root in this case.

If you have successfully run X commands with sudo before, then ignore this.  Have you tried connecting from another machine running Linux and using "ssh -X"?  Does that work or not?

---

### Post by JamesDonaldChilds on 2013-06-16
> **SeijiSensei said:**
> Does this only happen with sudo?  I haven't run X over SSH with putty, but using the normal SSH client with "ssh -X" you will have permission issues if you start the session as an ordinary user but then switch to being the root user with sudo.  The authorization cookie you got as the original user isn't valid for a different user, root in this case.

If you have successfully run X commands with sudo before, then ignore this.  Have you tried connecting from another machine running Linux and using "ssh -X"?  Does that work or not?

I have run with sudo before on my user account, this is my error after signing in as su.

"root@xxx:/home/xxx# gparted
PuTTY X11 proxy: wrong authorisation protocol attemptedPuTTY X11 proxy: wrong authorisation protocol attemptedPuTTY X11 proxy: wrong authorisation protocol attemptedPuTTY X11 proxy: wrong authorisation protocol attempted
(gpartedbin:15490): Gtk-WARNING **: cannot open display: localhost:10.0" 

I have only tried this on my user and my user alone other than this last time I ran as su to show this error. I could previously pull up a gui and then, without ending sessions or changing users, couldn't pull up guis. There was no apparent change that would have caused this that I can recall.

---

### Post by houstonbofh on 2013-06-16
Try running an X app as you, not as su'd root.  I am thinking it is a token problem too.

---

### Post by JamesDonaldChilds on 2013-06-16
Hmmm, This is weird, I tried it and it worked perfectly, it wasn't before!! I don't know what is going on here. I appreciate the help. If I have this issue again I will re-post here.

---

### Post by JamesDonaldChilds on 2013-07-03
Ok guys, it is doing it again for NO apparent reason, this is REALLY stressful so if you could assist me with a resolution that will prevent it from happening in the future that would be awesome. So I am ssh'ed in with Putty and xming as xserver, one second I can launch gui apps the next i get this error

"

~$ xhost
PuTTY X11 proxy: wrong authorisation protocol attemptedPuTTY X11 proxy: wrong authorisation protocol attemptedPuTTY X11 proxy: wrong authorisation protocol attemptedPuTTY X11 proxy: wrong authorisation protocol attemptedxhost:  unable to open display "localhost:10.0"

"

What in the world keeps causing this!!

---

