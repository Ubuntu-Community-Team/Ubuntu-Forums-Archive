---
title: "Start Lubuntu GUI from command line"
date: 2014-05-08
forum: Server Platforms
---

### Post by hgurol on 2014-05-08
I have a 14.04 server and a Lubuntu Desktop (core) on top of it and server boots into text mode. The idea is to be able to start the Lubuntu GUI when needed and to be able to turn back to the text mode when the GUI work is finished. May not be a widely used setup but sure it is something makes sense and that's what I need.

Now, when I boot into the command line, "startx" does not work. It does not start the GUI but just goes into a blank/black screen. The "startlubuntu" script does not exist anymore. Copying over the script from an older version does not work. The command suggested to be used as a replacement of startlubuntu; "lxsession -e LXDE -s Lubuntu" also does not work.

The only thing (somewhat) works is the command "service lightdm start", but of course with some caveats.

First problem is; when I run that command I am already logged into my server but when I start the service and the GUI, I see the login screen and I have to re-login to a server which I am already logged in. Annoying for the least.

Other problem is; when I finish my work on the GUI and log out, I go back to the graphical login screen. I do not go back to the command line which is expected. Now, this is more than annoying because there is a reason that I do not boot to the GUI directly but to the text mode. I wanna load the GUI when needed and unload it when not. This behaviour kills the whole idea.

Can anyone think of a workaround to achieve what I am looking for?

PS: There is a similar problem and a bug report [here ]("https://bugs.launchpad.net/ubuntu/+source/lubuntu-default-settings/+bug/1241958")but that is related when trying to make a remote desktop connection via some NX software. In my case, I am trying to make this work on the local machine.

Thanks....

---

### Post by trevor_allett on 2014-05-08
Questions I have are;

[LIST=1]
[*] Is this at the terminal, ie the monitor, keyboard and mouse connected to the computer?
[*] how did you install Lubuntu?
[*] do you have any thing relevant /helpful in syslog?
[/LIST]

---

### Post by matt_fussell2 on 2014-05-08
Have you tried using the init command?

To invoke a GUI try running:

```
init 5
```

To close a graphical session and return to CLI try running:

```
init 3
```

I personally haven't tried manually manipulating the runlevel on Ubuntu server in some time, and I'm not sure what to tell you about having to log in again after you start lightdm.

---

### Post by hgurol on 2014-05-08
1-
Yes

2-
apt-get install lubuntu-core --no-install-recommends

3-
a) for trying the "startlubuntu" or "lxsession -e LXDE -s Lubuntu" nothing on the syslog but I got this error message on the screen.
(lxsession:2186): Gtk-WARNING **: cannot open display:
b) for trying "startx" there is nothing on the screen since it goes black and nothing on the syslog
c) I didnt check for "service lightdm start" because it already works but in a weird way like I described.




> **trevor_allett said:**
> Questions I have are;

[LIST=1]
[*] Is this at the terminal, ie the monitor, keyboard and mouse connected to the computer?
[*] how did you install Lubuntu?
[*] do you have any thing relevant /helpful in syslog?
[/LIST]

---

### Post by hgurol on 2014-05-08
No no, neither does work.


> **matt_fussell2 said:**
> Have you tried using the init command?

To invoke a GUI try running:

```
init 5
```

To close a graphical session and return to CLI try running:

```
init 3
```

I personally haven't tried manually manipulating the runlevel on Ubuntu server in some time, and I'm not sure what to tell you about having to log in again after you start lightdm.

---

### Post by matt_fussell2 on 2014-05-08
Dumb question - did you try using sudo? Also, you might try run level 2 as indicated [here]("http://www.cyberciti.biz/faq/change-the-runlevel-for-a-linux-server/") (since Ubuntu is derived from Debian).

---

### Post by sudodus on 2014-05-08
Do you run ```
service lightdm start
``` as root (superuser)?

When running in graphics mode, you can ***start a text screen*** with one of the hot key combinations
[I][B]
ctrl + alt +F1 ... ctrl + alt +F6[/B][/I] and return to the graphics screen (while it is still running) with ***ctrl + alt +F7***

and from there you can stop lightdm with

```
service lightdm stop
```

I am logged in as the regular user and use sudo for those commands, so

```
sudo service lightdm start
```
```
sudo service lightdm stop
```

You can make a script or alias to toggle lightdm (on/off) in a convenient way. The following is a verbose script, that I store in the file [FONT=courier new]**[SIZE=3]~/bin/x[/SIZE]**[/FONT]

