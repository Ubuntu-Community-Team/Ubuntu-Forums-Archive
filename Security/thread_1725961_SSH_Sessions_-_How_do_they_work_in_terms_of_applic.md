---
title: "SSH Sessions - How do they work in terms of applications?"
date: 2011-04-10
forum: Security
---

### Post by own3mall on 2011-04-10
I've been using SSH for a long time to remotely access my machine, but I don't understand how SSH sessions work in terms of the programs that run under these sessions.  

For example, I don't understand why the programs I launch under an SSH session are terminated if I terminate the session.  Why don't they continue to run?  The ultimate session runs on the local machine, correct?  So, each time I create a new SSH session, why are my startup programs relaunched?  Wouldn't that create multiple instances of several programs?  I run a webserver on my Ubuntu machine, and it doesn't seem to be affected by sessions.  If I terminate the session it is still running, but my wine program does not continue to run.  Why is that?

Right now, I've set up my Ubuntu machine to run a wine program called Autokick as a Startup application.  When I start a session, it loads and runs.  However, if I close that session, it no longer runs.  By adding a program to the startup applications, it loads when the actual local computer boots, correct?  Thus, if I were to have Autokick run from the session that is created once the local machine loads Ubuntu, would Autokick continue to run even when I create new sessions over SSH?  

I'm so confused.  Please help me understand this better.  :confused:   I just don't know how apache can run all the time despite sessions, but a wine program cannot.

Is there no way to use SSH to login to the current session running on the local machine?  I don't want to keep creating sessions, if it launches programs every time a session is created.

I use NoMachine on Ubuntu 10.04

---

### Post by bodhi.zazen on 2011-04-10
When yo ussh in, you start a new session, a shell, bash.

Bash is the parent to all the process you then start, which are termed children.

If you close the parent, you then kill the children.

Daemons, such as apache, run in the back ground, not associated with a bash parent (the parent process varies with distro).

You use one of several tools :

nohup
dtach
screen

Those apps will dissociate any process you start from your session, or in the case of dtach and screen, you continue to run the session in the background.

---

### Post by own3mall on 2011-04-11
Thanks for the helpful information bodhi.zazen.  It's making more sense to me now.

Is there a way I can configure the program to run as a daemon?  nohup doesn't seem to work. Or better yet, is there a way I can make the application launch only after the computer boots up Ubuntu which logs into my account and not have it launch during created sessions?

---

### Post by BkkBonanza on 2011-04-11
You can start a program "detached" at the console by appending an & at the end of the command.

eg.
**myprog -a options -b etc &**

It will be started and run in the background, so you get the console back immediately. You can see it is running with **ps afx** and it will run until manually stopped using kill (or a reboot).


You can have a program start as daemon at boot by adding a conf file for it to /etc/init. There are others in that directory you can browse as examples. They're quite simple and in a simple case just set conditions for starting and then the program to start.

See tty1.conf as example. It's conf starts on certain runlevels, has respawn enabled (so it will get monitored and started again if it dies), and then a simple exec to start the program. You can set more specific conditions too, such as only starting after another program is up, or the network is up etc.

I'm suggesting this method for you as it's more robust than adding your program to /etc/rc.local (which also works), and more future proof than /etc/init.d/ scripts.

---

### Post by bodhi.zazen on 2011-04-11
> **own3mall said:**
> Thanks for the helpful information bodhi.zazen.  It's making more sense to me now.

Is there a way I can configure the program to run as a daemon?  nohup doesn't seem to work. Or better yet, is there a way I can make the application launch only after the computer boots up Ubuntu which logs into my account and not have it launch during created sessions?

What program is it you want to run and what problem did you have with nohup ? Is it a graphical program ?

& puts the program in the background, but does not allow you to close your terminal or log out of ssh and keep the program running.

screen may be your best option.

---

### Post by BkkBonanza on 2011-04-11
> **bodhi.zazen said:**
> but does not allow you to close your terminal or log out of ssh and keep the program running.


It does. The process gets detached and owned by init when you logout. I wasn't sure when you said that so I did a test here to confirm. I can logout/login again after and it stills runs and is owned by init.

---

### Post by own3mall on 2011-04-11
Thanks BkkBonanza,

I'll give it a try!

---

### Post by own3mall on 2011-04-11
I tried creating a script for Autokick, but it didn't run.

