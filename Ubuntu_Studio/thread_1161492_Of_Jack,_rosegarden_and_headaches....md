---
title: "Of Jack, rosegarden and headaches..."
date: 2009-05-16
forum: Ubuntu Studio
---

### Post by Warthaug on 2009-05-16
I just recently replaced my former ubuntu (8.something) with 9.04 (64 bit).  In the previous install I had rosegarden working - mostly.  I've been trying to get it to work in the new install, following this guide:

[http://www.funnestra.org/ubuntu/intrepid/#rosegarden](http://www.funnestra.org/ubuntu/intrepid/#rosegarden)

I've installed:
1) Rosegarden
2) Jack
3) Fluidsynth & sound fonts

In the past I got rosegarden to work by first starting jack, then fluidsynth, and finally rosegarden itself.  But for reasons I don't understand, I cannot get jack to start the server.  I checked off the "Start jack audio server on application startup" box under the setup menu, but all I get is errors.

But when I start Jack I get a pop-up error, and the following in a  pop-up message window:

Error:
> 
Could not start Jack server as client.
-Overall operation failed
-Unable to connect to server
Please check the message window for more info

The entirety of the message window reads:
> 
18:59:34.534 Patchbay deactivated.
18:59:34.549 Statistics reset.
18:59:34.690 Startup script...
18:59:34.691 artsshell -q terminate
18:59:34.695 ALSA connection graph change.
sh: artsshell: not found
18:59:35.167 Startup script terminated with exit status=32512.
18:59:35.168 JACK is starting...
18:59:35.168 /usr/bin/jackd -R -dalsa -dhw:0 -r44100 -p1024 -n2
18:59:35.217 JACK was started with PID=4578.
no message buffer overruns
18:59:35.377 ALSA connection change.
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
[COLOR="Red"]cannot use real-time scheduling (FIFO at priority 10) [for thread -1001838864, from thread -1001838864] (1: Operation not permitted)
cannot create engine[/COLOR]
18:59:35.423 JACK was stopped successfully.
18:59:35.424 Post-shutdown script...
18:59:35.424 killall jackd
jackd: no process killed
18:59:35.872 Post-shutdown script terminated with exit status=256.
18:59:37.423 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.

I suspect my problem has something to do with the stuff I highlighted in red, but I'm far from an expert when it comes to these things.

Any help?

Bryan

---

### Post by dawiba on 2009-05-17
I'm no expert, but it looks like you might need to install the realtime kernel or else you can untick the Realtime option in Jack Setup window to use without the realtime kernel.

---

### Post by raboofje on 2009-05-17
> **Warthaug said:**
> cannot use real-time scheduling (FIFO at priority 10) [for thread -1001838864, from thread -1001838864] (1: Operation not permitted)
cannot create engine

Are you in the 'audio' group?

Could you paste your /etc/security/limits.conf ?

---

### Post by Warthaug on 2009-05-17
> **raboofje said:**
> Are you in the 'audio' group?

Which audio group?  If there is a ubuntu one, this is the first I've heard of it...

> **raboofje said:**
> Could you paste your /etc/security/limits.conf ?

With pleasure:

> 
# /etc/security/limits.conf
#
#Each line describes a limit for a user in the form:
#
#<domain>        <type>  <item>  <value>
#
#Where:
#<domain> can be:
#        - an user name
#        - a group name, with @group syntax
#        - the wildcard *, for default entry
#        - the wildcard %, can be also used with %group syntax,
#                 for maxlogin limit
#        - NOTE: group and wildcard limits are not applied to root.
#          To apply a limit to the root user, <domain> must be
#          the literal username root.
#
#<type> can have the two values:
#        - "soft" for enforcing the soft limits
#        - "hard" for enforcing hard limits
#
#<item> can be one of the following:
#        - core - limits the core file size (KB)
#        - data - max data size (KB)
#        - fsize - maximum filesize (KB)
#        - memlock - max locked-in-memory address space (KB)
#        - nofile - max number of open files
#        - rss - max resident set size (KB)
#        - stack - max stack size (KB)
#        - cpu - max CPU time (MIN)
#        - nproc - max number of processes
#        - as - address space limit (KB)
#        - maxlogins - max number of logins for this user
#        - maxsyslogins - max number of logins on the system
#        - priority - the priority to run user process with
#        - locks - max number of file locks the user can hold
#        - sigpending - max number of pending signals
#        - msgqueue - max memory used by POSIX message queues (bytes)
#        - nice - max nice priority allowed to raise to values: [-20, 19]
#        - rtprio - max realtime priority
#        - chroot - change root to directory (Debian-specific)
#
#<domain>      <type>  <item>         <value>
#