```
#!/bin/bash

ans="$(ps -A|grep \ lightdm$)"
res=$?
if [ "$res" == "0" ]
then
 echo "x (lightdm) is already running"
else
 echo "x will be started:"
 echo "sudo service lightdm start"
 sudo service lightdm start
fi
```

---

### Post by hgurol on 2014-05-08
No dump questions my friend.

Sudo with a non-root user, or no sudo with a root user; it is like there is no command like "init 3" or "init 5". Nothing happens, no error messages. I was just thinking that you are giving me directions from decades ago since you said you haven't tried this for a long time (kidding) but then I tried "init 1" and it takes me to the single user mode. Weird huh?

Back to the topic, I assure you "init 3" and "init 5" does not work.



> **matt_fussell2 said:**
> Dumb question - did you try using sudo? Also, you might try run level 2 as indicated [here]("http://www.cyberciti.biz/faq/change-the-runlevel-for-a-linux-server/") (since Ubuntu is derived from Debian).

---

### Post by steeldriver on 2014-05-08
AFAIK SysV-style runlevels are not relevant in Ubuntu

I would focus on finding out why lxsession says it can't open the display - is lightdm perhaps still running? if so you will need to kill it first e.g. (after logging in at one of the CLI virtual terminals as your normal user)

```

sudo service lightdm stop

lxsession -s LXDE -e LXDE

```

---

### Post by hgurol on 2014-05-08
So you say I start the service when I want the GUI and when I am finished; I switch to another display and stop the service from there. Is that right?

How does your script works? I call the same script "lightdm" and if it is runnning, scripts stops the service. If the service is not running, then it starts it. Is this how it works?

Not exactly I was hoping for but this is something.


> **sudodus said:**
> Do you run ```
service lightdm start
``` as root (superuser)?

When running in graphics mode, you can ***start a text screen*** with one of the hot key combinations
[I][B]
ctrl + alt +F1 ... ctrl + alt +F6[/B][/I] and return to the graphics screen (while it is still running) with ***ctrl + alt +F7***

and from there you can stop lightdm with

```
service lightdm stop
```

I am logged in as the regular user and use sudo for those commands, so

```
sudo service lightdm start
```
```
sudo service lightdm stop
```

You can make a script or alias to toggle lightdm (on/off) in a convenient way. The following is a verbose script, that I store in the file [FONT=courier new]**[SIZE=3]~/bin/x[/SIZE]**[/FONT]

```
#!/bin/bash

ans="$(ps -A|grep \ lightdm$)"
res=$?
if [ "$res" == "0" ]
then
 echo "x (lightdm) is already running"
else
 echo "x will be started:"
 echo "sudo service lightdm start"
 sudo service lightdm start
fi
```

---

### Post by steeldriver on 2014-05-08
It sounds like you don't want (or need) lightdm at all - once you've figured out the lxsession starting issues you should be able to disable (or remove) lightdm altogether and just boot to a CLI and start the lxsession from there. You should be able to wrap that in a ~/.xsession or ~/.xinitrc so that you can do so with plain 'startx' if you prefer.

---

### Post by hgurol on 2014-05-08
No lightdm service is not running for sure.
I would be happy to debug the problem if you or someone else helps me how to do it. So far, googling for 2 days got me no where.
"echo $DISPLAY" returns me nothing but then again this might be normal when you are on the text mode. I don't know that much.



> **steeldriver said:**
> AFAIK SysV-style runlevels are not relevant in Ubuntu

I would focus on finding out why lxsession says it can't open the display - is lightdm perhaps still running? if so you will need to kill it first e.g. (after logging in at one of the CLI virtual terminals as your normal user)

```

sudo service lightdm stop

lxsession -s LXDE -e LXDE

```

---

### Post by hgurol on 2014-05-08
You sound good. Would you like to give me hand to debug the lxsession problem?

> **steeldriver said:**
> It sounds like you don't want (or need) lightdm at all - once you've figured out the lxsession starting issues you should be able to disable (or remove) lightdm altogether and just boot to a CLI and start the lxsession from there. You should be able to wrap that in a ~/.xsession or ~/.xinitrc so that you can do so with plain 'startx' if you prefer.

---

### Post by volkswagner on 2014-05-08
Install --without a recommends causes some missing packages such as policykit.  I have a post on here related to a webdt tablet. 
Sorry I'm mobile so it's difficult for me to offer a link.

EDIT:  Here is the [link]("http://ubuntuforums.org/showthread.php?t=1780853"), pardon the whining ;)

---

