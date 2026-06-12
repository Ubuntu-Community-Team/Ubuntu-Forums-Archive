---
title: "How to lock ubuntu server screen"
date: 2012-04-12
forum: Server Platforms
---

### Post by Penguin360 on 2012-04-12
I am newbie to Ubuntu server and I recently installed Ubuntu Server 12.04 to try to learn the server version. Anyway, here is my situation, I login my server and run an application in the terminal, now how can I lock the server screen after the application is started? I need to leave the application running so my client can connect to it.

Thanks a lot,

---

### Post by Jonathan L on 2012-04-12
Hi Beaver

> ... to try to learn the server version ...The server way of doing things would suggest

[LIST]
[*] Make the app start on its own when the server is rebooted
[*] Make it so it doesn't have any output to a console, only to logs
[*] Don't log in on the server in the first place
[/LIST]
 
I know that's an obtuse answer, but perhaps it helps.  Tell us about the application and we might be able to help describe how to get it to run in the style of a server process, for example by using the excellent "daemon" wrapper. See [http://manpages.ubuntu.com/manpages/oneiric/man8/start-stop-daemon.8.html](http://manpages.ubuntu.com/manpages/oneiric/man8/start-stop-daemon.8.html)

Kind regards,
Jonathan.

---

### Post by Penguin360 on 2012-04-12
Thank you very much for your reply. The application I am trying to run is [Minecraft]("http://www.minecraft.net/download") server. The command I use is:
```
java -Xmx1024M -Xms1024M -jar minecraft_server.jar nogui
```

If the Minecraft server can be loaded up when the server starts, as you said, that will be perfect.

BTW, I put the wrong prefix for this post, should be **ubuntu**, not _lubuntu_.

---

### Post by roelforg on 2012-04-12
> **CodingBeaver said:**
> Thank you very much for your reply. The application I am trying to run is [Minecraft]("http://www.minecraft.net/download") server. The command I use is:
```
java -Xmx1024M -Xms1024M -jar minecraft_server.jar nogui
```

If the Minecraft server can be loaded up when the server starts, as you said, that will be perfect.

