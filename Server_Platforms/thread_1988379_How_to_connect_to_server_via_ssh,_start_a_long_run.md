---
title: "How to connect to server via ssh, start a long running process and logout?"
date: 2012-05-27
forum: Server Platforms
---

### Post by legolas_w on 2012-05-27
Hi,

I have a problem like this:

I have a server which I should start a long running process from time to time on that server using ssh. I want to connect to the server  start the long running process and in case I got disconnected from the internet or close the terminal window... I want the process to survice and finish it's job rather than being interrupted because of my ssh connection being lost.

is that possible?

thanks.

---

### Post by SeijiSensei on 2012-05-27
Sure.  Run in it the background.  Adding a "&" to the end of a command detaches it from the terminal and runs it as a background task.  If you're running a script, say /usr/local/sbin/myscript, you'd just run "/usr/local/sbin/myscript &".  Now if the program writes to the terminal for any reason, you're going to see that output on the screen. So if the program produces output, you'll want to pipe it to a file like this.  

```
/usr/local/sbin/myscript > /var/log/myscript 2>&1 &
```

sends all the output to /var/log/myscript including anything written to the error terminal syserr.  That "2>&1" redirects output to device 2, syserr, to device 1, sysout.  All of sysout is sent to /var/log/myscript.

Of course, you should know whether the program will produce output by testing it from the command prompt.  Before I start any long-running program off on its own, I make sure to do a couple of test runs with the program in the foreground so I can see everything that's happening and intervene if necessary.  After a couple of clean test runs, running it in the background is fine.  

Once the program has started you can logout.  I usually have scripts write logs, so I'll often let the program run in the background and keep tabs on its behavior with "tail -f /var/log/myscript".

Of course, if you have a script that you want to run on a regularly-scheduled basis, you should use [cron]("https://help.ubuntu.com/community/CronHowto").  If you need the script to run with root privileges, edit root's crontab with "sudo crontab -e".  Otherwise entering just "crontab -e" will edit the current user's file.  You can control the editor it uses by setting "export EDITOR=editor_name" before running crontab.  A good choice for people new to Linux is "export EDITOR=nano".  Scripts run from cron should abide by the same rules about capturing output as any other background task.

---

### Post by papibe on 2012-05-27
Hi legolas_w.

Sure you can do it. The simplest solution is to use 'screen', which is a virtual terminal that be deattached from the console so it could continue running on the background.

To install it:
```
sudo apt-get install screen
```
To start a virtual screen named 'MyProcess':
```
screen -S MyProcess
```
Then you can run your script just as you would do normally:
```
./myscript.sh
```
To deattach the screen press Ctrl+a d (that is hold control, press a, release all, and then press d).

If you want to reattach the screen to check if your script is still running, do it like this:
```
screen -r MyProcess
```
Again you can deattach the screen press Ctrl+a d

You can logout now, and the process will still be running. You can go back any time to check how things are doing: reattach the screen, and deattach it before you leave.

In case you want to terminate the screen: cancel your script by pressing Ctrl+C, and then either:
[LIST]
[*]Entering 'exit', or
[*]Pressing Ctrl+D.
[/LIST]
I hope that helps, and tell us if you need more tips with 'screen'.
Regards.

---

### Post by CharlesA on 2012-05-27
+1 to screen.

You can also run it in the background as Seiji said, with the script writing output to a log file.

---

### Post by CharlesA on 2012-05-27
+1 to screen.

You can also run it in the background as Seiji said, with the script writing output to a log file.

---

### Post by The Cog on 2012-05-27
screen is good when you want to drop back and begin interacting with the program again. It's good to know how to use screen.

I think that running a program with & is will not work for this. For instance "program-name &" will launch it in background but that it will die as soon as you disconnect. After launching it in the background, you have to use the command "disown", which makes it immune to your logout. Alternatively start the program with nohup, as in "nohup program-name &", but unless yo uarrange to redirect its output, this will create a file called nohup.out and pipe the program's output there.

