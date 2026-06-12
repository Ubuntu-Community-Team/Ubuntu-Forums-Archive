---
title: "Mystery in bash history"
date: 2007-06-22
forum: Server Platforms
---

### Post by Bernd Nowak on 2007-06-22
I have upgraded my Ubuntu server installation to 7.0.4 server. Everything runs.
This server is setup as a router for my home network and has 2 ethernet cars.
eth0 which connects to my home network and
eth1 which is used with my DSL modem.

As I don't have any graphical stuff I have shorewall installed which only allows incoming port 80 for my apache webserver (webmail via squirrelmail 1.4.9.a) and port 443 for ssh (443 because I often have to work at customers behind several firewalls).

Now if I look through the bash history I can see this commands:

```

PROMPT_COMMAND='pwd>&7;kill -STOP $$'
cd "`echo -e '\0057home'`"
cd "`echo -e '\0057'`"
cd "`echo -e '\0057var'`"
cd "`echo -e '\0057var\0057log'`"
cd "`echo -e '\0057var'`"

```

I have checked with rkhunter but nothing.
My feeling tells me that those get through apache2/php. Any ideas ?

Thanks a lot

---

### Post by gaten on 2007-06-23
Check your Apache logs for anything odd. Also, unless you are running APache as your main user (a bad idea), those commands wouldn't show up in YOUR bash_history as they would be run as the Apache user (assuming they are being run though Apache).

Oddly enough, the "script" kills the bash shell ($$), then changes the directory 5 times to /home, /, /var, /var/log, and /var again. 

I'm not going to even pretend I know what they are trying to do, but I'm guessing a test of sorts. You could look up mod_security or mod_chroot for Apache to increase security.

---

### Post by Decoy on 2007-07-20
Bernd Nowak, you know, I have the same stuff with my account on my home server, but it doesn't run httpd! ;) So, it cannot be apache/php...

---

### Post by Bernd Nowak on 2007-07-24
Can it be Midnight Commander related ?

---

### Post by koenn on 2007-07-24
I don't understand the PROMP_COMMAND either. 
The ```
cd "`echo -e '\0057'`"
``` construction seems to be a trick to express the "/" in paths. 
There's an old trick to break out of a web server's document root and gain access to the file system by sending urls like ```
http://server/../../../ 
``` or something. Browsers, web servers and some firewalls detect this and correc/refuse it. The "echo -e '\0057" stuff might be an attempt to circumvent this. Or so.

---

### Post by Mr. C. on 2007-07-24
The PROMPT_COMMAND is a bash variable, whose contents are executed just prior to printout of the prompt.

The >&7 construct duplicates STDOUT into the file descriptor 7, which must have been opened earlier. Thus, the current working directory is output, duplicated into whatever file was previously opened with file descriptor 7.

Every time one of those cd's occurred, the current working directory was output.

This would be a very convenient way to determine which directories existed.

Imagine that file descriptor 7 was a pipe or connection to a running program, that transmitted its data over the network.

The kill -STOP $$ sends a STOP signal to the current shell, which stops.  It will not continue until a CONT signal is sent.

Try it: from one shell, issue the command:

```
echo $$          # get the current shell's PID
kill -STOP $$    # now the shell will appear hung, because its stopped

```
from another shell

```
kill -CONT PID   # PID is the process ID output above
```

This signal could be sent programmatically by some other program, which essentially would do so after reading input from file descriptor 7.

Without more data, we can't determine much more.

MrC

---

### Post by kerry_s on 2007-07-24
that definitely looks like the out put of mc. when you use mc all the movements you do are actually little commands in a terminal, so since it's a command run in a terminal it's logged in history.

Wait: i got that wrong, it only writes on closing, so i'm guessing it's a session saving thing. 

here's what mine looks like and i use mc all the time.

