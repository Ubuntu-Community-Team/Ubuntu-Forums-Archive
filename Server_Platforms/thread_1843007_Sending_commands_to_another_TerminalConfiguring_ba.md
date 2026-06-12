---
title: "Sending commands to another Terminal/Configuring bash env remotely"
date: 2011-09-12
forum: Server Platforms
---

### Post by darkscaryforest on 2011-09-12
Hello, 

I'm new so please inform me if I break some form of etiquette with my first post here; I'll take note of it for the future.  I hope I'm posting this in the correct place.
The only similar post I've found on this is here: [http://ubuntuforums.org/showthread.php?t=1571708](http://ubuntuforums.org/showthread.php?t=1571708)
which doesn't address exactly what I'm looking for.

**The Problem:**
How to instruct that a command be executed on a specified terminal/shell from another terminal/shell.
------
Example:
TTY1:
# script_that_sends_command "ls"

TTY2:
*displays current directory contents of TTY2*
-------

Note: doing a 
ls > /dev/tty2 or ls | tee /dev/tty2
would just display the current directory contents of TTY1 on TTY2, which is not what I'm looking to do.

**What I Really Want it For:**
It's not uncommon for me to have like 10 terminals open.  If I change something in one terminal, such as a few exported environment variables in a script, I would have to manually run the script on each terminal for the change to be global.  It would be beyond awesome if I could make a script that detects open terminals and tells them to run that other script to update environment variables.  I just can't figure out how to update variables, or run commands, on already existing shells/terminals without typing it in every single window.  The only solution I can figure is to create some kind of custom background process that gets launched per new shell and listens for another process to tell it to run a designated script.  But perhaps there's a much simpler way..

I'm not really sure if I should be using the word "terminal" here either...maybe what I want is to send a command to the bash shell running on the terminal device?

Any insight you have is greatly appreciated, even a "it can't be done."  I just gotta know if there's a way! =)

---

### Post by papibe on 2011-09-12
Welcome to the forums!

I know how do accomplish that using terminals administrated by 'screen'. For example if you have two gnome-terminals running:
```
$ w
 18:31:58 up 10:37,  3 users,  load average: 1.03, 0.79, 0.60
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
user    tty7     :0               07:55   10:36m 31:24   0.40s gnome-session
user    pts/0    :0.0             07:56    0.00s  0.27s  0.01s w
user    pts/1    :0.0             18:25   11.00s  0.24s  0.24s bash
```
Then go to the first one and enter:
```
$ screen -S mySession1
```
Now that terminal will accessible using screen with the name 'mySession1'.

Change directories in that session so can see the trick working:
```
$ cd Music
```

Go to the second terminal and enter:
```
$ screen -S mySession1 -X stuff "ls ^M"
```
You are sending a request to execute an 'ls 'to the first terminal. The ^M is the representation of a escaped control+M (i.e. an 'enter'). To escape control character in bash you press control+V. So to achieve the desired results you have to press control+V control+M.

I hope this helps,
Regards.

Note 1: If screen is not installed, install it like this:
```
$ sudo apt-get install screen
```

Note 2: here's a couple of threads that also can be helpful: [this]("http://ubuntuforums.org/showthread.php?t=1809501&highlight=screen+cron") and [this]("http://ubuntuforums.org/showthread.php?t=1644479&highlight=screen").

---

### Post by nothingspecial on 2011-09-12
Hi,

You did not break any form of etiquette here.

I have simply moved your post to where you should get the most help.

Cheers.

---

### Post by darkscaryforest on 2011-09-13
First off, thank you for the move nothingspecial

Papibe, your clever solution works perfectly!  I could do so much with this\\:D/

Thank you for taking the time to post your detailed explanation!  Had I even known you could do this with screen, I would have totally overlooked the need for that escape character.

---

