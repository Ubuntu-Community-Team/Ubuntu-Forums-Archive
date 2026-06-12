---
title: "Error with checkforupdategui"
date: 2007-11-15
forum: Ubuntuzilla
---

### Post by bilbo_b on 2007-11-15
Today i would like to test the Check for Updates feature with Thunderbird. But since i dont have seen any Infobox, i have raised the command manually. After this there the following error occurs:


```
bilbo@ODIN:~$ ubuntuzilla.py -a checkforupdategui -p thunderbird
Retrieving the version of the latest release of Thunderbird from the Mozilla website...
Latest release version of Thunderbird : 2.0.0.9
Currently installed version of Thunderbird : 2.0.0.6
pgrep '^x-session-man'
Previous command has failed to complete successfully. Exiting.
Process returned code 1
Traceback (most recent call last):
  File "/usr/local/bin/ubuntuzilla.py", line 1045, in <module>
    bs.start()
  File "/usr/local/bin/ubuntuzilla.py", line 207, in start
    ti.start()
  File "/usr/local/bin/ubuntuzilla.py", line 241, in start
    self.checkforupdateGui()
  File "/usr/local/bin/ubuntuzilla.py", line 540, in checkforupdateGui
    self.updateActionsGui()
  File "/usr/local/bin/ubuntuzilla.py", line 553, in updateActionsGui
    sessionPids = self.util.getSystemOutput(executionstring="pgrep '^x-session-man'", numlines=0)
  File "/usr/local/bin/ubuntuzilla.py", line 118, in getSystemOutput
    raise SystemCommandExecutionError, "Command has not completed successfully. If this problem persists, please seek help at our website, " + self.version.url
__main__.SystemCommandExecutionError: Command has not completed successfully. If this problem persists, please seek help at our website, http://ubuntuzilla.sourceforge.net/

```

Im running Ubuntu 7.10 with XFCE. This command was at the xfce terminal as user. with sudo there are the same error....

I have updated now my thunderbird via gksudo thunderbird...

Edit: when i check in text mode, all works fine, but without the notification in the notification area...

---

### Post by nanotube on 2007-11-15
hmm... looks like you are not running the x-session-manager? i thought it was a process that is common across x/k/ubuntu... that's the process i use to detect where to "send" the gui popup notification message.

could you check if it's running:
```
ps -ax |grep x-session-man
```

can anyone else running xubuntu check if you have the x-session-manager process running?

---

### Post by bilbo_b on 2007-11-15
Hmm the session manager is not running:
```

bilbo@ODIN:~$ ps -ax |grep x-session-man
Warning: bad ps syntax, perhaps a bogus '-'? See http://procps.sf.net/faq.html
 9485 pts/0    D+     0:00 grep x-session-man
```

(no process found after, correcting command...

but there are some other stuff:

```
8702 ?        Sl     0:00 /usr/bin/xfce4-session
8710 ?        Ss     0:04 xfce-mcs-manager
```

---

### Post by kc109 on 2007-11-18
> **nanotube said:**
> 

can anyone else running xubuntu check if you have the x-session-manager process running?

On my system that is running Xbuntu 7.04 with Gnome services 
```
ps ax |grep x-session-man
```
just returns my own pts/0 terminal process so  x-session-manager is not running.

---

### Post by nanotube on 2007-11-18
ah well... some searching leads me to believe that the xfce4-session process is the equivalent of the x-session-manager on xfce. 

since i don't have xfce, i can't test, so could you edit ubuntuzilla.py and change the line that says
```
sessionPids = self.util.getSystemOutput(executionstring="pgrep '^x-session-man'", numlines=0)
```
into
```
sessionPids = self.util.getSystemOutput(executionstring="pgrep '^xfce4-session'", numlines=0)
```

and then see if the gui update checker works? should be line 553 of the file.

thanks for your help! :)

---

