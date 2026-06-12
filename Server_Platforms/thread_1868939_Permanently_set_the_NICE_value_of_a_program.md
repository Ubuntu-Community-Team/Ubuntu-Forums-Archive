---
title: "Permanently set the NICE value of a program?"
date: 2011-10-25
forum: Server Platforms
---

### Post by Huntereb on 2011-10-25
Hello, I run a Garry's Mod server using SRCDS for linux. I have very recently created this server, and today I got complaints of a lot of lag, and it crashing too much. I tried to solve this by Exiting all of the programs I don't use while the server is running, and I also tried setting the NICE value to -20 in terminal. At first this worked, but now whenever the server restarts, the NICE value returns to normal. Because of it being the type of server it is, it will restart maybe once every hour.

I cannot constantly be tending the program, so that is where my question comes in. How can I make an application automatically set it's NICE value when started?

Thank you, and I hope this forum will help me in my exploration into the world of Ubuntu!

---

### Post by Huntereb on 2011-10-25
Are bumps against the rules in this server?
 
Bump

---

### Post by nothingspecial on 2011-10-25
> **Huntereb said:**
> Are bumps against the rules in this server?
 
Bump

No, but 24hours is the recommended time.

Maybe a move to the Server Platforms section will help.

The thread will still be visible in General Help with a redirect here visible for 3 days.

---

### Post by WasMeHere on 2011-10-25
Welcome to the Ubuntu Forums, Huntereb :-)

I think that you can start the programs that should have high priority with negative niceness as you suggested (with superuser privileges). This applies to autostarted programs too. You can also start the other programs with increased niceness (maximum 19) or simply avoid using your computer for other things while it is a server.

Read the info page about nice
```
info nice
```

Did you consider installing *Ubuntu Server*, that runs without desktop graphics leaving more power for the real server tasks?

Have fun finding out about Ubuntu
Olle

---

### Post by prodigy_ on 2011-10-25
> **Huntereb said:**
> Because of it being the type of server it is, it will restart maybe once every hour.

I'm not very familiar with SRCDS, but **renice** is probably what you want. If you need help with scripting, I'll need to know how exactly the server is restarted but the basic idea is:


```

# Some command, the server is restarted.
...
# Get the (new) SRCDS PID, grep args depend on the output of ps.
PID=$(ps -ef | grep ... )   
# Change niceness.
renice -20 $PID

```

---

### Post by Huntereb on 2011-10-25
> **prodigy_ said:**
> I'm not very familiar with SRCDS, but **renice** is probably what you want. If you need help with scripting, I'll need to know how exactly the server is restarted but the basic idea is:
 
 
```

# Some command, the server is restarted.
...
# Get the (new) SRCDS PID, grep args depend on the output of ps.
PID=$(ps -ef | grep ... )   
# Change niceness.
renice -20 $PID

```
 
So how would I go about making this work? Do I use another terminal along side the server terminal?
 
From my understanding, I need a code that will scan the application every minute or less (the program has a specific name, srcds_linux). And when it detects a new PID it will set the NICE back to -20 automatically. But there's one problem with that, to set the NICE value to -20 you need to type the sudo password. So is it possible to make it so you only have to type the password once and it will work every time from there until you exit the terminal?
 
I would need a lot of help with this, I don't know where to start with this, but what I said above would solve my problem completely.
 
Also, no I don't want to get rid of the Ubuntu GUI and go to having the computer run as a terminal only. Is there a way maybe to run Ubuntu in a lower graphics mode as well? Like Windows Recovery Mode.

---

### Post by WasMeHere on 2011-10-25
```
sudo -s
``` makes the terminal window keep the current user as root. It is not generally recommended, because you can easily damage your system, but in your case maybe it would be a solution.

Another solution might be to use ***cron***. It is a little tricky because the environment is very limited.

---

