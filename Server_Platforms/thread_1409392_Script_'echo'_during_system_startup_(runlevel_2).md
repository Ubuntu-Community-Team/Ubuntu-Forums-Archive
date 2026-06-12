---
title: "Script 'echo' during system startup (runlevel 2)"
date: 2010-02-17
forum: Server Platforms
---

### Post by Freresine on 2010-02-17
Hi All, 

I have created a new script that I am executing at system startup. All was going well until the last step... see below

1. Create script  **mytestscript.sh**
2. Made executable
3. Test script from command line. Works no problem
    At this stage it is very basic, just a few echo's and some initialization info
    Each echo also logs output to a .log file
4. Copy script to /etc/init.d
5. Updated runlevels
[COLOR=#000000][FONT=Arial][COLOR=#0000ff]sudo update-rc.d mytestscript.sh[/COLOR][COLOR=#0000ff] defaults[/COLOR][/FONT][/COLOR]

Then restarted the system...
The system comes up and does execute my script as I can see the output in my logfile...
BUT... my echo's are not displaying on the console.

I have attached a simple example script (without logging) but which also does not echo to the console.

My system
VMWare Server 2 running Ubuntu 9.10

I am stumped...  any thoughts to help please...

Thanks

---

### Post by koenn on 2010-02-17
the script you attached doesn't run **at all**

first error is this:
```

bash: /home/kn/Desktop/sbc-test.sh: /bin/bash^M: bad interpreter: No such file or directory

```
it's because of the ^M -you probably did not create this on a linux system.
After I fixed that, there's some more problems :

```

: command not foundc-test.sh: line 15: 
: command not foundc-test.sh: line 16: 
: command not foundc-test.sh: line 17: 
: command not foundc-test.sh: line 18: 
: command not foundc-test.sh: line 19: 
: command not foundc-test.sh: line 20: 
: command not foundc-test.sh: line 21: 
: command not foundc-test.sh: line 22: 
: command not foundc-test.sh: line 23: 
: command not foundc-test.sh: line 24: 

'home/kn/Desktop/sbc-test.sh: line 25: syntax error near unexpected token `in 'home/kn/Desktop/sbc-test.sh: line 25: `case "$1" in

```
These are probably just more of those ^M line breaks.

The last one is more interesting : the 'start' case is the one that needs to run during system boot, so if your case statement is no good, the thing won't show during startup. 

of course, in the real script, everything could be different.

---

### Post by Freresine on 2010-02-17
Hi koenn,

Thanks for the reply...

Ubuntu is running in a VM on my main machine which is windows. When I transferred the file from linux to my machine to put onto the forum it would have translated the 
LF to CR/LF (^M).

This would be the only difference to the actual script executing on the server.

thanks.

---

### Post by sisco311 on 2010-02-17
Try to redirect the output of the echo command to stderr:
```
echo "whatever" 1>&2
```

---

### Post by Freresine on 2010-02-17
I have tried as you suggested. No luck.

I have also added back logging to a file.

When I restart the system the log file gets updated as expected... so the script is definitely being executed.

The echo's are just not displaying on the console....

I have attached the latest version of the script with the logging to a file.

---

### Post by Freresine on 2010-02-18
Could this be anything to do with the change to upstart? Using upstart you have to specify that you want to enable output to the console...
Is this somehow redirecting my echo output to some other device?

Thoughts?

---

### Post by koenn on 2010-02-18
> **Freresine said:**
> Could this be anything to do with the change to upstart? Using upstart you have to specify that you want to enable output to the console...
Is this somehow redirecting my echo output to some other device?

Thoughts?
not unlikely.
If your script actually runs at startup, re the entries in the output file, then it runs. and normal init scripts would echo to your screen no problem. 
It's worth looking in to, but I can't tell you where to look.


Edit
oh, wait  - I was thinking servers
if you're doing this on a desktop or so, the output of init scripts would be hidden behind the splash screen :-)
[http://en.wikipedia.org/wiki/Usplash](http://en.wikipedia.org/wiki/Usplash)

---

### Post by Freresine on 2010-02-19
Have resolved this.... finally. Was driving me mad and am still not a entirely sure why this works, but I will leave that for later...

Solution as follows:
On Ubuntu (and Debian) they have been trying to standardize the system start-up scripts and to do this they have
1. Published various standards to follow  **SEE**: [wiki.debian.org/LSBInitScripts]("http://wiki.debian.org/LSBInitScripts")
2. Your scripts need to adhere to the standards
3. And then it seems, to ensure this standardisation they have made a library of scripts with various functions to be called that will then publish to the console for you.
And it is this part that does not seem to be well documented.
The library is located at :
      [COLOR=Blue]/lib/lsb/init-functions[/COLOR]

I used functions:
   log_daemon_msg
   log_action_msg

And suddenly I my console was being updated on start-up.

--------------------------------------------
They have also made an example available:
[COLOR=Blue]/etc/init.d/skeleton[/COLOR]
--------------------------------------------

What is odd is that the function "log_action_msg" simply does an "echo" and when I do the same thing (a simple echo) it does not work. Very mysterious...
But for the moment it works... I will figure out the *why* later...

Thanks all for the comments....

---

### Post by koenn on 2010-02-20
glad you got it, 
and good to know, thanks

---

