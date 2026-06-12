---
title: "Jack won't start, neither in Ubuntu Studio nor Ubuntu 14.04"
date: 2014-10-09
forum: Ubuntu Studio
---

### Post by redaxe90 on 2014-10-09
Hi guys

I installed the Ubuntu Studio package while I was still running Ubuntu in 12.04 LTS and it upgraded with no problems to 12.10. After I upgraded again, to 13.04 and following that to 13.10 and now 14.04LTS, jackd completely refuses to work for me.

As an act of desperation I decided to install the Ubuntu Studio 13.10 distro on a separate drive (clean install) and I have the same error messages there and nothing wants to work there either. I'm at the end of my wits, as nothing I've tried or searched for wants to work. So here I come begging for some assistance in deciphering the errors and maybe help in brainstorming possible solutions. I have to admit that I'm not very strong in the terminal, so if you want me to add anything to configurations files or start lines, please be specific in where and how to do it, because I'm easily confused :p

Here's the error soup that comes up when I try to start up Jackd:

```
 [COLOR=#999999]11:09:14.420 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]11:09:14.451 Statistics reset.[/COLOR]
 [COLOR=#cccc99]11:09:14.466 ALSA connection change.[/COLOR]
 [COLOR=#999999]11:09:14.475 D-BUS: Service is available (org.jackaudio.service aka jackdbus).[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 Registered event listener change listener:  true 
 [COLOR=#66cc99]11:09:14.487 ALSA connection graph change.[/COLOR]
 FIXME: handle dialog start. 
 FIXME: handle dialog end. 
 FIXME: handle dialog start. 
 FIXME: handle dialog end. 
 [COLOR=#ff0000]11:11:05.182 D-BUS: JACK server could not be started. Sorry[/COLOR]
 Thu Oct  9 11:10:40 2014: Starting jack server...
 Thu Oct  9 11:10:40 2014: JACK server starting in realtime mode with priority 10
 Thu Oct  9 11:10:40 2014: ERROR: Cannot lock down 82274202 byte memory area (Cannot allocate memory)
 Thu Oct  9 11:10:40 2014: Acquired audio card Audio1
 Thu Oct  9 11:10:40 2014: creating alsa driver ... hw:Omega|hw:Omega|256|2|44100|0|0|nomon|swmeter|-|32bit
 Thu Oct  9 11:10:40 2014: configuring for 44100Hz, period = 256 frames (5.8 ms), buffer = 2 periods
 Thu Oct  9 11:10:40 2014: ALSA: final selected sample format for capture: 24bit little-endian
 Thu Oct  9 11:10:40 2014: ALSA: use 2 periods for capture
 Thu Oct  9 11:10:40 2014: ALSA: final selected sample format for playback: 24bit little-endian
 Thu Oct  9 11:10:40 2014: ALSA: use 2 periods for playback
 Thu Oct  9 11:10:40 2014: ERROR: Cannot use real-time scheduling (RR/10)(1: Operation not permitted)
 Thu Oct  9 11:10:40 2014: ERROR: AcquireSelfRealTime error
 Thu Oct  9 11:10:45 2014: ERROR: JackPosixProcessSync::LockedTimedWait error usec = 5000000 err = Connection timed out
 Thu Oct  9 11:10:45 2014: ERROR: Driver is not running
 Thu Oct  9 11:10:45 2014: ERROR: Cannot open client name = dbusapi
 Thu Oct  9 11:10:45 2014: ERROR: failed to create dbusapi jack client
 Thu Oct  9 11:10:45 2014: ERROR: Unknown request 4294967295
 Thu Oct  9 11:10:45 2014: ERROR: CheckSize error size = 0 Size() = 12
 Thu Oct  9 11:10:45 2014: ERROR: CheckRead error
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 QSpiAccessible::accessibleEvent not handled:  "2"  obj:  QMessageBox(0x7ffff6828d20) "" 
 FIXME: handle dialog start. 
 FIXME: handle dialog end. 
 [COLOR=#ff0000]11:11:18.265 Could not connect to JACK server as client. - Overall operation failed. - Server communication error. Please check the messages window for more info.[/COLOR]
 Cannot read socket fd = 17 err = Success
 CheckRes error
 JackSocketClientChannel read fail
 Cannot open qjackctl client
 QSpiAccessible::accessibleEvent not handled:  "2"  obj:  QMessageBox(0x7ffff6829a60) "" 
 FIXME: handle dialog start. 
 Thu Oct  9 11:11:18 2014: ERROR: JackPosixProcessSync::LockedTimedWait error usec = 5000000 err = Connection timed out
 Thu Oct  9 11:11:18 2014: ERROR: Driver is not running
 Thu Oct  9 11:11:18 2014: ERROR: Cannot create new client
 Thu Oct  9 11:11:18 2014: ERROR: Unknown request 4294967295
 Thu Oct  9 11:11:18 2014: ERROR: CheckSize error size = 0 Size() = 12
 Thu Oct  9 11:11:18 2014: ERROR: CheckRead error
 FIXME: handle dialog end. 
 Thu Oct  9 11:12:19 2014: Released audio card Audio1
 Thu Oct  9 11:12:19 2014: Saving settings to "/home/tommi/.config/jack/conf.xml" ...
 QSpiAccessible::accessibleEvent not handled:  "6"  obj:  QMenu(0x1e58120) "" 


```