### Post by Huntereb on 2011-10-25
So could someone please combine all of the commands I need here so it will work? I understand everything you guys are throwing at me, I'm just not sure which codes I need to use all togethor to do this. Like, which one goes first, second, and so on.

---

### Post by WasMeHere on 2011-10-25
> **Huntereb said:**
> ...
Also, no I don't want to get rid of the Ubuntu GUI and go to having the computer run as a terminal only. Is there a way maybe to run Ubuntu in a lower graphics mode as well? Like Windows Recovery Mode.
It might be attractive for you to run Ubuntu with a small foot-print desktop environment (compared to 'vanilla' Ubuntu or Kubuntu). *Try Xubuntu with XFCE or Lubuntu with LXDE*. This way your desktop graphics will use less RAM and the computer will be faster. In other words, there will be more power for your server task.

---

### Post by Huntereb on 2011-10-25
> **Olle Wiklund said:**
> It might be attractive for you to run Ubuntu with a small foot-print desktop environment (compared to 'vanilla' Ubuntu or Kubuntu). *Try Xubuntu with XFCE or Lubuntu with LXDE*. This way your desktop graphics will use less RAM and the computer will be faster. In other words, there will be more power for your server task.
 
 But if I installed Xubuntu (By the way, it looks great. Thanks!), would I have to remove all of the files from my computer and start all over again? I mean I can, I'll just copy everything I need for the server to my Dropbox, but is it possible to just update inside the Ubuntu I have now so it keeps all of my old files, but installs the new OS? I'm guessing not, but it would be a lot easier.
 
Also, I still need help with my last post.

---

### Post by WasMeHere on 2011-10-25
You can install the XFCE desktop environment and when logging in, you can choose which desktop session to run. I don't know if there would be extra processes running compared to a clean Xubuntu install, but I think that it is easier to get an optimized system, starting from the beginning and only installing what you really need. An alternative might be to have dual boot, to switch between a dedicated server system and a convenient desktop system.

I suggest that you sit back and think about several different alternatives. You can also search for other threads in the Ubuntu Forums, that can give you tips how to make an efficient system. Let it take some time to digest all the new ideas and alternatives!

---

### Post by Gyokuro on 2011-10-25
Why do not start your application via a script? Look at Prodigy_'s answer it's the way how you can solve your request.

---

### Post by Huntereb on 2011-10-25
Thank you Olle, I'll look into it. Now I just need to figure out how to make that nice reset code...
 
Anyone know how to set it up? Using the codes mentioned in past posts?

---

### Post by Huntereb on 2011-10-25
> **Olle Wiklund said:**
> ...Another solution might be to use ***cron***. It is a little tricky because the environment is very limited.

I just started looking into cron, the only problem with it is that I don't have the command to use with it, because the PID of the application always changes (srcds_linux). And also I keep getting this error; **"cron: can't lock /var/run/crond.pid, otherpid may be 778: Resource temporarily unavailable"**.

lol?

Thanks for the help everyone who knows what I want to do!

---

### Post by WasMeHere on 2011-10-26
> **prodigy_ said:**
> I'm not very familiar with SRCDS, but **renice** is probably what you want. If you need help with scripting, I'll need to know how exactly the server is restarted but the basic idea is:```

# Some command, the server is restarted.
...
# Get the (new) SRCDS PID, grep args depend on the output of ps.
PID=$(ps -ef | grep ... )   
# Change niceness.
renice -20 $PID

```
[QUOTE=Huntereb]I just started looking into cron, the only problem with it is that I don't have the command to use with it, because the PID of the application always changes (srcds_linux). And also I keep getting this error; "cron: can't lock /var/run/crond.pid, otherpid may be 778: Resource temporarily unavailable".
[/QUOTE]
Basically do what *prodigy_* suggests: it seems you should search for ***srcds_linux*** with ***grep***. If the following command yields a four-digit number as output,
```
ps -ef | grep srcds_linux | grep -v grep | sed s/[a-z\ ]*\ // | sed s/\ .*//
``` the next command is likely to work (to store the pid number in the shell variable PID).
```
PID=$( ps -ef | grep srcds_linux | grep -v grep | sed s/[a-z\ ]*\ // | sed s/\ .*//)
``` Anyway, please enter the output of the first command into a reply!

