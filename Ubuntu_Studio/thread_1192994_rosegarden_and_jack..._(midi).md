---
title: "rosegarden and jack... (midi)"
date: 2009-06-20
forum: Ubuntu Studio
---

### Post by zander1013 on 2009-06-20
hi,

i have installed rosegarden and jack in an attempt to utilize the midi functions of my fender g-dec guitar amp.

(i am using 9.04)

when i start rosegarden i get a warning dialog rosegarden failed to connect to the jack server.

i am pretty sure that jack is installed but it is not starting. thus midi applications like rosegarden cannot connect to it.

please advise.

-zander

---

### Post by ChrisB111 on 2009-06-21
Have you got qjackctl installed, try typing qjackctl in a terminal. This is the interface you use to start the jack server, if you haven't got this installed use synaptic to find it and install it.

Chris

---

### Post by raboofje on 2009-06-21
As chris mentions, you need to start jack yourself first, and qjackctl is a good way of doing that.

You might want to check out [http://rosegarden.sourceforge.net/tutorial/en/chapter-2.html](http://rosegarden.sourceforge.net/tutorial/en/chapter-2.html) , which seems pretty comprehensive.

---

### Post by zander1013 on 2009-06-21
thank you chris it starts and runs. it seems like "sudo qjackctl" gives the best results...

> af@gaga:~$ sudo qjackctl
[sudo] password for af: 
Suspending PulseAudio


but when i start rosegarden it still post a dialog to notify of this error...
> 
Rosegarden could not connect to the JACK audio server. This probably means the JACK server is not running.
If you want to be able to play or record audio files or use plugins, you should exit Rosegarden and start the JACK server before running Rosegarden again.

even though i clicked the start button and the jack server state is listed as started in the jack audio kit status dialog box.

there are a number of errors that post when rosegarden starts...
> 
System timer resolution is too low
Rosegarden was unable to find a high-resolution timing source for MIDI performance.
You may be able to solve this problem by loading the RTC timer kernel module. To do this, try running sudo modprobe snd-rtctimer in a terminal window and then restarting Rosegarden.
Alternatively, check whether your Linux distributor provides a multimedia-optimized kernel. See [http://rosegarden.wiki.sourceforge.net/Low+latency+kernels](http://rosegarden.wiki.sourceforge.net/Low+latency+kernels) for notes about this.

perhaps this will go away if i plug in a midi device? but probably it is the kernel. yes?

when i ran sudo modprobe snd-rtctimer i got this...

> af@gaga:~$ sudo modprobe snd-rtctimer
[sudo] password for af: 
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
FATAL: Module snd_rtctimer not found.
af@gaga:~$ 



and this one...
> 
Helper programs not found
Rosegarden could not find one or more helper programs which it needs to provide some features. The following features will not be available:
Export and import of Rosegarden Project files
To fix this, you should install the following additional programs:
kdialog - for project file support

but i have installed everything that came up in synaptic package manager when i searched for kdialog (there were only 2 ssft and libui-dialog-pearl).

and of course this one too...

> Newer version available
A newer version of Rosegarden may be available.
Please consult the Rosegarden website for more information.

i just installed rosegarden using synaptic package manager tonight so i presume that it would be the latest for use with 9.04.

my bad to bring all this to the table but it is where i am at.


if you can help it would be great.


thank you,

-zander:popcorn:

---

### Post by raboofje on 2009-06-21
> **zander1013 said:**
> it seems like "sudo qjackctl" gives the best results...

but when i start rosegarden it still post a dialog to notify of this error...
> Rosegarden could not connect to the JACK audio server

You should not use 'sudo' when running qjackctl: applications running as root will not 'see' jack running as a user, and vice-versa. It is a bad idea to run all your audio applications as root.

> System timer resolution is too low

You seem not to be running an -rt kernel. This might not be a problem for you right now, but should improve performance.

> Rosegarden was unable to find a high-resolution timing source for MIDI performance

Do you have a /dev/rtc? What permissions does it have? For example:

```
arnouten@mintzer:~$ ls -alFh /dev/rtc
lrwxrwxrwx 1 root root 4 2009-05-08 01:25 /dev/rtc -> rtc0
arnouten@mintzer:~$ ls -alFh /dev/rtc0
crw-rw---- 1 root audio 252, 0 2009-05-08 01:25 /dev/rtc0
```

Looks like [http://rosegarden.wiki.sourceforge.net/Low+latency+kernels](http://rosegarden.wiki.sourceforge.net/Low+latency+kernels) has disappeared, we should create that one again.

> you should install the following additional programs:
kdialog - for project file support

You probably don't really need 'kdialog', but you could search for it with 'apt-file search bin/kdialog'.

> Newer version available

Yeah, for now I'd just stick to the packaged version.

---

### Post by thorgal on 2009-06-21
don't start any jack application as root, especially the jack server itself. If you do that, you will have to start all jack clients as root.

start qjackctl as yourself (af) without sudo.
To enjoy the RT mode, you need the right permissions to do so.

Google "/etc/security/limits.conf audio group" to do that properly.
There are tons of posts about it in this forum.

---

### Post by raboofje on 2009-06-21
> **thorgal said:**
> To enjoy the RT mode, you need the right permissions to do so.

Google "/etc/security/limits.conf audio group" to do that properly.
There are tons of posts about it in this forum.

All the relevant information should be at the corresponding wikipage, [https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation). If not, we should extend it :)

---