Edit: Second paragraph is rubbish - see SeijiSensei's reply to this post.

---

### Post by SeijiSensei on 2012-05-27
> **The Cog said:**
> I think that running a program with & is will not work for this.
I just tested this by connecting with ssh to another host and running this script:

```

#!/bin/bash

while true
do
   echo "hi"
   sleep 3
done

```

I ran it from the command prompt and got the expected series of "hi"'s on the screen.  Then I ran it in the background as "./testscript > ~/testscript.log &" piping sysout to the log.  I then closed my SSH connection.  When I reconnected, the job was still running in the background and writing to the log.

---

### Post by legolas_w on 2012-05-27
Thank you very much. very helpful. I used the the following sample with slight variation.
```
/usr/local/sbin/myscript > /var/log/myscript 2>&1 &
```

Using screens is good but I cannot install it on the machine because it is restricted to what is already installed and no new package is allowed.

---

### Post by CharlesA on 2012-05-27
screen should be installed by default.

---

### Post by The Cog on 2012-05-28
> **SeijiSensei said:**
> I just tested this by connecting with ssh to another host and running this script:

```

#!/bin/bash

while true
do
   echo "hi"
   sleep 3
done

```

I ran it from the command prompt and got the expected series of "hi"'s on the screen.  Then I ran it in the background as "./testscript > ~/testscript.log &" piping sysout to the log.  I then closed my SSH connection.  When I reconnected, the job was still running in the background and writing to the log.
Thanks for the correction. I just tried it with local terminals in the GUI, and killing the parent kills the child there. But as you say, it's OK over SSH, so there's a difference between the two situations, obviously.

---

### Post by Cheesemill on 2012-05-28
> **CharlesA said:**
> screen should be installed by default.

+1 for screen. It is installed by default on a Ubuntu Server installation  and is a very useful tool to learn.

---

### Post by LHammonds on 2012-05-29
If I want to login, run a job and logout, I use nohup to ensure the job will not hang-up (no matter how I am connected) and use "&" to send it into the background.

If my script handles all output:
**nohup ./scriptname.sh > /dev/null 2>&1**

If there might be screen/error output that I need to capture:
**nohup ./scriptname.sh > /var/log/scriptname.log 2>&1**

If I do not log out, I can bring the command back to the foreground by typing **fg 1**.  If I have more than one job running, I can type **jobs** to see a list of jobs and their job numbers I can use with the **fg** command.

Even if you start the job without &, you can do the same thing by pressing **CTRL+Z** while waiting on the job to finish.  It will assign a job number to it and temporarily "stop" it from running.  To allow it to continue running in the background, type **bg 1** to tell job #1 to continue running in the background.  However, you are not guaranteed it will run if you logout (depends on the flavor of OS and how you logged in).

There is not a "clean" way of managing jobs when you logout/exit because when you log back in, the **jobs** and **fg** command will not work (or at least "see" any jobs).  There is a way to disown a job before logging out but as others have said, if you need to do something like that, **screen** is probably the better tool for the job and it comes standard with Ubuntu Server.

The only "job" I currently use screen for is Minecraft because you have to be at the console to issue a shutdown command in order to cleanly stop Minecraft.  So I call screen inside my startup script in order to keep things as "normal" as possible when controlling jobs from crontab.  e.g. I call the script in crontab like any other script, however, inside the script, I have the following command:

```
**screen -d -m** java -d64 -Xincgc -Xmx${RAM}M -jar ${CBDIR}/${CBJAR} nogui
```If I ever need to shutdown Minecraft, I login to the server and type **screen -r** which brings me to Minecraft's console so I can issue the "stop" command...which also exits the screen command and returns you to the prompt.

Other commands helpful to know about screen are:

**man screen** - Gives you the manual
**CTRL+A** and then **d** - While inside a screen session, it will detach and send you back to the prompt.
**screen -ls** - Lists all screen sessions in case you have multiple.
**screen -r** - Reattaches to the last screen.

---