### Post by kc109 on 2007-11-19
> **nanotube said:**
> ah well... some searching leads me to believe that the xfce4-session process is the equivalent of the x-session-manager on xfce. 

since i don't have xfce, i can't test, so could you edit ubuntuzilla.py and change the line that says
```
sessionPids = self.util.getSystemOutput(executionstring="pgrep '^x-session-man'", numlines=0)
```
into
```
sessionPids = self.util.getSystemOutput(executionstring="pgrep '^xfce4-session'", numlines=0)
```

and then see if the gui update checker works? should be line 553 of the file.

thanks for your help! :)

The only system that I have that is running xfce is a control for other machines and I can not install any software (including Ubuntuzilla) or make changes to it. I can confirm that /usr/bin/xfce4-session is a running process ( status is Sl) on that machine.
As a fun exercise I may try to do it on a live cd boot if I get the chance, but don't rely on me. I think this is something the OP will have to do.

---

### Post by nanotube on 2007-11-20
ok, well, i'll wait, then. :) thanks for the effort, anyway!

---

### Post by kc109 on 2007-11-27
> **nanotube said:**
> ok, well, i'll wait, then. :) thanks for the effort, anyway!

Now I am really confused.

Machine with Ubuntu 7.10
Install VMware server
Set up a virtual machine and install Xubuntu 7.10 onto it
Run the Xubuntu vm
Install Ubuntuzilla 4.4.4
Use Ubuntuzilla to install firefox and Thunderbird, both 2.0.0.9
Wait for new releases
Firefox 2.0.0.10 released
Fire up the Xubuntu virtual machine and try Ubuntuzilla
It ran without any problems

```
kc109@VMxub:~$ ubuntuzilla.py -a checkforupdategui -p thunderbird
Retrieving the version of the latest release of Thunderbird from the Mozilla website...
Latest release version of Thunderbird : 2.0.0.9
Currently installed version of Thunderbird : 2.0.0.9
kc109@VMxub:~$ ubuntuzilla.py -a checkforupdategui -p firefox
Retrieving the version of the latest release of Firefox from the Mozilla website...
Latest release version of Firefox : 2.0.0.10
Currently installed version of Firefox : 2.0.0.9
```

mmm... check which session manager is running, - its is x-session, no sign of xfce4-session

```
kc109@VMxub:~$ ubuntuzilla.py --version
Ubuntuzilla version 4.4.4
Project homepage: http://ubuntuzilla.sourceforge.net/

kc109@VMxub:~$ ps ax |grep session
 4138 ?        S      0:00 dbus-daemon --session --print-address --nofork
 5202 ?        Ssl    0:00 x-session-manager
 5232 ?        Ss     0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session x-session-manager
 5235 ?        S      0:00 /usr/bin/dbus-launch --exit-with-session x-session-manager
 5236 ?        Ss     0:00 /usr/bin/dbus-daemon --fork --print-pid 4 --print-address 8 --session
 5702 pts/0    R+     0:00 grep session

kc109@VMxub:~$ ps ax |grep xfce4
 5253 ?        S      0:05 xfce4-panel --display :0.0 --sm-client-id 117f000101000119583774800000051090001
 5264 ?        S      0:04 /usr/lib/xfdesktop4/xfce4/panel-plugins/xfce4-menu-plugin socket_id 18874408 name xfce4-menu id 1 display_name Xfce Menu size 34 screen_position 1
 5265 ?        S      0:00 /usr/lib/thunar/xfce4/panel-plugins/thunar-tpa socket_id 18874439 name thunar-tpa id 4 display_name Trash Applet size 34 screen_position 11
 5270 ?        Ss     0:03 xfce4-terminal
 5742 pts/0    R+     0:00 grep xfce4
kc109@VMxub:~$ 
```

Power off pc and go down pub.

---

### Post by nanotube on 2007-11-28
> **kc109 said:**
> 
Power off pc and go down pub.
heh! :)

doesn't make much sense to me either...

---