---

### Post by Huntereb on 2011-10-26
4230
 
Oh and thanks for translating this for me. :D
 
I did both commands, but if this is the PID, the application will restart over time! Unless the second code from what I understand saves it?

---

### Post by WasMeHere on 2011-10-26
> **Huntereb said:**
> 4230
 
Oh and thanks for translating this for me. :D
 
I did both commands, but if this is the PID, the application will restart over time! Unless the second code from what I understand saves it?

Yes, it seems to be a pid number. Now you complete what was suggested by Prodigy_ ```
renice -20 $PID
``` I hope it will work for you with cron.

---

### Post by Huntereb on 2011-10-26
Ok, I see... But I am not sure how to create a command file for crontab. I just tried creating a blank file and putting the command "*renice -20 4230*" inside, then I typed what I should and this happens:
 
```
huntereb@Huntereb:~$ sudo -s crontab 01 * * * * /home/huntereb/Update
[sudo] password for huntereb: 
01: No such file or directory

```
 
Any clue on how to make a cron file? Or am I just doing this wrong? I know I already am doing something wrong, but what exactly is going on?
 
Thank you!
 
Edit: Also, the file "*Update*" is located at "/home/huntereb/" like I typed, that's not what is wrong.

---

### Post by WasMeHere on 2011-10-26
For the moment, forget about *cron* and *crontab*. You may get that working later on.

Now I suggest that you run a 'regular shellscript' with sudo in a terminal window. This way it will be easier to get something working :-)

Make a file with the name ***2nice-20_srcds*** in a suitable directory, for example your home directory with the following content:
(cut and paste it into an editor)
```

#!/bin/bash
#
echo "Usage: $0 [number-of-seconds]"
echo "Autorefresh niceness of srcds_linux every $1 (default 60) seconds"
echo "Press  r  to refresh niceness of srcds_linux"
echo "Press  q  to quit"
if [ "$1" != "" ]
then
 typeset interval="$1"
else
 typeset interval=60
fi
typeset ans=r
while [ "$ans" != q ]
do
 PID=$( ps -ef | grep srcds_linux | grep -v grep | sed s/[a-z\ ]*\ // | sed s/\ .*//)
 if [ "$PID" != "" ]
 then
#  echo renice -20 "$PID"
  renice -20 "$PID" > /dev/null
 fi
 read -n 1 -s -t "$interval" ans
done

```
Call the file ***2nice-20_srcds*** as superuser, that is run one of the following commands from the directory where you have the file:
```
sudo bash ./2nice-20_srcds 30   # to renice every 30 seconds or
sudo bash ./2nice-20_srcds      # to renice every 60 seconds (default) or
sudo bash ./2nice-20_srcds 300  # to renice every 5 minutes ...
```

This script works if your application's name is ***srcds_linux***, and can be changed to fit another application name by changing the ***PID= ... line*** in the script file.

Check that it works using the *System Monitor* or *top*

Good luck
Olle

---

### Post by Huntereb on 2011-10-26
[Yes! Thanks dude! It works perfectly! This is exactly what I wanted from the start, amazing. I can't thank you enough!]("http://www.youtube.com/watch?v=C_VheAwZBuQ")

If there is some type of thanking system on this site I would do so, but if not then take this piece of text; "**Thank you**".

[SIZE="1"]P.S. Click the first line of text.[/SIZE]

---

### Post by WasMeHere on 2011-10-27
I'm glad it works for you, Huntereb,

Maybe next time *you* can help someone. That would be the best way of thanking me and others here at the Ubuntu Forums.

Please mark the thread SOLVED

Having fun finding out :-)
Olle

---