### Post by steeldriver on 2014-05-08
OK so I've installed lubuntu-core --no-install-recommends in a trusty VM and can confirm what you're seeing

[ATTACH=CONFIG]253001[/ATTACH]

I also found that there seems to be a bit of a disconnect about the recommends - lxsession only *suggests *lxde-common (which is the package containing startlxde) whereas doing rdepends on lxde-common says lxsession depends on it. That's by-the-bye since after installing lxde-common (again with no-install-recommends) startlxde gives the same error...

EDIT: HOWEVER startx DOES WORK FOR ME, starting a plain LXDE session initially, but starting what I believe to be a Lubuntu session after I created a ~/.xsession file containing just

```

lxsession -s Lubuntu -e LXDE

```

[ATTACH=CONFIG]253002[/ATTACH]

So let's go back to using

```

startx

```

and see if we can figure out why *that's* not working for you

---

### Post by hgurol on 2014-05-08
Okay, I installed "lxde-common".
Now "startx" works nice, just for the plain LXDE environment though.
Then I create the file "~/.xsession" containing only the command "lxsession -s Lubuntu -x LXDE" still loads the plain LXDE session, not the Lubuntu one just like yours.
I am using root user to manage the server, so I thought if I use a non-root user maybe it would work but things get worse when I do that.
"xinit: connection to X server lost" is what I get for a non-root user. 
So, I stick with the root user, which I normally use anyway.

I am gonna do a fresh vm install and try it again.


> **steeldriver said:**
> OK so I've installed lubuntu-core --no-install-recommends in a trusty VM and can confirm what you're seeing

[ATTACH=CONFIG]253001[/ATTACH]

I also found that there seems to be a bit of a disconnect about the recommends - lxsession only *suggests *lxde-common (which is the package containing startlxde) whereas doing rdepends on lxde-common says lxsession depends on it. That's by-the-bye since after installing lxde-common (again with no-install-recommends) startlxde gives the same error...

EDIT: HOWEVER startx DOES WORK FOR ME, starting a plain LXDE session initially, but starting what I believe to be a Lubuntu session after I created a ~/.xsession file containing just

```

lxsession -s Lubuntu -x LXDE

```

[ATTACH=CONFIG]253002[/ATTACH]

So let's go back to using

```

startx

```

and see if we can figure out why *that's* not working for you

---

### Post by steeldriver on 2014-05-08
apologies, the ~/.xsession contents should have read

```

lxsession -s Lubuntu [COLOR=#ff0000]**-e**[/COLOR] LXDE

```

---

### Post by hgurol on 2014-05-08
@steeldriver and all, thank you soooooo much.

Here is the wrap up....
After installing the server 14.04
```

apt-get install lxde-common --no-install-recommends
apt-get install lubuntu-core --no-install-recommends

```

Create the file ~/.xsession 
```

touch ~/.xsession

```
with the only content of this command.
```

lxsession -s Lubuntu -e LXDE

```

Change run level to text mode and reboot.

Now,
startx - takes me to Lubuntu environment, already logged in.
Logout - back to the command line.

Works great.
Thank you guys, appreciated...

---

### Post by steeldriver on 2014-05-08
Great! happy to help

---

### Post by steeldriver on 2014-05-08
oops double post

---

### Post by aaron50 on 2015-02-04
> **hgurol said:**
> @steeldriver and all, thank you soooooo much.

Here is the wrap up....
After installing the server 14.04
```

apt-get install lxde-common --no-install-recommends
apt-get install lubuntu-core --no-install-recommends

```

Create the file ~/.xsession 
```

touch ~/.xsession

```
with the only content of this command.
```

lxsession -s Lubuntu -e LXDE

```

Change run level to text mode and reboot.

Now,
startx - takes me to Lubuntu environment, already logged in.
Logout - back to the command line.

Works great.
Thank you guys, appreciated...

I know this is an older thread, but I am hoping someone can help me. I am trying to do exactly what you are describing. I have a freshly installed ubuntu 14.04 and have installed lxde-common and ubuntu-core just as you have explained. When I use startx I get the same error as steeldriver shows in his first photo. So now I am trying to create the file ~/.xsession. I am not sure what touch is that your putting in front of it, I assume it is some kind of text editor, but when I run touch~/.xsession the command does not do anything, just goes to the next line where I can enter a new command. I entered your next command in the command line,lxsession -s Lubuntu -e LXDE, which I don't think I am supposed to do and it gives me an error. My question is how do you create the file ~/.xsession. I am very new at this, so could you go into slightly more detail by any chance, thank you for any help that you can provide.

---

