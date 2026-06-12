---
title: "Launching applications from an SSH session"
date: 2010-03-08
forum: Server Platforms
---

### Post by NCLI on 2010-03-08
Ok, I want to start applications from an SSH connection, and close the connection, without the applications I've started closing with it.

Is this possible?

---

### Post by yogesh.girikumar on 2010-03-08
Hi,

Checkout 'nohup' command.

The syntax is 
```
$ nohup <command> &
```For e.g. 
```
$ nohup sleep 300 &
```will create a delay for 300 seconds. The '&' in the end will put the process to the background. Having a 'nohup'  in the start of the command will make the 'sleep' immune to terminal hangups. 

P.S. The output of the command is not written to the standard output. It's written into a file named nohup.out in the present working directory at the time of running the command.

See the manpage for more info
```
$ man nohup
```

HTH,

---

### Post by noway2 on 2010-03-08
You might also want to check out screen.  Just launch the application you want as screen 'application'.  Then you can disconnect by detaching (CTRL-A d) and log off the SSH connection.  The application will continue to run unimpeded in its own screen.  You can then re-attach at a later time, even from a different location with the command screen -raAd and be right where you left off.

---

### Post by Aurelius on 2010-03-08
Another vote for screen - I start rtorrent and a few other processes in a screen session on my home server and can connect to that session from any ssh connection.

You can also use the following commands if you forgot to detach from the screen session on another computer:

screen -D -RR: force a detach if possible and connect
screen -r -x: attach to an active session from another machine.

---

### Post by NCLI on 2010-03-09
Thanks a lot for your suggestions :D 

This fills the final hole in my knowledge I felt needed filling before I migrate my server from Ubuntu Desktop to Server.

---

### Post by tlsarles on 2010-03-09
Screen is a good option if you want to be able to reconnect your SSH session later and pick up where you left off.

However, if you truly just want to run a service, and put it in the background to run forever without being touched again, simple put a & at the end; 'example-command &'

---

### Post by Agent ME on 2010-03-09
> **tlsarles said:**
> However, if you truly just want to run a service, and put it in the background to run forever without being touched again, simple put a & at the end; 'example-command &'
That will quit when you log out. 'nohup example-command &' would let it keep going even if you log out.

---

### Post by Mr.Kappa on 2010-10-27
Guys it doesn't work for me. I fireup transmission via SSH on my home server but when i close my terminal transmission gets killed (i know it for sure because i check with the web client!).
Neither screen nor the nohup commands seem to work for me :(

What am i doing wrong:confused:

---

### Post by CharlesA on 2010-10-27
Are you launching a graphical app or a CLI app?

If you are launching a CLI app, using screen and then detaching with Ctrl+A+D then closing the ssh session should prevent it from terminating the application.

---

### Post by yesrno on 2010-10-27
Another vote for screen here. What I do when I for example want to download a torrent from ssh without the download progress stop when I close ssh:
 
Ssh to the remote server.
Enter the command 'screen'. some text will pop-up. press enter. (you now already opend a screen session).
Enter the download command.
Just exit the terminal/putty or whatever you use to ssh in.
 
This is basicly it. If you want to test it you can ssh back in again, and give the command 'screen -ls' which will give you the open screen sessions. and 'screen -r <session number>' to resume it.

---

### Post by CharlesA on 2010-10-27
***screen -R*** will restore the newest session, which saves some typing if there are multiple sessions.

---

### Post by Mr.Kappa on 2010-11-05
Thanks guys! That seems to work now :guitar:

---

