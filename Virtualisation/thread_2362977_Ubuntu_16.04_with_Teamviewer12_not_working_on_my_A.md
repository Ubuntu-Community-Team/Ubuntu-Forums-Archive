---
title: "Ubuntu 16.04 with Teamviewer12 not working on my AMD64"
date: 2017-06-04
forum: Virtualisation
---

### Post by Robbyx on 2017-06-04
After installing by following this advice:

[http://www.linuxslaves.com/2017/01/fix-teamviewer-wont-start-ubuntu-linux.html]("http://www.linuxslaves.com/2017/01/fix-teamviewer-wont-start-ubuntu-linux.html")

I tested the daemon status  with > systemctl status teamviewerd This shows the daemon is running:

> systemctl status teamviewerd&#9679; teamviewerd.service - TeamViewer remote control daemon
   Loaded: loaded (/etc/systemd/system/teamviewerd.service; enabled; vendor pres
   Active: active (running) since Sun 2017-06-04 22:37:36 BST; 46s ago
  Process: 24604 ExecStart=/opt/teamviewer/tv_bin/teamviewerd -d (code=exited, s
 Main PID: 24606 (teamviewerd)
   CGroup: /system.slice/teamviewerd.service
           &#9492;&#9472;24606 /opt/teamviewer/tv_bin/teamviewerd -d

Jun 04 22:37:36 robins-desktop systemd[1]: Starting TeamViewer remote control da
Jun 04 22:37:36 robins-desktop systemd[1]: teamviewerd.service: PID file /var/ru
Jun 04 22:37:36 robins-desktop systemd[1]: Started TeamViewer remote control dae

Lastly I ran Teamviewer 12 and it would not load because it claims the TV daemon is not running. 

Does anyone know a solution?

---

### Post by sp40140 on 2017-06-05
What is the output of 
```

which teamviewer

```
And what happens if you run
```

/usr/bin/teamviewer -stop
/usr/bin/teamviewer -start

```

---

### Post by Robbyx on 2017-06-05
> **sp40140 said:**
> What is the output of 
```

which teamviewer

```
/usr/bin/teamviewer
And what happens if you run
```

/usr/bin/teamviewer -stop
> /usr/bin/teamviewer -stop

Init...
CheckCPU: SSE2 support: yes
XRandRWait: No value set. Using default.
XRandRWait: Started by user.
Checking setup...
Launching TeamViewer ...
Launching TeamViewer GUI ...

Error parsing command line: unrecognised option '-stop'


```
/usr/bin/teamviewer -start
Ditto output for -stop as above


Thanks for your help

---

### Post by #&amp;thj^% on 2017-06-05
> **Robbyx said:**
> Thanks for your help
it would not load because it claims the TV daemon is not running.

Try this:
```
sudo teamviewer --daemon enable
```

EDIT:
For _**systemd **_run:
```
systemctl enable teamviewerd.service
systemctl start teamviewerd.service
```

---

### Post by Robbyx on 2017-06-05
Unfortunately none of the commands in your last post enable TV GUI to load! All get the same message that the daemon is not running.

---

### Post by #&amp;thj^% on 2017-06-05
:( Sorry to hear that.
The last 2 commands in my Edit worked for me.

---

### Post by sp40140 on 2017-06-06
Actually I didn't need to mess with systemd at all. There is option in TV settings to enable at startup and it works just fine.

As to your issue, I think it would be better if you re-install it. I have a feeling something went wrong during install.

---

### Post by Robbyx on 2017-06-06
I have reinstalled it many times in the hope it would correct itself. I have also reinstalled the os a few times just in case that was the cause.

---

### Post by sp40140 on 2017-06-06
First check any running TV processes and kill them.
then
```

/opt/teamviewer/tv_bin/teamviewerd start

```
I have it installed there, you should run ```
locate teamviewerd
``` to find the path.
check if it runs using "ps" or "top" or system/process monitor.
And then launch TV.

---

### Post by Robbyx on 2017-06-06
I am looking in HTOP after a reboot and there are 15 entries re teamviewer, before trying to start TV.
They have different PID otherwise they are all from command /opt/teamviewer/tv_bin/teamviewerd -d

Should they be there? I am finding I can not kill them.

---

### Post by sp40140 on 2017-06-06
I think it points to something being fishy in rc.local / init entry for TV.
I suggest you remove the manual entries for TV. And then use TV settings to auto launch TV.

Or it might have something to do with permissions. root / login id. Maybe you should check that.

---

### Post by Robbyx on 2017-06-06
Or it might have something to do with permissions. root / login id. Maybe you should check that.

Teamviewer can not be run under sudo

> ~$ gksu teamviewer

Init...
 *** TeamViewer can not be executed with sudo! ***
 Either use your normal user account without sudo
 or use a the real root account to log in to your desktop (not recommended!).

rc.local / init entry for TV
What is the path please.

---

### Post by sp40140 on 2017-06-07
As for rc.local/init.. if you haven't touched it, you don't need to worry about it. It's for auto launching the app at startup. (TV doesn't require that you do it manually though).
Honestly, I don't have anything else to suggest.

---

### Post by Robbyx on 2017-06-07
Thank you for your best efforts. 

I have it working by abandoning the specific  Ubuntu installation of TV. Instead  I have installed the standalone version, but it means I do not have a start icon to click.

There is a TV icon in the standalone directory and I have edited  it to  run   Teamviewer within the directory. Where should I copy the icon so that it appears in application icons? Do I copy the icon or link it?

Robin

---

### Post by sp40140 on 2017-06-07
Adding icon is simple. Lots of easy instructions just a search away.
However, I don't care for it as I have it set to auto-start at boot. (It's in settings of TV).
I am happy you were able to sort this out.
Cheers,

---

