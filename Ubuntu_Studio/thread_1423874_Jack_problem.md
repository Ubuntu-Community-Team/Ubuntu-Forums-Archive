---
title: "Jack problem"
date: 2010-03-07
forum: Ubuntu Studio
---

### Post by Philip133 on 2010-03-07
Hello. I have jack, qjackctl and ubuntu-studio-audio (or whatever it's called) installed.
My problem is, that whenever I try to run jack through qjackctl i get this in the messages window:
```

 p, li { white-space: pre-wrap; }  14:26:23.629 Patchbay deactivated.
 14:26:23.635 Statistics reset.
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 14:26:23.663 ALSA connection graph change.
 14:26:23.857 ALSA connection change.
 14:26:32.182 JACK is starting...
 14:26:32.182 jackdmp -dalsa -dhw:0 -r44100 -p1024 -n2
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 14:26:32.206 Could not start JACK. Sorry.
 14:26:33.753 JACK was stopped with exit status=255.
 14:26:33.754 Post-shutdown script...
 14:26:33.754 killall jackd
 jackd: no process found
 14:26:34.166 Post-shutdown script terminated with exit status=256.

```Here's my settings window:
[[IMG]http://img31.imageshack.us/img31/2659/snapshot1pl.png[/IMG]]("http://img31.imageshack.us/i/snapshot1pl.png/")

I'm on a Realtek HD onboard soundcard, and I have really no idea what is wrong :/

Please help [-o<

---

### Post by AutoStatic on 2010-03-07
Hello Philip133,

```
14:26:32.182 jackdmp -dalsa -dhw:0 -r44100 -p1024 -n2
```
jackdmp? Which version of Ubuntu are you using? Did you update JACK maybe? It is supposed to be */usr/bin/jackd* instead of *jackdmp*.

---

### Post by Philip133 on 2010-03-07
I'm using kubuntu 9.10, I don't really get what's happening.
Anyway, I changed the server path to what you said, and here's what it gives me:



[[IMG]http://img715.imageshack.us/img715/9308/snapshot2s.png[/IMG]]("http://img715.imageshack.us/i/snapshot2s.png/")

Thanks for the reply, though :)

---

### Post by AutoStatic on 2010-03-07
It's */usr/bin/jackd* (not *usr/bin/jackd*)
Could you post the output of the terminal command **jackd --version** ?

---

### Post by Philip133 on 2010-03-07
```
$ jackd --version
jackdmp 1.9.5
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2009 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
jackdmp version 1.9.5 tmpdir /dev/shm protocol 7

```

And when I tried /usr/bin/jackd it gave me this, and went on and on trying to connect:
```

 p, li { white-space: pre-wrap; }  18:02:19.559 Patchbay deactivated.
 18:02:19.566 Statistics reset.
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 18:02:19.623 ALSA connection graph change.
 18:02:19.809 ALSA connection change.
 18:02:28.229 JACK is starting...
 18:02:28.230 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n2
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 18:02:28.272 JACK was started with PID=3372.
 no message buffer overruns
 jackd 0.116.1
 Copyright 2001-2005 Paul Davis and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK compiled with System V SHM support.
 loading driver ..
 SSE2 detected
 apparent rate = 44100
 creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
 control device hw:0
 configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 2 periods
 ALSA: final selected sample format for capture: 32bit integer little-endian
 ALSA: use 2 periods for capture
 ALSA: final selected sample format for playback: 32bit integer little-endian
 ALSA: use 2 periods for playback
 18:02:29.275 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 18:02:36.205 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 18:02:39.433 JACK is stopping...
 jack main caught signal 15
 18:02:39.468 JACK was stopped successfully.
 18:02:39.469 Post-shutdown script...
 18:02:39.469 killall jackd
 jackd: no process found
 18:02:39.927 Post-shutdown script terminated with exit status=256.

```

---

### Post by AutoStatic on 2010-03-07
Ah, jackdmp 1.9.5. That's not in any standard repository. So you must have installed it from a PPA or compiled it yourself. You can't recall having done anything like that?

---

### Post by Philip133 on 2010-03-07
I had a friend install it for me. I don't really know what he did :|
In the end we couldn't get it to work.

Would it work if I tried to uninstall/remove jack and install it thourgh synaptic?

---

### Post by AutoStatic on 2010-03-08
> **Philip133 said:**
> Would it work if I tried to uninstall/remove jack and install it thourgh synaptic?Yes, that will work. Make sure you remove anything related to Jack2 (jackdmp is often referred to as Jack2 while jackd is often called Jack1). If you have any doubts about what to remove don't hesitate to ask, you don't want to cripple your system by removing something essential.

---

### Post by Philip133 on 2010-03-09
So, I ran
sudo apt-get -f install

then
sudo apt-get remove jackd
I let it uninstall all the dependencies, and then installed it again:
sudo apt-get install jackd

Now when I try to start jack with qjackctl it gives me this in the message window:

```
  p, li { white-space: pre-wrap; }  [COLOR=#999999]16:37:20.542 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]16:37:20.554 Statistics reset.[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 [COLOR=#66CC99]16:37:20.578 ALSA connection graph change.[/COLOR]
 [COLOR=#CCCC99]16:37:20.772 ALSA connection change.[/COLOR]
 [COLOR=#999999]16:37:44.380 JACK is starting...[/COLOR]
 [COLOR=#990099]16:37:44.381 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n2[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 no message buffer overruns
 jackd 0.116.1
 Copyright 2001-2005 Paul Davis and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK compiled with System V SHM support.
 loading driver ..
 SSE2 detected
 apparent rate = 44100
 creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
 control device hw:0
 [COLOR=#999999]16:37:44.429 JACK was started with PID=5164.[/COLOR]
 configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 2 periods
 ALSA: final selected sample format for capture: 32bit integer little-endian
 ALSA: use 2 periods for capture
 ALSA: final selected sample format for playback: 32bit integer little-endian
 ALSA: use 2 periods for playback
 [COLOR=#FF0000]16:37:45.560 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 [COLOR=#999999]16:37:48.537 JACK is stopping...[/COLOR]
 jack main caught signal 15
 [COLOR=#999999]16:37:48.585 JACK was stopped successfully.[/COLOR]
 [COLOR=#999999]16:37:48.585 Post-shutdown script...[/COLOR]
 [COLOR=#990099]16:37:48.585 killall jackd[/COLOR]
 jackd: no process found
 [COLOR=#999999]16:37:48.999 Post-shutdown script terminated with exit status=256.[/COLOR]

```

If this fails, is there any way to run ardour without jack?

---

### Post by AutoStatic on 2010-03-09
You will first have to find out how JACK was installed in the first place. Did you, or the person who has installed it, use a package, a PPA or compile it yourselves?
And Ardour needs JACK.

---

### Post by Philip133 on 2010-03-09
It turns out he compiled it.
I understand that there's a different way of removing compiled programs than synaptic, so, what is it?

Also, thanks for helping me out so far :)

---

### Post by AutoStatic on 2010-03-10
> **Philip133 said:**
> It turns out he compiled it.
I understand that there's a different way of removing compiled programs than synaptic, so, what is it?You can either try removing all files manually or check what compile routine JACK uses. If it's in the order of ./configure make, make install, then you could try cd'ing into the directory in which JACK was compiled and do a **sudo make uninstall**. This should remove all the files that were installed with make install. But maybe JACK uses another tool/framework to compile (scons, waf, cmake), not sure, never compiled JACK myself.
Be very careful with the first option though (removing things manually). Maybe it's better to find out first where certain files reside. What does **find /usr/bin /usr/lib /usr/include -name *jack*** say?

---

### Post by Philip133 on 2010-03-10
[B]find /usr/bin /usr/lib /usr/include -name *jack*

[/B]```
$ find /usr/bin /usr/lib /usr/include -name *jack*
/usr/bin/jack_lsp                                                 
/usr/bin/jack-dssi-host                                           
/usr/bin/jack.plumbing                                            
/usr/bin/qjackctl                                                 
/usr/bin/jack.clock                                               
/usr/bin/jack_load                                                
/usr/bin/jack_impulse_grabber                                     
/usr/bin/jack_netsource                                           
/usr/bin/jack_showtime                                            
/usr/bin/jack_freewheel                                           
/usr/bin/jack_midiseq                                             
/usr/bin/jackrec                                                  
/usr/bin/jack_connect                                             
/usr/bin/jack_transport                                           
/usr/bin/jack_alias                                               
/usr/bin/jack.scope                                               
/usr/bin/jack_unload                                              
/usr/bin/jack-rack                                                
/usr/bin/jackd                                                    
/usr/bin/jack_midisine                                            
/usr/bin/qjackctl.bin                                             
/usr/bin/jacksum                                                  
/usr/bin/jack.ctl                                                 
/usr/bin/jack.udp                                                 
/usr/bin/jack_metro                                               
/usr/bin/jack_transport_client                                    
/usr/bin/jack_simple_client                                       
/usr/bin/jack_monitor_client
/usr/bin/jack.play
/usr/bin/jackbeat
/usr/bin/jack_evmon
/usr/bin/jackeq
/usr/bin/jack_disconnect
/usr/bin/calfjackhost
/usr/lib/audacious/Output/jackout.so
/usr/lib/libjack.so.0.0.28
/usr/lib/csound/plugins64-5.2/libjackTransport.so
/usr/lib/csound/plugins64-5.2/librtjack.so
/usr/lib/libjackserver.so.0
/usr/lib/libjack0.100.0
/usr/lib/libjack.so.0
/usr/lib/libjack-0.100.0.so.0
/usr/lib/libjackserver.so.0.0.28
/usr/lib/jack
/usr/lib/jack/jack_net.so
/usr/lib/jack/jack_alsa.so
/usr/lib/jack/jack_freebob.so
/usr/lib/jack/jack_dummy.so
/usr/lib/jack/jack_oss.so
/usr/lib/jack/jack_firewire.so

```

I can't find the directory.
I could get the links and download the source, and then uninstall.

---

### Post by AutoStatic on 2010-03-10
Thanks! And what's the output of **find /usr/local/bin /usr/local/lib /usr/local/include -name *jack*** ? Probably you have the compiled version and the version from Synaptic installed next to each other. That could be a cause why JACK doesn't work.

---

### Post by Philip133 on 2010-03-10
> **AutoStatic said:**
> Thanks! And what's the output of **find /usr/local/bin /usr/local/lib /usr/local/include -name *jack*** ? 
```
$ find /usr/local/bin /usr/local/lib /usr/local/include -name *jack*
/usr/local/bin/jack_lsp                                                             
/usr/local/bin/jack_wait                                                            
/usr/local/bin/jack_multiple_metro                                                  
/usr/local/bin/jack_load                                                            
/usr/local/bin/jack_netsource                                                       
/usr/local/bin/jack_showtime                                                        
/usr/local/bin/jack_freewheel                                                       
/usr/local/bin/jack_midiseq                                                         
/usr/local/bin/jack_connect                                                         
/usr/local/bin/jack_transport                                                       
/usr/local/bin/jack_alias                                                           
/usr/local/bin/jack_samplerate                                                      
/usr/local/bin/jack_unload                                                          
/usr/local/bin/jackd                                                                
/usr/local/bin/jack_midisine                                                        
/usr/local/bin/jack_rec                                                             
/usr/local/bin/jack_cpu_load                                                        
/usr/local/bin/jack_bufsize                                                         
/usr/local/bin/jack_metro                                                           
/usr/local/bin/jack_server_control                                                  
/usr/local/bin/jack_simple_client                                                   
/usr/local/bin/jack_control                                                         
/usr/local/bin/jack_monitor_client                                                  
/usr/local/bin/jack_zombie                                                          
/usr/local/bin/jack_cpu                                                             
/usr/local/bin/jack_evmon                                                           
/usr/local/bin/jack_thru                                                            
/usr/local/bin/jack_disconnect                                                      
/usr/local/bin/jack_delay                                                           
/usr/local/bin/jack_test                                                            
/usr/local/lib/share/man/man1/jack_netsource.1                                      
/usr/local/lib/share/man/man1/jack_monitor_client.1                                 
/usr/local/lib/share/man/man1/jack_transport.1                                      
/usr/local/lib/share/man/man1/jack_freewheel.1                                      
/usr/local/lib/share/man/man1/jackd.1                                               
/usr/local/lib/share/man/man1/jackrec.1                                             
/usr/local/lib/share/man/man1/jack_bufsize.1                                        
/usr/local/lib/share/man/man1/jack_samplerate.1                                     
/usr/local/lib/share/man/man1/jack_impulse_grabber.1                                
/usr/local/lib/share/man/man1/jack_connect.1                                        
/usr/local/lib/share/man/man1/jack_load.1                                           
/usr/local/lib/share/man/man1/jack_wait.1                                           
/usr/local/lib/share/man/man1/jack_showtime.1                                       
/usr/local/lib/share/man/man1/jack_metro.1                                          
/usr/local/lib/share/man/man1/jack_lsp.1                                            
/usr/local/lib/share/man/man1/jack_unload.1                                         
/usr/local/lib/share/man/man1/jackstart.1                                           
/usr/local/lib/share/man/man1/jack_disconnect.1                                     
/usr/local/lib/lib64/libjack.so.0.0.28                                              
/usr/local/lib/lib64/libjackserver.so                                               
/usr/local/lib/lib64/libjackserver.la                                               
/usr/local/lib/lib64/libjackserver.so.0                                             
/usr/local/lib/lib64/libjack.so                                                     
/usr/local/lib/lib64/libjack.la                                                     
/usr/local/lib/lib64/libjack.so.0                                                   
/usr/local/lib/lib64/pkgconfig/jack.pc                                              
/usr/local/lib/lib64/libjackserver.so.0.0.28                                        
/usr/local/lib/lib64/jack                                                           
/usr/local/lib/lib64/jack/jack_net.so                                               
/usr/local/lib/lib64/jack/jack_net.la                                               
/usr/local/lib/lib64/jack/jack_alsa.la                                              
/usr/local/lib/lib64/jack/jack_oss.la                                               
/usr/local/lib/lib64/jack/jack_alsa.so                                              
/usr/local/lib/lib64/jack/jack_dummy.so                                             
/usr/local/lib/lib64/jack/jack_dummy.la                                             
/usr/local/lib/lib64/jack/jack_oss.so                                               
/usr/local/lib/include/jack                                                         
/usr/local/lib/include/jack/weakjack.h                                              
/usr/local/lib/include/jack/jack.h                                                  
/usr/local/lib/libjack.so.0.1.0                                                     
/usr/local/lib/libjackserver.so                                                     
/usr/local/lib/libjackserver.so.0                                                   
/usr/local/lib/libjack.so                                                           
/usr/local/lib/bin/jack_lsp                                                         
/usr/local/lib/bin/jack_wait                                                        
/usr/local/lib/bin/jack_load                                                        
/usr/local/lib/bin/jack_impulse_grabber                                             
/usr/local/lib/bin/jack_netsource                                                   
/usr/local/lib/bin/jack_showtime                                                    
/usr/local/lib/bin/jack_freewheel                                                   
/usr/local/lib/bin/jack_midiseq                                                     
/usr/local/lib/bin/jackrec                                                          
/usr/local/lib/bin/jack_connect                                                     
/usr/local/lib/bin/jack_transport                                                   
/usr/local/lib/bin/jack_alias
/usr/local/lib/bin/jack_samplerate
/usr/local/lib/bin/jack_unload
/usr/local/lib/bin/jackd
/usr/local/lib/bin/jack_midisine
/usr/local/lib/bin/jack_bufsize
/usr/local/lib/bin/jack_metro
/usr/local/lib/bin/jack_transport_client
/usr/local/lib/bin/jack_simple_client
/usr/local/lib/bin/jack_monitor_client
/usr/local/lib/bin/jack_evmon
/usr/local/lib/bin/jack_disconnect
/usr/local/lib/libjackserver.so.0.1.0
/usr/local/lib/libjack.so.0
/usr/local/lib/pkgconfig/jack.pc
/usr/local/lib/jack
/usr/local/lib/jack/jack_net.so
/usr/local/lib/jack/jack_netone.so
/usr/local/lib/jack/jack_alsa.so
/usr/local/lib/jack/jack_dummy.so
/usr/local/lib/jack/jack_loopback.so
/usr/local/include/jack
/usr/local/include/jack/weakjack.h
/usr/local/include/jack/jack.h

```

> **AutoStatic said:**
> Probably you have the compiled version and the version from Synaptic installed next to each other.
I think that's it, however I don't feel very confident saying that (I've just switched from windows, and I know almost nothing on linux).

Also, when I uninstall jack through synaptic, all the links (icons) in Kickoff disappear. Doesn't this mean that there is no jack left on the PC?

---

### Post by AutoStatic on 2010-03-10
You have two versions of JACK installed, one in /usr (the one from Synaptic) and one in /usr/local (the compiled version). There are two things you could do, use the compiled version of JACK and purge (uninstalling won't suffice) the one from Synaptic or get rid of the compiled version and use JACK from Synaptic. Uninstalling JACK in Synaptic doesn't mean there's no more JACK, the compiled version will still sit there in /usr/local
Personally I think it's best to try to get the compiled version in /usr/local going. So could you try purging ('Mark for complete removal' in Synaptic) JACK? The packages you need to purge are **jackd** and **libjack**. After that try running QjackCtl with /usr/local/bin/jackd as the server path for JACK.

---

### Post by Philip133 on 2010-03-10
I've removed the packages, but now I don't have qjackctl installed. It wouldn't let me remove jackd without removing all the associated packages :/
So I'm stuck with nothing right now.

I think it'll  be easier to get the synaptic version of jack running (I'm assuming that just deleting the files from the compiled one would be enough?).

---

### Post by AutoStatic on 2010-03-10
> **Philip133 said:**
> I think it'll  be easier to get the synaptic version of jack running (I'm assuming that just deleting the files from the compiled one would be enough?).That's another option. But I won't recommend it within the scope of this forum. You need to do it as root namely and there's always a chance that you delete the wrong files and/or directories. So yes, you could try it, but it's at your own risk. And to drag in the-scope-of-this-forum thing again, I won't help you with it, sorry :(

---

### Post by hamx0r on 2010-03-10
Not sure if this helps, but i was having this problem for a few hours until it dawned on me what was happening.  Here's the story:  I installed Ubuntu Studio 9.10 and JACK worked fine, but my USB keyboards (MIDI controllers) did not.  I got the right MIDI controller firmware packages and then JACK stopped working.  I got the same error messages as in the first couple posts of this thread.  Well, what was happening is that before the USB keyboards worked, my Sound Blaster Audigy was hw0, but after the USB stuff kicked in, the keyboards became hw0 and hw1 while my audigy became hw2.  JACK was still trying to use hw0 which is now a USB MIDI controller, so it failed.  All I had to do was configure jack with the GUI to use HW2.0 (or something) and then it worked.  

Hope this helps!

---

### Post by sgx on 2010-03-10
> **Philip133 said:**
> I've removed the packages, but now I don't have qjackctl installed. It wouldn't let me remove jackd without removing all the associated packages :/
So I'm stuck with nothing right now.

I think it'll  be easier to get the synaptic version of jack running (I'm assuming that just deleting the files from the compiled one would be enough?).
Hi, its time to reinstall. Make a separate /home partion if you don't have one, so in the future you can reinstall without reconfiguring the moon and stars. Backup data/debs/goodies first, or this message will retroactively become beyond the scope of this forum ;)

---

### Post by Philip133 on 2010-03-11
> **AutoStatic said:**
> You need to do it as root namely and there's always a chance that you delete the wrong files and/or directories. So yes, you could try it, but it's at your own risk. And to drag in the-scope-of-this-forum thing again, I won't help you with it, sorry :(
Alright, no prob with that, I understand that whatever I screw up with the deleting could possibly make Kubuntu unusable.

Now, for the files, I need to delete the ones that **find /usr/local/bin /usr/local/lib /usr/local/include -name *jack* **gives me, right?

> **sgx said:**
> Hi, its time to reinstall. Make a separate /home partion if you don't have one, so in the future you can reinstall without reconfiguring the moon and stars. Backup data/debs/goodies first, or this message will retroactively become beyond the scope of this forum ;)

I'd like to, but... I don't have the space to back up. I've got about 250 GB's of free space that I could back up to, and that's assuming I'd uninstall all of the software I have, leaving just the bare OS and my files. And I need at least 600 GB. Too bad I guess, time to get some terabytes :)

EDIT: I did it, all I needed was to delete the files from the compiled jack. Thanks for the help guys :)

---