BTW, I put the wrong prefix for this post, should be **ubuntu**, not _lubuntu_.
[http://embraceubuntu.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/](http://embraceubuntu.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/)
And this script should be ok:
```

#! /bin/sh
#
# Matt LaPlante - 5/8/06 (http://boinc.berkeley.edu/dev/forum_thread.php?id=849)
# Roelf - 4/12/12 (modded for codingbeaver)
# /etc/init.d/minecraft: start and stop minecraft

BOINC_DIR="/full/path/to/dir/containing/minecraft_server.jar"
MINECRAFT_D=java -- -Xmx1024M -Xms1024M -jar $MINECRAFT_DIR/minecraft_server.jar nogui
PID_FILE="/var/run/minecraft.pid"

test -f /lib/lsb/init-functions || exit 1
. /lib/lsb/init-functions

case "$1" in
start)
log_begin_msg "Starting Minecraft server..."
start-stop-daemon -b -d $MINECRAFT_DIR --start --quiet -m -p $PID_FILE --exec \\
$MINECRAFT_D || log_end_msg 1
log_end_msg 0
;;
stop)
log_begin_msg "Stopping Minecraft..."
start-stop-daemon --stop --quiet -p $PID_FILE || log_end_msg 1
log_end_msg 0
;;
status)
#figure this out yourself:P
;;
*)
log_success_msg "Usage: /etc/init.d/minecraft {start|stop|status}"
exit 1
esac

exit 0

```

happy?

---

### Post by Penguin360 on 2012-04-12
@roelforg,

For a newbie like me, that is A LOT to digest. I bet your code works perfectly, but I need time to understand the code before I can try it. Please bear with me.

Right now, I have a batch file called start.sh with these two lines in it:
```
#! /bin/bash
java -Xmx1024M -Xms1024M -jar minecraft_server.jar nogui
```
if I modify the path to minecraft_server.jar in the batch file, then put the batch file in /etc/init.d, will that work?

---

### Post by roelforg on 2012-04-12
> **CodingBeaver said:**
> @roelforg,

For a newbie like me, that is A LOT to digest. I bet your code works perfectly, but I need time to understand the code before I can try it. Please bear with me.

Right now, I have a batch file called start.sh with these two lines in it:
```
#! /bin/bash
java -Xmx1024M -Xms1024M -jar minecraft_server.jar nogui
```
if I modify the path to minecraft_server.jar in the batch file, then put the batch file in /etc/init.d, will that work?

Short: nope
Long: The script get called like this on boot:
```

/etc/init.d/minecraft start

```
start-stop-daemon (look up it's man page, very interesting stuff) is used to start and stop the program you used it for to start (java)
Got this? Let's move on...
When shutting down, start-stop-daemon kills that java when init calls:
```

/etc/init.d/minecraft stop

```

I advise reading this: [http://tldp.org/LDP/abs/html/index.html](http://tldp.org/LDP/abs/html/index.html)
It's a lot to read but it'll teach you basic bash scripting,
you're gonna need it.
Configured 3 desktops and 1server on ubuntu server, bash is a must know

---

### Post by papibe on 2012-04-12
Hi CodingBeaver.

The simplest solution I can think, so you don't have to deal with init scrtips, is to use 'screen'.

To install it:
```
sudo apt-get install screen
```
Then you could run your script like this:
```
screen -dmS MyMinecraft start.sh
```
That will create a virtual detached screen where your script will run. You can logout now, and it will still be running.

To attach the screen run this:
```
screen -r MyMinecraft
```
Now you'll be inside the screen running your script. To de attach it again press:
```
Ctrl+a d
```
That is 'Control' and 'a' press together, and then a 'd'.

For more advance stuff using screen and minecraft (and crontab) take a look at this [thread]("http://ubuntuforums.org/showthread.php?t=1809501&highlight=minecraft").

Hope that helps.
Regards.

---

### Post by Penguin360 on 2012-04-12
Hi roelforg,

Thank you so much for your patience. I will definitely read the guide you suggested. I will come back after I finish the reading (or at least have a better understanding).

---

### Post by Penguin360 on 2012-04-12
> **papibe said:**
> Hi CodingBeaver.

The simplest solution I can think, so you don't have to deal with init scrtips, is to use 'screen'.

To install it:
```
sudo apt-get install screen
```
Then you could run your script like this:
```
screen -dmS MyMinecraft start.sh
```
That will create a virtual detached screen where your script will run. You can logout now, and it will still be running.

To attach the screen run this:
```
screen -r MyMinecraft
```
Now you'll be inside the screen running your script. To de attach it again press:
```
Ctrl+a d
```
That is 'Control' and 'a' press together, and then a 'd'.

For more advance stuff using screen and minecraft (and crontab) take a look at this [thread]("http://ubuntuforums.org/showthread.php?t=1809501&highlight=minecraft").

Hope that helps.
Regards.

This is very interesting. I will give it a try.

---

### Post by roelforg on 2012-04-12
> **CodingBeaver said:**
> This is very interesting. I will give it a try.

I never got along with screen.
But i can't stress enough how important learning bash is when using ubuntu server.

---

### Post by CharlesA on 2012-04-12
> **papibe said:**
> Hi CodingBeaver.

The simplest solution I can think, so you don't have to deal with init scrtips, is to use 'screen'.

To install it:
```
sudo apt-get install screen
```
Then you could run your script like this:
```
screen -dmS MyMinecraft start.sh
```
That will create a virtual detached screen where your script will run. You can logout now, and it will still be running.

To attach the screen run this:
```
screen -r MyMinecraft
```
Now you'll be inside the screen running your script. To de attach it again press:
```
Ctrl+a d
```
That is 'Control' and 'a' press together, and then a 'd'.

For more advance stuff using screen and minecraft (and crontab) take a look at this [thread]("http://ubuntuforums.org/showthread.php?t=1809501&highlight=minecraft").

Hope that helps.
Regards.
This whole thing.

Screen = need to have.

As for "locking" the screen, just log out of the console.

I haven't done a console login in ages - everything is done via ssh for me.

---

### Post by roelforg on 2012-04-12
> **CharlesA said:**
> This whole thing.

Screen = need to have.

As for "locking" the screen, just log out of the console.

I haven't done a console login in ages - everything is done via ssh for me.

Likewise here,
but i always used a combi of nohup and io redirection to files (i heart logfiles).
Can't get along with screen.

---

### Post by CharlesA on 2012-04-12
> **roelforg said:**
> Likewise here,
but i always used a combi of nohup and io redirection to files (i heart logfiles).
Can't get along with screen.
Ah. I tried using nohup and lock/log files, but I found screen easier to deal with.

To each their own. ;)

I used this page to learn the basics:
[http://www.rackaid.com/resources/linux-screen-tutorial-and-how-to/](http://www.rackaid.com/resources/linux-screen-tutorial-and-how-to/)

---

### Post by roelforg on 2012-04-12
> **CharlesA said:**
> Ah. I tried using nohup and lock/log files, but I found screen easier to deal with.

To each their own. ;)

I used this page to learn the basics:
[http://www.rackaid.com/resources/linux-screen-tutorial-and-how-to/](http://www.rackaid.com/resources/linux-screen-tutorial-and-how-to/)

Still don't get screen.
But the linux way is: If you don't like it, change it!
And that has never let me down!
I don't like screen, so i used the alternative (which is also easier to search).

My tool is files and your's is screen; at least 2 extra skills for the community :)

---

### Post by Jonathan L on 2012-04-13
Hi Coding Beaver

From looking around at others (search for minecraft daemon) you'll see this is a common enough problem with no perfect solution which suits all.  Many people have found complex solutions to maximise performance and so on.

My advice would be:

If you want to run minecraft server and use its interactive features, most people use seem to use screen.  It gives you a virtual screen which you can disconnect from, and log out; when you log back in again you can connect to that virtual screen again.

If you want to learn the "server approach", which is basically hands off and non-interactive, follow roelforg's trail and the others you'll find when you search.

At least one thing I read suggested simple redirection should work, which made me want to try daemon, perhaps a bit like this:

make a user called 'mrminer' or whatever you like
```
sudo apt-get install daemon

sudo daemon --name=mcserver --respawn --user=mrminer -- java -Xmx1024M -Xms1024M -jar minecraft_server.jar nogui
```This "daemonises" the program: cd to the root, disconnects terminals and so on.

Let us know how you get on.

Kind regards,
Jonathan.

---

