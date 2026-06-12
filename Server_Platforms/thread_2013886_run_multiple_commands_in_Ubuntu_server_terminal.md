---
title: "run multiple commands in Ubuntu server terminal"
date: 2012-07-01
forum: Server Platforms
---

### Post by terminal27 on 2012-07-01
I am using Ubuntu server for running avserver (ffmpeg) and stream after booting. But I can't figure out how to make both run automatically (either boot time or later).
command "avserver" needs to run first, and then avconv -f .........
I tried with bash scripts. Having both at the same scripts but avserver won't return the command line so avconv will be never executed (I used $(....);$(....). I tried with screens: 
"screen -dmS AVserver avserver" and
"screen -dmS AVconv avconv -f alsa-i................" and not luck
Then I tried them in different scripts at boot time with 
"sudo update-rc.d avserver defaults"
"sudo update-rc.d bash './myscript.sh' defaults"
and setting them with different start/stops such as
"sudo update-rc.d avserver start 20 2 3 4 5 . stop 80 0 1 6."
"sudo update-rc.d bash 'myscript.sh' start 30 2 3 4 5 . stop 70 0 1 6."
but not luck...
Can anyone give me more ideas? I am running out (I am new to this)
Thank you in advance.

---

### Post by computerfox on 2012-07-01
If you are referring to running multiple commands in 1 line, you would simply use a semicolon ( ; ) to separate all your commands

If you're talking about boot up, I assume you would need to add them to your startup section

What is it exactly that you are trying to accomplish?

---

### Post by terminal27 on 2012-07-01
OK, let me make my question more simple:
I want to start "avserver" at runtime and start a script (called 'myscript.sh' with a sh command such as 'avconv -f alsa -i ...blablabla...') after avserver. Both at boot time on a Ubuntu server without user intervention or loging on the server or writing the command line.
I tried different methods and didn't work. 
First time I try to do a service start up a t boot. I use a script 'runAll.sh' with:
 
#!/bin/bash
echo Starting server and streaming
sh $HOME/runMyserver.sh & $/myScript.sh &
 
But doesn't work.

---

### Post by terminal27 on 2012-07-01
sorry should say my last message:
 
sh $HOME/avserver & $HOME/myScript.sh &

---

### Post by codemaniac on 2012-07-01
> **terminal27 said:**
> sorry should say my last message:
 
sh $HOME/avserver & $HOME/myScript.sh &

In order to run both scripts at one go you need to use **&&** .

```
sh $HOME/avserver && sh $HOME/myScript.sh
```

---

### Post by computerfox on 2012-07-01
> **codemaniac said:**
> In order to run both scripts at one go you need to use **&&** .

```
sh $HOME/avserver && sh $HOME/myScript.sh
```


@OP-Okay, so you are asking what I think you're asking...

@maniac-I never tried running more than one command in bash, but wouldn't it be easier with the semicolon or it's a must to do that?

---

### Post by SeijiSensei on 2012-07-02
Put the commands in /etc/rc.local.  It's the last script that runs at boot time.  You'll need to use sudo to edit the file since it is owned by root.

---

### Post by spynappels on 2012-07-02
> **codemaniac said:**
> In order to run both scripts at one go you need to use **&&** .



Actually, that will run the second command if, and only if, the first completes correctly. As I understand it, the OP wants both to run concurrently.

Either do what SeijiSensei said, or if you want to run it manually, nohup and background each command like this:

```
nohup command1 &
nohup command2 &
```

These can be combined into a little bash script, so you can just run a single script to start the services you want.

SeijiSensei's solution is cleaner though.

---

### Post by codemaniac on 2012-07-02
> **spynappels said:**
> Actually, that will run the second command if, and only if, the first completes correctly. 

Yes Exactly .

---

### Post by terminal27 on 2012-07-02
I haven't tried this method (/etc/rc.local) but I wil try later today.
I managed to make it works by having a script (as I had originally called runAll.sh) with a line:
 
#!/bin/bash
sh runMyServer.sh & myScript.sh &
 
and then add it to boot time with 
sudo update-rc.d runAll.sh defaults
 
But my runMyServer.sh and myScript.sh must be in the /etc/init.d folder otherwise will fail (probrably because $HOME is not available or doesn't like or bash is not available at those runlevel).
 
Thanks,

---

### Post by spynappels on 2012-07-02
> **terminal27 said:**
> 
 
But my runMyServer.sh and myScript.sh must be in the /etc/init.d folder otherwise will fail (probrably because $HOME is not available or doesn't like or bash is not available at those runlevel).

That is why in scripts it is better to use absolute paths like this:

```
#!/bin/bash
sh /home/user/path/to/runMyServer.sh & /home/user/path/to/myScript.sh &
```

---

### Post by terminal27 on 2012-07-12
> **SeijiSensei said:**
> Put the commands in /etc/rc.local. It's the last script that runs at boot time. You'll need to use sudo to edit the file since it is owned by root.
 
Actually it run better as you said, without interfereing any other system boot up.
Thanks,

---