Here's what I originally had as the startup entry:

```

nohup wine "c:\program files\Autokick\Autokick.exe" /a

```

Here's the script I created in the /etc/init folder:

```

# Autokick
#
# This service scans the -*B[w]*- MOHAA Server
# and makes sure banned clients cannot connect

description    "Crowfoot's Autokick Scanner"

start on stopped rc RUNLEVEL=[2345]
stop on runlevel [!2345]

respawn
exec wine "c:\program files\Autokick\Autokick.exe" /a

```

Any idea why the /etc/init script does not work, but the start-up entry does?

---

### Post by bodhi.zazen on 2011-04-11
> **BkkBonanza said:**
> It does. The process gets detached and owned by init when you logout. I wasn't sure when you said that so I did a test here to confirm. I can logout/login again after and it stills runs and is owned by init.

I have not tried it in a while, but last I looked & is not sufficient.

Open a terminal

Run xeyes or firefox with &

close the terminal and xeyes or firefox will close.

It may well depend on the application mind you.

@ own3mall: does that command work in a terminal ? the /a looks suspect.

I would try :

(nohup 'wine "c:\program files\Autokick\Autokick.exe" /a')&

In a subshell with the &

You may need to use the full path to wine (/bin/wine or what have you).

Is autokick a graphical program ? Is there no Linux native solution to running autokick in wine ?

---

### Post by own3mall on 2011-04-11
It is a graphical program.  The /a flag makes it start scanning once Autokick is launched.  

If it's not possible to run a graphical program as a daemon, is it possible to have it start up only on the local machine's default session and not on the SSH sessions?

---

### Post by BkkBonanza on 2011-04-11
Once you have the init conf file you can try a manual start with,

service <confname> start

and perhaps that will provide some feedback message. I'm not familiar how wine behaves when run with "exec" but there may be some issue with that. It may be that the whole line including wine needs to be quoted,

exec 'wine "c:\program files\Autokick\Autokick.exe" /a'

but that's just a guess. It may need to be "embedded" in a script. ie. exec calls bash with a script name and the script does the wine command. Just things I might try if I were doing this.

Edit: if it's a gui app you may need a condition that ensures the gui has started before it runs.

---

### Post by BkkBonanza on 2011-04-11
> **bodhi.zazen said:**
> 
Run xeyes or firefox with &

close the terminal and xeyes or firefox will close.

It may well depend on the application mind you.


It seems to depend on how you close the terminal. I just tried it with gnome-sudoku. When closed with the mouse [X] button the game ended. When typed "exit" to close the game continued. I'd guess then maybe the normal exit process takes care of detaching. It's a bit surprising to me that clicking [X] doesn't end the terminal the same as exiting. Odd.

---

### Post by own3mall on 2011-04-11
I'll try some things later tonight, and I'll get back to you.  Thanks for the help so far!  :KS

---

### Post by bodhi.zazen on 2011-04-11
If it is a graphical application, then the easiest method would be to add it to autostart when you log in. You then need to leave the user logged in , but you can "switch user" to bring you back to the log in screen so others may use the system or lock the screen.

---

### Post by bodhi.zazen on 2011-04-11
> **BkkBonanza said:**
> It seems to depend on how you close the terminal. I just tried it with gnome-sudoku. When closed with the mouse [X] button the game ended. When typed "exit" to close the game continued. I'd guess then maybe the normal exit process takes care of detaching. It's a bit surprising to me that clicking [X] doesn't end the terminal the same as exiting. Odd.

Interesting, I will take a look at it, thank you for the update.

---

### Post by own3mall on 2011-04-11
Here's what I'm getting:

```

eric@eric-desktop:~$ service Autokick.conf start
Autokick.conf: unrecognized service
eric@eric-desktop:~$ service Autokick.conf start
Autokick.conf: unrecognized service
eric@eric-desktop:~$ service Autokick.conf start
Autokick.conf: unrecognized service
eric@eric-desktop:~$ sudo service Autokick.conf start
[sudo] password
Autokick.conf: unrecognized service
eric@eric-desktop:~$ 

```

Autokick.conf now contains:

```

description    "Crowfoot's Autokick Scanner"

start on stopped rc RUNLEVEL=[2345]
stop on runlevel [!2345]

respawn
exec /home/eric/Scripts/Autokick.sh

```

autokick.sh

