---
title: "Launching a gui program on a remote computer"
date: 2010-08-14
forum: Server Platforms
---

### Post by hellocatfood on 2010-08-14
Is it possible to use ssh to launch a program and it's gui on a remote computer? I've tried connecting with ssh -X computer@ipaddress but when I launch gedit it loads on the local computer

---

### Post by HermanAB on 2010-08-14
Hmm, it is certainly possible, but how???

I think that after launching the program, you need to tell X to use a different screen number, but that is something I haven't done in many a year.

---

### Post by hellocatfood on 2010-08-14
It's ok, someone on Twitter helped me a lot
```
ssh foo@bar -t "xhost +; export DISPLAY=:0; command"
```
The only problem is that the connection gets closed once the program is closed, so you essentially would need to open a connection for each program

---

### Post by eric_1982 on 2010-08-14
I have done it in the past with the root user and X while enabling compression. For example if I wanted get around a restricted site at work I could call firefox from my home computer and then it would use my home itnernet. 

**ssh -X -C root@ip_address_here FireFox**

(replace ip_address_here with your ip address or DNS name)





[http://mixeduperic.com](http://mixeduperic.com)

---

### Post by Bachstelze on 2010-08-14
> **hellocatfood said:**
> Is it possible to use ssh to launch a program and it's gui on a remote computer? I've tried connecting with ssh -X computer@ipaddress but when I launch gedit it loads on the local computer

I'm pretty sure when you do ssh -X and open a graphical app, it is running on the remote host (of course it will appear on the local host's dsktop, that's the whole point of the maneuver). Try to write something and save the file, I'm pretty sure you will see it whan you do a ls on your SSH session.

---

### Post by eric_1982 on 2010-08-14
Yes, your right. I missed read the question, my bad.

---

### Post by bodhi.zazen on 2010-08-15
> **hellocatfood said:**
> It's ok, someone on Twitter helped me a lot
```
ssh foo@bar -t "xhost +; export DISPLAY=:0; command"
```
The only problem is that the connection gets closed once the program is closed, so you essentially would need to open a connection for each program

ssh in, set xhost , set the DISPLAY to :0 

Then when your start you program, either use screen, nohup, or dtach.

Example:

```
nohup command &
```

See man screen and man dtach for details.

---

### Post by HermanAB on 2010-08-15
From the ssh man page:
```
-f      Requests ssh to go to background just before command execution.  This
             is useful if ssh is going to ask for passwords or passphrases, but the
             user wants it in the background.  This implies -n.  The recommended way
             to start X11 programs at a remote site is with something like ssh -f
             host xterm.

             If the ExitOnForwardFailure configuration option is set to “yes”, then
             a client started with -f will wait for all remote port forwards to be
             successfully established before placing itself in the background.

```

---

### Post by kat_ams on 2011-05-07
> **bodhi.zazen said:**
> ssh in, set xhost , set the DISPLAY to :0 

Then when your start you program, either use screen, nohup, or dtach.

Example:

```
nohup command &
```

See man screen and man dtach for details.

Thank you Bodhi.zazen for this instruction.

As this instruction is not very clear for normal everyday (power) users here is line by line how to perform what bodhi.zazen is explaining.:
```

kat@tabbycat:~$ **ssh *kevin@linus***     # log in via ssh to the users account
kevin@linus:~$ **export DISPLAY=:0**           # use the remote display
kevin@linus:~$ **xhost**                       # set xhost
access control enabled, only authorized clients can connect
SI:localuser:kevin
SI:localuser:gdm
SI:localuser:root
kevin@linus:~$ **nohup *minecraft1uur.sh* &**    #start the program *(minecraft limited to 1 hour)*
[1] 4387
kevin@linus:~$ nohup: input will be ignored and output added to &#8216;nohup.out&#8217;
kevin@linus:~$**CTRL+D**                       #end the ssh session
kevin@linus:~$ logged out
Connection to linus closed.

```

Also I didn't find manuals for screen nor for dtach, and the manual for nohup is very cryptic and gives very little clue as to why it works in this situation.

This method is very good for starting a program that a normal user is not allowed to start on their own. Enjoy and have a great day.

---

### Post by bodhi.zazen on 2011-05-08
Nice post with additional information.

Sorry if my instructions were a bit cryptic, glad you got it sorted.

---

### Post by kat_ams on 2011-05-10
I brought it down to one line although I couldn't get the ssh -t part to work. so I still had to ssh in causing two steps.

```
kat@tabbycat:~$ ssh kevin@linus
Password:
kevin@linus:~$ export DISPLAY=:0; xhost; nohup mc/minecraft1uur.sh &
```

---