#*               soft    core            0
#root            hard    core            100000
#*               hard    rss             10000
#@student        hard    nproc           20
#@faculty        soft    nproc           20
#@faculty        hard    nproc           50
#ftp             hard    nproc           0
#ftp             -       chroot          /ftp
#@student        -       maxlogins       4

# End of file


Bryan

---

### Post by Warthaug on 2009-05-17
> **dawiba said:**
> I'm no expert, but it looks like you might need to install the realtime kernel or else you can untick the Realtime option in Jack Setup window to use without the realtime kernel.

So I deactivated the realtime option in jack, and it now starts properly.  All three programs now start up fine (aside from one error message in rosegarden, about no realtime kernel), but I have no audio output - despite configuring things the way (I think) I had it configured previously...

...Any idea how to work around that?

Bryan

---

### Post by dawiba on 2009-05-18
I can't say for sure about your lack of sound.

I downloaded qsynth and ran it along with jack (with realtime unticked) and rosegarden and was able to get sound after making connections in jack. It worked much better though when using the realtime kernel.

It looks as though raboofje is right though. I suggest you have a look at [Ubuntu Studio Preparation](https://help.ubuntu.com/community/UbuntuStudioPreparation).

It'll take you through the steps you need for 9.04. It certainly worked for me.

---

### Post by raboofje on 2009-05-18
> **Warthaug said:**
> Which audio group?  If there is a ubuntu one, this is the first I've heard of it...

'groups' are a standard linux/unix concepts - they seem to be a tad poorly documented for Ubuntu, but check out [https://help.ubuntu.com/community/AddUsersHowto](https://help.ubuntu.com/community/AddUsersHowto)

Basically, your initial problem was that your user didn't have the permissions needed to run jack in 'realtime' mode. 

Disabling realtime is of course an option, but you might get better performance by installing a realtime kernel, adding yourself to the audio group, and adding some configuration to /etc/security/limits.conf as described [here](https://help.ubuntu.com/community/UbuntuStudioPreparation#Real-Time%20Support) to grant realtime capabilities to the 'audio' group.

---

### Post by Warthaug on 2009-05-19
> **dawiba said:**
> I can't say for sure about your lack of sound.

Turns out my problem is I'm an idiot - soundfonts only work if you load them...downloading isn't quite enough ](*,)

Bryan

---

### Post by Warthaug on 2009-05-19
> **raboofje said:**
> 'groups' are a standard linux/unix concepts - they seem to be a tad poorly documented for Ubuntu, but check out [https://help.ubuntu.com/community/AddUsersHowto](https://help.ubuntu.com/community/AddUsersHowto)

Basically, your initial problem was that your user didn't have the permissions needed to run jack in 'realtime' mode. 

Disabling realtime is of course an option, but you might get better performance by installing a realtime kernel, adding yourself to the audio group, and adding some configuration to /etc/security/limits.conf as described [here](https://help.ubuntu.com/community/UbuntuStudioPreparation#Real-Time%20Support) to grant realtime capabilities to the 'audio' group.

Ahh, I see what you mean.  Rosegarden seems to be doing fine without the realtime kernel, at least to my very out-of-practice ears...

Bryan

---

