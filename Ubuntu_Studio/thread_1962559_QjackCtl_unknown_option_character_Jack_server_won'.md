---
title: "QjackCtl unknown option character: Jack server won't start"
date: 2012-04-21
forum: Ubuntu Studio
---

### Post by HuaiDan on 2012-04-21
Greetings. The latest episode of my Jack saga has yielded some important clues as to why the server won't start. 
Running Natty AMD64

Message output from QjackCtl reads thus:
> 17:13:02.753 Patchbay activated.
17:13:02.777 Statistics reset.
17:13:02.791 ALSA connection change.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
17:13:02.803 ALSA connection graph change.
17:13:02.998 ALSA active patchbay scan...
17:13:06.303 JACK is starting...
17:13:06.303 /usr/bin/jackd -P80 -t5000 -dalsa -dhw:1 -r44100 -p128 -n3 -Xseq -D -Phw:0
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
17:13:06.359 JACK was started with PID=4543.
unknown option character jackdmp 1.9.7
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
usage: jackdmp [ --no-realtime OR -r ]
               [ --realtime OR -R [ --realtime-priority OR -P priority ] ]
      (the two previous arguments are mutually exclusive. The default is --realtime)
               [ --name OR -n server-name ]
               [ --timeout OR -t client-timeout-in-msecs ]
               [ --loopback OR -L loopback-port-number ]
               [ --port-max OR -p maximum-number-of-ports]
               [ --midi OR -X midi-driver ]
               [ --verbose OR -v ]
               [ --clocksource OR -c [ c(ycle) | h(pet) | s(ystem) ]
               [ --replace-registry ]
               [ --silent OR -s ]
               [ --sync OR -S ]
               [ --temporary OR -T ]
               [ --version OR -V ]
         -d backend [ ... backend args ... ]
               Available backends may include: alsa, dummy, freebob, firewire or net
       jackdmp -d backend --help
             to display options for each backend
17:13:06.445 JACK was stopped with exit status=255.
17:13:08.403 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
Note the following lines:
> /usr/bin/jackd -P80 -t5000 -dalsa -dhw:1 -r44100 -p128 -n3 -Xseq -D -Phw:0
...

unknown option character jackdmp 1.9.7

When I try to run this at the command prompt,
> 
jackd -P80 -t5000 -dalsa -dhw:1 -r44100 -p128 -n3 -Xseq -D -Phw:0

it looks like it's going to start, but then after starting a sound app (ardour, fmit)  throws the error:

> JackProcessSync::LockedTimedWait error usec = 5000000 err = Connection timed out
Driver is not running
Cannot create new client
jackd: ../common/JackGraphManager.cpp:45: void Jack::JackGraphManager::AssertPort(jack_port_id_t): Assertion `port_index < fPortMax' failed.
Aborted


Content of the .jackdrc file is as follows:
> /usr/bin/jackd -T -P 80 -d alsa -d hw:1 -r 44100 -p 128 -n 3 -D -P hw:0 -X seq -H

I put the spaces in the arguments myself, but they appear to have little effect. When I run that line in shell, it throws the same error when I start a sound app.


I find it a little suspicious that there are two -d arguments, but the man page says that both backend **driver** and input **device** use the -d argument. Yes, I do want hw:1 (a digitech rp500 effects pedal) as the input.

Been at it off and on for months now. I have it working as desired under lucid, but I really would like to get it working under Natty because that's the build I use.

How do I get this thing started?

---

### Post by HuaiDan on 2012-04-21
Got it to connect by deleting /home/user/.config/rncbc.org/QjackCtl.conf,
removing and reinstalling all Jack related files and dependencies, and starting from scratch. The problem was probably due to copying over settings and conf files from the Lucid install, which may have been incompatible with this version

---

### Post by sgx on 2012-04-21
Hi, the .jackdrc file is written by qjackctl each time you
save its settings. I think the multiple -d arguments were a
problem. I use 1000 for midi timing, to help windows apps I
run, the default is much lower, and may be fine.

[http://linux.die.net/man/1/jackd](http://linux.die.net/man/1/jackd)

this handy page lists the command options.

But the -R option has changed in jackd2, where rt is on by default, and is turned off by -R

Cheers

---

### Post by chkneater on 2012-05-30
One thing I did notice in the Jack message was this:

usage: jackdmp [ --no-realtime OR -r ]
[ --realtime OR -R [ --realtime-priority OR -P priority ] ]
(the two previous arguments are mutually exclusive. The default is --realtime)

following this syntax error:  unknown option character jackdmp 1.9.7

My guess is that Realtime and noRealtime are being executed at startup, either by command line or by script.

Start jack and check the Setup and make sure there is not a conflict, I don't think this will solve your ENTIRE prob. it should help untangle it.

---