### Post by steeldriver on 2015-02-04
You don't really need the extra step of "touch"ing the file - just *create* it using your favorite text editor and type the lxsession command into it, or directly by echoing the desired command string to an empty file using

```

echo 'lxsession -s Lubuntu -e LXDE' > ~/.xsession

```

or alternatively

```

cat > ~/.xsession
lxsession -s Lubuntu -e LXDE

```

and then hitting Ctrl-d to quit

---

### Post by aaron50 on 2015-02-04
> **steeldriver said:**
> You don't really need the extra step of "touch"ing the file - just *create* it using your favorite text editor and type the lxsession command into it, or directly by echoing the desired command string to an empty file using

```

echo 'lxsession -s Lubuntu -e LXDE' > ~/.xsession

```

or alternatively

```

cat > ~/.xsession
lxsession -s Lubuntu -e LXDE

```

and then hitting Ctrl-d to quit

steeldriver,

Thank you for your comments, but i am afraid that i didn't do something correctly. Here are my steps that i took from the start:
[LIST=1]
[*]installed a fresh copy of Ubuntu 14.04 trusty onto my machine
[*]ran in command line - sudo apt-get update && sudo apt-get upgrade
[*]ran in command line - sudo reboot
[*]login as the user that i created when i set up the machine
[*]ran in command line - sudo apt-get install lxde-common --no-install-recommends
[*]ran in command line - sudo apt-get install lubuntu-core --no-install-recommends
[*]ran in command line - echo 'lxsession -s Lubuntu -e LXDE' > ~/.xsession
[*]ran in command line - sudo reboot
[*]login as the user that i created when i set up the machine
[*]ran in command line - startx
[/LIST]

Here is where i get an error. It appears that it is trying to start up Lubuntu but cannot. I get a 30 or so "Initializing built-in" lines then "loading extension GLX". This looks like it is probably correct, but then i get some lines that start off (EE) and the last few are as follows:

```
Fatal server error:
(EE) Caught signal 11 (Segmentation fault). Server aborting
(EE)
(EE)
Please consult the The X.Org Foundation support at http://wiki.x.org
(EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information
(EE)
(EE) Server terminated with error (1). Closing log file.
xinit: giving up
xinit: unable to connect to X server: connection refused
xinit: server error
```

I am very new to this but "giving up" never sounds good [IMG]http://ubuntuforums.org/images/icons/icon9.png[/IMG]

I looked around for the fatal service error and maybe i don't have a graphics chip or something to support Lubuntu?? I am not sure what any of this means.

If you know why this is not working, let me know, or if you need the log information, i think i could probably figure out how to open that file and view it.

Thank again for your help

---

### Post by steeldriver on 2015-02-04
That sounds like a lower-level graphics driver issue to me - my advice (and I know some board members may disagree) would be to start a new thread since (a) it's not directly related to the issue of starting a Lubuntu session specifically; and (b) this thread being marked as [SOLVED] may mean it doesn't get as many eyeballs on it

If possible give information about your particular graphics hardware e.g. the output of 

```

sudo lshw -C display

```

---

### Post by aaron50 on 2015-02-04
Thank you, i took your advice and posted a new thread in the general information section, not sure this is where it needs to be, but i figure someone will move it if need be. In that thread i showed my graphics hardware for your reference. The thread is located here: [http://ubuntuforums.org/showthread.php?t=2263938&p=13221849#post13221849](http://ubuntuforums.org/showthread.php?t=2263938&p=13221849#post13221849)

---

### Post by Opayq on 2015-02-28
> **hgurol said:**
> @steeldriver and all, thank you soooooo much.

Here is the wrap up....
After installing the server 14.04
```

apt-get install lxde-common --no-install-recommends
apt-get install lubuntu-core --no-install-recommends

```

Create the file ~/.xsession 
```

touch ~/.xsession

```
with the only content of this command.
```

lxsession -s Lubuntu -e LXDE

```

Change run level to text mode and reboot.

Now,
startx - takes me to Lubuntu environment, already logged in.
Logout - back to the command line.

Works great.
Thank you guys, appreciated...

Perhaps you can help me! I've done exactly as you describe and it seems to work. But I have noticed that my permissions / policies are different when logging in to the desktop this way. Is that the same for you? I've made a thread about it here: [http://ubuntuforums.org/showthread.php?t=2267297](http://ubuntuforums.org/showthread.php?t=2267297). For example, I can't mount usb drives ar reboot without entering my password. Whereas I can do that just fine with the same user account when booting straight to the desktop interface.... strange.

---