---

### Post by jejeman on 2014-10-09
Really don't know.
Try jackd instead of jackdbus.
Try adding sudo.

---

### Post by redaxe90 on 2014-10-09
I start jackd every time, but I have no clue why jackdbus starts instead. And adding sudo how???

---

### Post by jejeman on 2014-10-09
If you use Qjacktl to start JACK it uses jackdbus by default.
Try like
```
sudo jackd ...
```

---

### Post by redaxe90 on 2014-10-09
I don't use Qjacktl to start JACK, I go straight for jackd, as I have a desktop shortcut to it. Still doesn't help. I'll try the terminal command in the morning when my brain is functioning again.

---

### Post by redaxe90 on 2014-10-10
Tried running via terminal, but due to my lack of know how, I'm stumped about what arguments to run with it. This is what I got from the terminal when I tried this:
```
tommi@Loonie:~$ sudo jackd
[sudo] password for tommi: 
jackdmp 1.9.10
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2013 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
no message buffer overruns
no message buffer overruns
no message buffer overruns

Usage: jackdmp [ --no-realtime OR -r ]
               [ --realtime OR -R [ --realtime-priority OR -P priority ] ]
      (the two previous arguments are mutually exclusive. The default is --realtime)
               [ --name OR -n server-name ]
               [ --timeout OR -t client-timeout-in-msecs ]
               [ --loopback OR -L loopback-port-number ]
               [ --port-max OR -p maximum-number-of-ports]
               [ --slave-backend OR -X slave-backend-name ]
               [ --internal-client OR -I internal-client-name ]
               [ --verbose OR -v ]
               [ --clocksource OR -c [ c(ycle) | h(pet) | s(ystem) ]
               [ --replace-registry ]
               [ --silent OR -s ]
               [ --sync OR -S ]
               [ --temporary OR -T ]
               [ --version OR -V ]
         -d master-backend-name [ ... master-backend args ... ]
       jackdmp -d master-backend-name --help
             to display options for each master backend


```

---

### Post by jejeman on 2014-10-11
Well I'm confused now. You said that
> I don't use Qjacktl to start JACK, I go straight for jackd,and now you don't know the parameters for the server?
What do you have in
```
cat .jackdrc
```

---

### Post by redaxe90 on 2014-10-11
This is all I get from the terminal command you suggested:
```
root@Loonie:~# cat .jackdrc
cat: .jackdrc: No such file or directory


```

Like I said in the original post, I'm not that terminal savvy, so all commands need to be very precise or I'm up **** creek without a paddle man ;)

---

### Post by redaxe90 on 2014-10-11
> **jejeman said:**
> Well I'm confused now. You said that
and now you don't know the parameters for the server?
What do you have in
```
cat .jackdrc
```

Sorry about the confusion, but I have a desktop shortcut for jackd, but if I try to run it from the terminal I get that problematic sequence I posted earlier

---

### Post by redaxe90 on 2014-10-11
Oddly enough, after messing about with everything I could think of, to no avail, I decided to try logging into my Gnome desktop environment and then everything works, with the exception of whatever settings I'm using, I get only sound to the left side of my headphone via my Lexicon Omega external soundcard. 

Thanks for giving this a whirl though, I guess I'll have to call this one solved even though I have no clue what I did right lol

---

### Post by jejeman on 2014-10-12
> but I have a desktop shortcut for jackdThat must be some magic icon ;)
What is the command inside?
Give us now, after working JACK,
```
cat .jackdrc
```

---

### Post by rgonnering on 2015-01-03
I updated to UbuntuStudio 14.04 and I have the same problem.

$ cat .jackdrc
/usr/bin/jackd -t 200 -p 2048 -R -T -d alsa -n 2 -r 44100 -p 1024 -d hw:SB,0

---

