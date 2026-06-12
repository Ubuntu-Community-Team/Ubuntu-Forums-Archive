---
title: "Make daemon script run in separate thread on startup"
date: 2008-06-26
forum: Server Platforms
---

### Post by _Dan on 2008-06-26
Hi,

Sorry I don't know the correct word, thread is the nearest I could think of...

anyway, I have a script that performs an action every few seconds, so it's an infinite loop.

I want it to run on startup, so I figure linking to it from /etc/init.d will do that.

But my problem is, how do I get it so it doesn't hang the system?

If I started it from the console I'd just do:
./myscript &

but obviously parameters can't be given when it's just a symbolic link or the file.

I guess I could have a script in init.d which does the command ./myscript &

But I was hoping for a cleaner solution, such as a command I could put at the top of the script that would make it fork or whatever it's called.

Is there such a thing?

Thanks ;)

---

### Post by unixbills on 2008-06-26
I don't know how.  Maybe look at exec.  In my opinion the script calling the script is cleaner and or more normal.  Only start/stop control scripts belong in here.  If your code was a binary you wouldn't put it here so this should be no different.

Bill

---

### Post by _Dan on 2008-06-26
Ok, thanks. I guess I'll do the script-calling-script.

And thanks for the reply in the other topic too :)

---

### Post by unixbills on 2008-06-26
You are very welcome but just my opinion. :)

---

### Post by _Dan on 2008-06-27
Ok heeeeeeeeeeeelllllllpppppp. :'(

Why wouldn't this work?

It's in /etc/init.d/
It works fine if I run it after logging in to the terminal. i.e. browsing to /etc/init.d and running ./haxevideo-start.sh

But it just doesn't seem to run on boot! (that is, it does not appear in ps -A and the server is not started)

This is what I have in /etc/init.d/

haxevideo-start.sh
```
#!/bin/bash

# Starts the haxevideo daemon script

echo "Attempting to start the haxevideo daemon script..."

cd /haxevideo/
./serverdaemon.sh &
```

and this is the script in /haxevideo

serverdaemon.sh
```
#!/bin/bash

# this script checks every 6 seconds that haxevideo is running

echo "Started haxevideo daemon script."

while true
do
	
	# see if "neko server.n" is running, start it if it isn't
	started=`ps -ef|grep -v grep|grep "neko server.n"`
	
	if [ -z "$started" ]
	then
		echo "Starting haxevideo server..."
		
		# find the IP
		IPADDR=`ifconfig venet0:0 | awk '/inet/ {print $2}' | sed -e s/addr://`
		
		neko server.n $IPADDR 1935 &
	fi
	sleep 6
done

```

Oh and this is Ubuntu server 7.04.

---

### Post by unixbills on 2008-06-27
You need to link it out to a run level.  It only lives in here.  /etc/rc*.d/.  Maybe try a man on init.  If it starts witha "S" then it starts when that level is entered.  If it start with a "K" it is stopped.  Look at something that does work.  Here is my geronimo script.

(I am trying "CODE" tags so lets see if this works.  I am new to this part)

```

user@host:$ ls -l /etc/rc*.d/*geronimo /etc/init.d/geronimo
-rwxr-xr-x 1 root root 993 2008-06-24 14:02 /etc/init.d/geronimo
lrwxrwxrwx 1 root root  18 2008-06-24 14:49 /etc/rc0.d/K01geronimo -> ../init.d/geronimo
lrwxrwxrwx 1 root root  18 2008-06-24 14:49 /etc/rc1.d/K01geronimo -> ../init.d/geronimo
lrwxrwxrwx 1 root root  18 2008-06-24 14:49 /etc/rc2.d/S99geronimo -> ../init.d/geronimo
lrwxrwxrwx 1 root root  18 2008-06-24 14:49 /etc/rc3.d/S99geronimo -> ../init.d/geronimo
lrwxrwxrwx 1 root root  18 2008-06-24 14:49 /etc/rc4.d/S99geronimo -> ../init.d/geronimo
lrwxrwxrwx 1 root root  18 2008-06-24 14:49 /etc/rc5.d/S99geronimo -> ../init.d/geronimo
lrwxrwxrwx 1 root root  18 2008-06-24 14:49 /etc/rc6.d/K01geronimo -> ../init.d/geronimo

```

Bill

---

### Post by unixbills on 2008-06-27
I should have added more.  So when you enter run level 2-5 (like on boot) the script starts with "S" so it gets passes a start like "geronimo start".  And when you enter run level 6, 0, or 1 (shutdown) the script name start with a "K" so it gets passes a stop like "geronimo stop".

I am not really up on Linux init or Ubuntu upstart but this is a typical init sequence.  Linux has more then just start and stop but this is the general idea.

---

### Post by unixbills on 2008-06-27
Take a look at this [http://www.faqs.org/docs/linux_scratch/chapter07/usage.html](http://www.faqs.org/docs/linux_scratch/chapter07/usage.html)

---

### Post by _Dan on 2008-06-27
Thanks Bill :) 

My only problem now is that the program "neko" is not starting (and the daemon is trying every 6 seconds after boot as expected)

I've been outputting stuff to a log file, and everything else works, $IPADDR is found correctly.

I tried removing the parameters to neko, just doing
neko >> /var/log/haxeserverlog

but nothing is output :/ 
(normally neko would write a line saying the program version etc..)

But maybe I should ask about this on the neko mailing lists.

---

### Post by _Dan on 2008-06-27
No problem, fixed it. Added these to the top:

```
export LD_LIBRARY_PATH=/usr/lib/neko
export PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/lib/neko
export NEKOPATH=/usr/lib/neko
```

(not sure exactly which part does the trick, just randomly copied from neko mailing lists and other places. But it works!)

Thanks again for your help :)

---