```

#!/bin/bash

wine "c:\program files\Autokick\Autokick.exe" /a

```

Why is it an unrecognized service?

---

### Post by bodhi.zazen on 2011-04-11
service Autokick start

See also: [http://upstart.ubuntu.com/getting-started.html](http://upstart.ubuntu.com/getting-started.html)

Your upstart script is very basic and I am not sure it will work.

---

### Post by own3mall on 2011-04-11
```


Autokick start/running, process 5588
eric@eric-desktop:~$ 


```
And it shows up as running:

```

root      5473     1  0 19:12 pts/1    00:00:00 leafpad /etc/init/Autokick.conf
eric      5505     1  0 19:30 ?        00:00:00 leafpad /home/eric/Scripts/Autokick.sh
eric      5629  5397  0 20:49 pts/2    00:00:00 grep --color=auto Autokick
eric@eric-desktop:~$ 


```But it's not running, or it's not running properly, and I'm not getting any output.  Also, Autokick.sh is working when I run it.

Although, it also said this when I tried to stop it:

```

eric@eric-desktop:~$ service Autokick stop
stop: Unknown instance: 

```

---

### Post by bodhi.zazen on 2011-04-11
Well, it needs to run in X , no ?

So you are going about this the wrong way and your init script is incomplete.

You need to add that command to autostart, so it starts when you log in.

You then keep your user logged in, use switch user to share the computer with others or lock the screen when you leave.

Also, as I asked before, is there not a linux equivalent or do you need to use wine ?

---

### Post by own3mall on 2011-04-11
> **bodhi.zazen said:**
> Well, it needs to run in X , no ?

So you are going about this the wrong way and your init script is incomplete.

You need to add that command to autostart, so it starts when you log in.

You then keep your user logged in, use switch user to share the computer with others or lock the screen when you leave.

Also, as I asked before, is there not a linux equivalent or do you need to use wine ?

Crow King's Autokick is a Windows only program.  I would normally run it on a Windows machine, but since my web server runs Ubuntu, I figured if I could get it to work, that would be the best in terms of energy usage.  I have it running, but now I need to get it to launch properly and run correctly in the manner that I want it to run.

The /a flag goes with the Wine command, as the executable must be started with the /a flag so that it begins scanning automatically.  

This works:

```

#!/bin/bash

wine "c:\program files\Autokick\Autokick.exe" "/a"

```

This works:

```

#!/bin/bash

wine "c:\program files\Autokick\Autokick.exe" /a

```

This doesn't work:

```

#!/bin/bash

'wine "c:\program files\Autokick\Autokick.exe" /a'

```

How do I add the X flag as a linux flag instead of appending it to the Windows command?

---

### Post by BkkBonanza on 2011-04-12
I think if wine depends on having certain gui components running then you would need a condition in the conf that only starts wine (and your app) after those. You might try a condition like,

start on started gdm

rather than "start on runlevel...". This will make sure gdm is started first and delay the autokick start until later in the init process. 

Another thing is whether autokick depends on some data files. If it is started from init as root it may not behave the same as when started from home as "user". You might try adding a few setup steps, and run as your user, to your script, eg.

cd /home/eric
sudo -u eric wine "c:\program files\Autokick\Autokick.exe" /a

Typically on linux daemons are designed for that purpose so running "regular" apps as daemon may not work correctly due to issues like this. It's safer for you not to run it as root anyway. Often a daemon app will start as root but then change the user it runs as to avoid being root if compromised.

As for the instance not being recognized it may be due to your script not backgrounding itself and so holding up upstart which doesn't see it complete successfully. You may try adding **&** to the wine cmd in your script so it backgrounds and the script ends. But if you do then be sure to also add,

expect fork

just above the respawn in your conf file. You may to remove the respawn line as it may decide your "service" ended and needs to be started again - causing many instances to be started.

---

### Post by own3mall on 2011-04-12
> **BkkBonanza said:**
> I think if wine depends on having certain gui components running then you would need a condition in the conf that only starts wine (and your app) after those. You might try a condition like,

start on started gdm

rather than "start on runlevel...". This will make sure gdm is started first and delay the autokick start until later in the init process. 

Another thing is whether autokick depends on some data files. If it is started from init as root it may not behave the same as when started from home as "user". You might try adding a few setup steps, and run as your user, to your script, eg.

cd /home/eric
sudo -u eric wine "c:\program files\Autokick\Autokick.exe" /a

Typically on linux daemons are designed for that purpose so running "regular" apps as daemon may not work correctly due to issues like this. It's safer for you not to run it as root anyway. Often a daemon app will start as root but then change the user it runs as to avoid being root if compromised.

As for the instance not being recognized it may be due to your script not backgrounding itself and so holding up upstart which doesn't see it complete successfully. You may try adding **&** to the wine cmd in your script so it backgrounds and the script ends. But if you do then be sure to also add,

expect fork

just above the respawn in your conf file. You may to remove the respawn line as it may decide your "service" ended and needs to be started again - causing many instances to be started.


I created the following alias and put it in the ~/.bash_profile file[FONT=&quot]

```

alias autokick_launch='wine "/home/eric/.wine/drive_c/Program Files/Autokick/Autokick.exe" "/a"'

```[/FONT]Autokick.sh now contains[FONT=&quot]

```

#!/bin/bash
autokick_launch /x &

```[/FONT]

Which still interferes in the flag of the wine program, as it doesn't start scanning automatically if any other flags are used in the command.  

I'm still an Ubuntu n00b, so I'm not exactly sure what to do.  
[FONT=&quot]
[/FONT]Autokick.conf:[FONT=&quot]

```

description    "Crowfoot's Autokick Scanner"

start on started gdm

expect fork
respawn
exec /home/eric/Scripts/Autokick.sh

```[/FONT]Does that look right?[FONT=&quot]

[/FONT]Also, it does not run as root.  It runs as eric.  I'm the only user of the ubuntu machine, and it auto logs me in.  [FONT=&quot]
[/FONT]

---

### Post by BkkBonanza on 2011-04-12
If you are set up to auto login under your name then the easiest solution is wwhat bodi.zazen suggested. From the gui try adding your wine command as autostart in the **System, Preferences, Startup Applications** menu item. This more closely mimics a regular user running of the program and will be much simpler than trying to use an init/service method. 

I had suggested the service idea because I assumed you didn't want to login each time during boot just to start the app, but given you already do that it makes a lot more sense use take the simplest route.

You mentioned that it doesn't run as root but in fact all init conf get processed and run as root before you even have a gui desktop and before you get logged in. The init system happens right at system boot and your desktop login (under gdm) happens as part of the init but much later in the sequence. Your last conf file looks fine but respawn may cause grief. This will wait for gdm to be up before trying to run autokick but that point is still before you are logged in as user eric.

The startup app method as suggested by bodi.zazen happens after user desktop login (not at boot) and so the app does get run as eric. The issue being that if you don't get logged in then the autokick isn't run.

Aside: If you run **ps afux** at the console it will show which process owns which (via tree layout) and what user your script ends up running as.

---

### Post by own3mall on 2011-04-12
Right, but since I use SSH on a regular basis, every time I log in via SSH, it creates a new session and the autokick is launched again when it is already running.  I just want it to run once or not be triggered to run at all when I SSH in.  I just want it to run under eric, and not run when I login via SSH.

---

### Post by bodhi.zazen on 2011-04-12
ssh in as a second user (easy solution perhaps).

---

### Post by own3mall on 2011-04-12
Could I write a script that I add to startup programs that won't launch if there's an SSH session but will launch for users?

---

### Post by BkkBonanza on 2011-04-12
Yes. You should be able to do that. When you ssh an env variable SSH_CLIENT is set.
You could check for that with,

```

if [ -z "$SSH_CLIENT" ]; then
  do the right stuff
fi
```

(-z test is true if SSH_CLIENT is null/uninitialized)

---

### Post by own3mall on 2011-04-13
> **BkkBonanza said:**
> Yes. You should be able to do that. When you ssh an env variable SSH_CLIENT is set.
You could check for that with,

```

if [ -z "$SSH_CLIENT" ]; then
  do the right stuff
fi
```(-z test is true if SSH_CLIENT is null/uninitialized)

Works perfectly.  Thanks so much for the help.  Startup script it is with the -z test!

I will probably reference this thread in the future, as it contains a lot of good information.  Thanks BkkBonanza and bodhi.zazen!

:)

---

### Post by EJeanmaire on 2011-04-13
Maybe I read over this too quickly but what if you just add the line to /etc/rc.local

---