```

 PROMPT_COMMAND='pwd>&7;kill -STOP $$'
mc
 PROMPT_COMMAND='pwd>&7;kill -STOP $$'
xman
rxvt -rv mc -x
rxvt -rv-e mc -x
rxvt -rv -e mc -x
rxvt -rv -e mc
rxvt
 PROMPT_COMMAND='pwd>&7;kill -STOP $$'
 cd "`echo -e '\057home\057user\057\056fluxbox'`"
 PROMPT_COMMAND='pwd>&10;kill -STOP $$'
 cd "`echo -e '\057home\057user\057\056fluxbox'`"
 PROMPT_COMMAND='pwd>&10;kill -STOP $$'
 cd "`echo -e '\057home'`"
 cd "`echo -e '\057'`"
 cd "`echo -e '\057etc'`"
locale
 PROMPT_COMMAND='pwd>&10;kill -STOP $$'
reset
 PROMPT_COMMAND='pwd>&10;kill -STOP $$'
mc
 PROMPT_COMMAND='pwd>&10;kill -STOP $$'
mc
ls -a
 PROMPT_COMMAND='pwd>&10;kill -STOP $$'
mc
mc -a
 PROMPT_COMMAND='pwd>&10;kill -STOP $$'
mc
 PROMPT_COMMAND='pwd>&10;kill -STOP $$'
 cd "`echo -e '\057home\057user\057\056fluxbox'`"
 PROMPT_COMMAND='pwd>&10;kill -STOP $$'
 PROMPT_COMMAND='pwd>&7;kill -STOP $$'
 cd "`echo -e '\057home'`"
 cd "`echo -e '\057'`"
 cd "`echo -e '\057media'`"
 cd "`echo -e '\057media\057sda\061'`"
 cd "`echo -e '\057media'`"
 PROMPT_COMMAND='pwd>&7;kill -STOP $$'
sudo visudo
 PROMPT_COMMAND='pwd>&7;kill -STOP $$'
sudo updatedb
sudo update-menus
sudo apt-get update
pstree
 PROMPT_COMMAND='pwd>&7;kill -STOP $$'
 PROMPT_COMMAND='pwd>&10;kill -STOP $$'
urxvtd
 PROMPT_COMMAND='pwd>&7;kill -STOP $$'
 PROMPT_COMMAND='pwd>&10;kill -STOP $$'
killall urxvtd
 PROMPT_COMMAND='pwd>&7;kill -STOP $$'
 cd "`echo -e '\057home\057user\057\056fluxbox'`"
locale
 PROMPT_COMMAND='pwd>&10;kill -STOP $$'
 cd "`echo -e '\057home\057user\057\056config'`"
 cd "`echo -e '\057home\057user'`"
 PROMPT_COMMAND='pwd>&10;kill -STOP $$'
 PROMPT_COMMAND='pwd>&7;kill -STOP $$'
xrdb -merge $HOME/.Xdefaults
ls -a
mc
 PROMPT_COMMAND='pwd>&7;kill -STOP $$'
ls -a
mc
 PROMPT_COMMAND='pwd>&10;kill -STOP $$'
 PROMPT_COMMAND='pwd>&7;kill -STOP $$'
 PROMPT_COMMAND='pwd>&10;kill -STOP $$'
 PROMPT_COMMAND='pwd>&7;kill -STOP $$'
sudo orphaner
 PROMPT_COMMAND='pwd>&10;kill -STOP $$'
 cd "`echo -e '\057home'`"
 cd "`echo -e '\057'`"
 cd "`echo -e '\057etc'`"
 cd "`echo -e '\057etc\057modutils'`"
 cd "`echo -e '\057etc'`"
 PROMPT_COMMAND='pwd>&7;kill -STOP $$'
xedit .Xdefaults
ls -a
 PROMPT_COMMAND='pwd>&7;kill -STOP $$'
 cd "`echo -e '\057home\057user\057Save'`"
 cd "`echo -e '\057home\057user'`"
 cd "`echo -e '\057home\057user\057Save'`"
sudo ./ice
sudo ./iceweasel-fix 
sudo ./install -i
sudo ./iceweasel-fix 
 PROMPT_COMMAND='pwd>&7;kill -STOP $$'
 cd "`echo -e '\057home'`"
 cd "`echo -e '\057'`"
 cd "`echo -e '\057root'`"
sudo ./iceweasel-fix 
sudo updatedb
 PROMPT_COMMAND='pwd>&7;kill -STOP $$'
ls -a
 PROMPT_COMMAND='pwd>&7;kill -STOP $$'
 cd "`echo -e '\057home\057user\057Applications\057Other'`"
 cd "`echo -e '\057home\057user\057Applications'`"
 PROMPT_COMMAND='pwd>&7;kill -STOP $$'

```

---

### Post by Mr. C. on 2007-07-24
Since this question has come up a couple of times, I went to the source, literally.  This is from Midnight Commander.  The source shows:

```
$ grep PROMPT_COMMAND=  */*

src/subshell.c:             " PROMPT_COMMAND='pwd>&%d;kill -STOP $$'\n",
```

Case closed.

MrC

---

### Post by wladyx on 2008-04-08
Did you find any workarounds?

---

