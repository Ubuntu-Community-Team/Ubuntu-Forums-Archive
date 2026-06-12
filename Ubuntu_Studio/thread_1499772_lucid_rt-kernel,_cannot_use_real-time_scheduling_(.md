---
title: "lucid: rt-kernel, cannot use real-time scheduling (FIFO at priority 10)"
date: 2010-06-02
forum: Ubuntu Studio
---

### Post by floogy on 2010-06-02
Hi there,

I don't understand why jack dosen't work with pulseaudio. Yesterday it worked like a charm.

pulseaudio -vvv
> 
[...]
Memory locking is unlimited - this is dangerous. You should probably alter the line:
     [COLOR="Magenta"]@audio   -  memlock    unlimited[/COLOR]
in your [COLOR="Magenta"]/etc/limits.conf[/COLOR] to read:
     @audio   -  memlock    2319054
JACK compiled with System V SHM support.
cannot use real-time scheduling (FIFO at priority 10) [for thread -1576884480, from thread -1576884480] (1: Operation not permitted)
cannot create engine
[COLOR="Red"]E: module-jack-source.c: jack_client_open() failed.
E: module.c: Failed to load  module "module-jack-source" (argument: ""): initialization failed.
E: main.c: Module load failed.
E: main.c: Failed to initialize daemon.
I: module.c: Unloading "module-device-restore" (index: #0).[/COLOR]
[...]


> ~$ grep audio /etc/security/limits.conf
#@audio -       rtprio          99
#@audio - [COLOR="Magenta"]memlock unlimited[/COLOR]
#@audio - nice -10
@audio          -       rtprio          99
@audio - [COLOR="SeaGreen"]memlock 2319054[/COLOR]
@audio - nice -10


```
~$ uname -a
Linux ubuntu 2.6.32-22-preempt #33-Ubuntu SMP PREEMPT Wed Apr 28 15:41:26 UTC 2010 x86_64 GNU/Linux

~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

~$ cat bin/jack_startup 
#load pulseaudio jack modules
#!/bin/bash

pactl load-module module-jack-sink
pactl load-module module-jack-source


```

Do I have to log out every time I changed /etc/security/limits.conf and log back in to make the changes take effect?

I today worked on the qjackctl startscript because it failed on line 12 with an error message 
```
/usr/bin/qjackctl: line 12: [: too many arguments
```

It looks now like this (I'm not that good at bash-scripting though):
```
~$ cat `which qjackctl`
#!/bin/sh
PATH=/bin:/usr/bin:/sbin:/usr/sbin
QJACKCTL=$(which qjackctl.bin)
PULSEAUDIO=$(pgrep -f pulseaudio > /dev/null)

if $PULSEAUDIO; then

	PACTL=$(which pactl)
	#JACK=$( $PACTL list | grep jack-sink )
	#JACK=$( $PACTL list | egrep Name\:\ module-jack-sink|awk '{print $2}' )
	#locate module-jack-sink|grep \.so	
	
	JACK=$(locate $( $PACTL list | egrep Name\:\ module-jack-sink|awk '{print $2}' )|grep  \.so)
	JACKPAMODULE=/usr/lib/pulse-0.9.21/modules/module-jack-sink.so
	PASUSPENDER=$(which pasuspender)
	if [ "$($PACTL list 2>&1)" = "Connection failure: Connection refused" ];then
		echo -e "/usr/bin/pactl list:\nConnection failure: Connection refused"
		exit 0
		else if [ -z $JACK ];then
			JACK=notexistant
        		else JACK=$JACK
		fi
	fi
	#if [ $PACTL -a $JACK ]; then
	#if [ [ -x $PACTL ] -a [ -f $JACK ] ]; then
	if  [ -x $PACTL ] && [ $JACKPAMODULE = $JACK ]; then
		echo "Using JACK for audio";
		$QJACKCTL "$@";
	elif [ $PASUSPENDER ]; then
		echo "Suspending PulseAudio";
		$PASUSPENDER -- $QJACKCTL "$@";
	else
		echo "Cannot suspend PulseAudio";
		$QJACKCTL "$@";
		exit 1;
	fi

else

	$QJACKCTL "$@";

fi

```

But I can't see how this affected jackd and limits.conf.

And today I noticed that my changes in limits.conf were altered to nothing by something e.g. some process (apparmor?) I don't know what deleted my @audio lines. Also the jackmodule in pulseaudio say<s something about memlock unlimited and /etc/limits.conf but actually there is /etc/security/limits.conf with  @audio - [COLOR="SeaGreen"]memlock 2319054[/COLOR]

EDIT:

Yesterday this worked also:
```
$ pactl load-module module-jack-sink
Connection failure: Connection refused
```
Today it even doesn't work with sudo
```
$ sudo pactl load-module module-jack-sink
Home directory /home/gerhard not ours.
Connection failure: Connection refused
```

---

### Post by cchhrriiss121212 on 2010-06-02
> Do I have to log out every time I changed /etc/security/limits.conf and log back in to make the changes take effect?
Yeah, you have to do that with any system file edit. I'm not sure about the rest, but you might have more luck with alsa bridge+jack than pulse+jack.

---

### Post by floogy on 2010-06-02
I already did that (logout) because I wasn't sure about it. Though, It's a pitty that one must logout and relogin instead of reloading sth. ;)

I prefer to get pulseaudio to work with jack like yesterday. I completely stuck on that issue.

Ok, I'll try to purge and reinstall the pulseaudio-jack-module, because I renamed one of these libs for testing purposes for my script, and reinstalled it then. I might have to purge it, because jack starts from the commandline using alsa:

```
~$ jackd -d alsa -r
jackd 0.118.0
[...]


Memory locking is unlimited - this is dangerous. You should probably alter the line:
     @audio   -  memlock    unlimited
in your /etc/limits.conf to read:
     @audio   -  memlock    2319054
JACK compiled with System V SHM support.
loading driver ..
Enhanced3DNow! detected
SSE2 detected
apparent rate = 48000
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 48000Hz, period = 1024 frames (21.3 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 16bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 16bit little-endian
ALSA: use 2 periods for playback

**** alsa_pcm: xrun of at least 0.065 msecs

**** alsa_pcm: xrun of at least 0.038 msecs

delay of 2067.000 usecs exceeds estimated spare time of 1577.000; restart ...
```

---

### Post by thorgal on 2010-06-02
do you have a file called 
```

/etc/security/limits.d/audio.conf

```

if yes, I bet you have to modify that file instead :)

---

### Post by floogy on 2010-06-02
THANK YOU! I'll bet that's the culprit!
```
~$ cat /etc/security/limits.d/audio.conf
# generated by jackd's postinst.
#
# Do not edit this file by hand, use
#
#    dpkg-reconfigure -p high jackd
#
# instead.
@audio   -  rtprio     99
@audio   -  memlock    unlimited
#@audio   -  nice      -19

```

I'll definetly try that out!

Hm.. dpkg-reconfigure  -p high jackd comments the @audio   -  nice      -19 out. And it also doesn't have any effect on the pulseaudio -vv jack error.

```
~$ rgrep @audio /etc/ 2>/dev/null
/etc/security/limits.conf:#@audio          -       rtprio          99
/etc/security/limits.conf:#@audio - memlock 1546036 unlimited
/etc/security/limits.conf:#@audio - nice -19
/etc/security/limits.conf:@audio - rtprio 99
/etc/security/limits.conf:@audio - memlock 1546036
/etc/security/limits.conf:@audio - nice -19
/etc/security/limits.conf.dpkg-old:@audio - rtprio 99
/etc/security/limits.conf.dpkg-old:@audio - memlock 250000
/etc/security/limits.conf.dpkg-old:@audio - nice -10
/etc/security/limits.conf-2010-05-02:@audio - rtprio 99
/etc/security/limits.conf-2010-05-02:@audio - memlock 250000
/etc/security/limits.conf-2010-05-02:@audio - nice -10
/etc/security/limits.d/audio.conf:@audio   -  rtprio     99
/etc/security/limits.d/audio.conf:@audio   -  memlock    unlimited
/etc/security/limits.d/audio.conf:@audio   -  nice      -19
```

I'll try to reboot and retry it.

That doesn't help.

With strace I found this line before the error line:
```
connect(17, {sa_family=AF_FILE, path="/dev/shm/jack-1000/default/jack_0"}, 110) = -1 ENOENT (No such file or directory)
```

That's true, but I tried to create that directory already with the appropriate permission, but something deleted it. I'll try that again according this thread:
[http://ubuntuforums.org/showpost.php?p=3471266&postcount=5](http://ubuntuforums.org/showpost.php?p=3471266&postcount=5)

Now I get:
```
JACK compiled with System V SHM support.
cannot remove `/dev/shm/jack-1000' (Operation not permitted)
cannot use real-time scheduling (FIFO at priority 10) [for thread 1861678848, from thread 1861678848] (1: Operation not permitted)
cannot create engine
```

Ok, I changed the ownership to $USER, but then pulseaudio deletes this directory each time it starts up. The error persists.

```

access("/usr/bin/jackd", X_OK)          = 0
pipe2([17, 18], O_CLOEXEC)              = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0x7fcedc4b9a10) = 8419
close(18)                               = 0
fcntl(17, F_SETFD, 0)                   = 0
fstat(17, {st_mode=S_IFIFO|0600, st_size=0, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fcedc382000
read(17, "/dev/shm\n", 4096)            = 9
close(17)                               = 0
wait4(8419, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0, NULL) = 8419
munmap(0x7fcedc382000, 4096)            = 0
open("/proc/cpuinfo", O_RDONLY)         = 17
fstat(17, {st_mode=S_IFREG|0444, st_size=0, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fcedc382000
read(17, "processor\t: 0\nvendor_id\t: Authen"..., 1024) = 563
close(17)                               = 0
munmap(0x7fcedc382000, 4096)            = 0
socket(PF_FILE, SOCK_STREAM, 0)         = 17
getuid()                                = 1000
connect(17, {sa_family=AF_FILE, path="/dev/shm/jack-1000/default/jack_0"}, 110) = -1 ENOENT (No such file or directory)
close(17)                               = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0x7fcedc4b9a10) = 8420
rt_sigprocmask(SIG_BLOCK, [CHLD], [], 8) = 0
rt_sigaction(SIGCHLD, NULL, {SIG_DFL, [], SA_RESTORER, 0x7fcedad9b8f0}, 8) = 0
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
nanosleep({1, 0}, {0, 998518426})       = ? ERESTART_RESTARTBLOCK (To be restarted)
--- SIGCHLD (Child exited) @ 0 (0) ---
restart_syscall(<... resuming interrupted call ...>jackd 0.118.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details


Memory locking is unlimited - this is dangerous. You should probably alter the line:
     @audio   -  memlock    unlimited
in your /etc/limits.conf to read:
     @audio   -  memlock    2319054
JACK compiled with System V SHM support.
cannot use real-time scheduling (FIFO at priority 10) [for thread 1321256704, from thread 1321256704] (1: Operation not permitted)
cannot create engine
```

Is this file a socket or a directory that I should create?
/dev/shm/jack-1000/default/jack_0

Ok, that should be something like a socket:

```
JACK compiled with System V SHM support.
cannot unlink `/dev/shm/jack-1000/default/jack_0' (Is a directory)
cannot remove `/dev/shm/jack-1000/default' (Directory not empty)
cannot use real-time scheduling (FIFO at priority 10) [for thread 857065216, from thread 857065216] (1: Operation not permitted)
cannot create engine
cannot unlink `/dev/shm/jack-1000/default/jack_0' (Is a directory)
cannot remove `/dev/shm/jack-1000/default' (Directory not empty)
E: module-jack-source.c: jack_client_open() failed.
```

I guess I had to start jack first&#8230;

If jack is already started I get a connection error:
```
connect(17, {sa_family=AF_FILE, path="/dev/shm/jack-1000/default/jack_0"}, 110) = -1 ECONNREFUSED (Connection refused)
close(17)    
```

---

### Post by thorgal on 2010-06-02
wow, that's quite some digging you are doing here :)

jack uses some shared memory so that server and clients can work all together. /dev/shm is usually where the shared mem resides.

Not sure why you have issues like this. On my debian machines (pulseaudio-free), all /dev/shm/jack* is owned by me (not root or other user / group than mine).

---

### Post by floogy on 2010-06-02
I created the folders according to this:
[http://ubuntuforums.org/showpost.php...66&postcount=5](http://ubuntuforums.org/showpost.php...66&postcount=5)

But I figured out that they are created by jackd. Therefore I tried to start jack before pulseaudio, but then I get the connection error&#8230; I'll purge now pulseaudio and reinstall it.

That did the trick. Now everything is working fine again. It's mysterious to me what happened.

BTW: I changed the qjackctl to this now (This isn't related to the error):

~$ cat  `which qjackctl`
```
#!/bin/sh
PATH=/bin:/usr/bin:/sbin:/usr/sbin
QJACKCTL=$(which qjackctl.bin)
PULSEAUDIO=$(pgrep -f pulseaudio > /dev/null)

#if $PULSEAUDIO; then # Wrong exit status test of pgrep, better use this:
if [ $? -eq 0 ]; then


	PACTL=$(which pactl)
	JACKPAMODULE=$(dpkg -L pulseaudio-module-jack|grep module-jack-sink.so)
	
        if [ -f $JACKPAMODULE ];then
		#load pulseaudio jack modules
		pactl load-module module-jack-sink
		pactl load-module module-jack-source
			else 
			echo -e "Please install $(dpkg -S $JACKPAMODULE)"
			exit 0
        fi

	JACK=$(locate $( $PACTL list | egrep Name\:\ module-jack-sink|awk '{print $2}' )|grep  \.so)

	PASUSPENDER=$(which pasuspender)
	if [ "$( $PACTL list 2>&1)" = "Connection failure: Connection refused" ];then
		echo -e "/usr/bin/pactl list:\nConnection failure: Connection refused"
		exit 0
		else if [ -z $JACK ];then
			JACK=notexistant
        		else JACK=$JACK
		fi
	fi

	if [ $JACKPAMODULE = $JACK ]; then
	echo "Using JACK for audio";
		$QJACKCTL "$@";
	elif [ $PASUSPENDER ]; then
		echo "Suspending PulseAudio";
		$PASUSPENDER -- $QJACKCTL "$@";
	else
		echo "Cannot suspend PulseAudio";
		$QJACKCTL "$@";
		exit 1;
	fi

else

	$QJACKCTL "$@";

fi


```

---

### Post by floogy on 2010-06-02
I'm afraid, that this is all wrong, because jackd must be started before pulseaudio to load the module-jack-sink and module-jack-source. 

But I don't know how to reactivate pulsaudio after stopping jack.

EDIT: Ok, this prevents qjackctl to give the "too many arguments" or "unary operator expected" error:```
/usr/bin/qjackctl: line 12: [: too many arguments
```

```


$ diff  -u qjackctl.orig qjackctl
--- qjackctl.orig	2010-06-02 22:55:02.000000000 +0200
+++ qjackctl	2010-06-02 23:09:43.000000000 +0200
@@ -3,16 +3,17 @@
 QJACKCTL=$(which qjackctl.bin)
 PULSEAUDIO=$(pgrep -f pulseaudio > /dev/null)
 
-if $PULSEAUDIO; then
+if [ $? -eq 0 ]; then
+
 
 	PACTL=$(which pactl)
 	JACK=$($PACTL list | grep jack-sink)
 	PASUSPENDER=$(which pasuspender)
 
-	if [ $PACTL -a $JACK ]; then
+	if [ "$PACTL" -a "$JACK" ]; then
 		echo "Using JACK for audio";
 		$QJACKCTL "$@";
-	elif [ $PASUSPENDER ]; then
+	elif [ -x $PASUSPENDER ]; then
 		echo "Suspending PulseAudio";
 		$PASUSPENDER -- $QJACKCTL "$@";
 	else


```

---

