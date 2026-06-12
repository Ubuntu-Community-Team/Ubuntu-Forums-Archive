---
title: "vpn momitoring script"
date: 2015-06-26
forum: Security
---

### Post by davaweb on 2015-06-26
I've written this bash script to monitor my vpn connection and kill processes if vpn fails.

I've tested it and it works (so far) but running in terminal I see
> VPN up
1
scrolling continuously. At least I see it is not stuck but it is distracting.
```
#! /bin/bash
#
while true
do
    if /sbin/ifconfig tun0|grep -ci 'UP'
    then
        echo "VPN up"
    else
        killall <process>
        date +"%T"
        read -p "vpn failed - process killed and stopped" nothing
        exit
    fi
done
```
How can the script check the process did actually get killed and what can it do if the process persists?

May I have your opinions please - critical or otherwise?

Many thanks
David

---

### Post by TheFu on 2015-06-26
Ok - you asked. ;)

How about a 5 sec sleep in the loop? A tight loop like this isn't good.
How about reversing the "if" - so you don't need the else and don't need the "echo"

If the result was stored into a variable before the if, then the '1' wouldn't be displayed ... 

I'd read the PID for the vpn process from a file in /var/run/ ... and use that for the kill, not killall. Also, if the vpn is down and that file doesn't exist, wouldn't that mean the VPN isn't running? I dunno, just a thought. With bash scripting, we often do what is quick to code and that is fine too.

Inside every script, it is a best practice to use full-paths to all external commands.

Everyone has a little bit different style for newlines and whitespace - I'd use more ';' more (), and merge a few lines ... 

Is there a better way to see if the VPN is running? I dunno, but checking the output from ifconfig seems odd.

No comments in the code? Really?

Lastly, the displayed indentation is poor - please switch to "code tags" by editing the first post.

---

### Post by davaweb on 2015-06-27
Thanks for your post, TheFu,
Yes - I did ask for it - I want to learn!
I'm very much out of my depth here so if I may ask:
1) a 5 second sleep ... well, monitoring the vpn is critical. I am trying to stop all traffic from certain processes from going in/out unless the vpn is up. That may even have to extend to firefox if banking is occurring. I can't think of any 'constant monitoring' that is not, in effect an endless loop. Maybe I misunderstand how UFW and IPTABLES actually work?
2) I put the echo in so I knew it was still 'working'. Is there a better way?
3) I can't find how to read the PID - that is I can't see the application's pid file listed there.
4) " ...use full-paths to all external commands" - I'm not understanding where I'm not?
5) Point taken about ';' and () - I'm just getting used to the syntax
6) If tun0 doesn't show in ifconfig it's gone so there can't be a vpn connection - as I understand it
7) Comments were take out for the post as it's a very basic script

Can you give me any examples to 'illustrate' your comments please?
Many thanks - very grateful for your comments.
David

---

### Post by TheFu on 2015-06-27
2) Unix "style" says to only complain when something is wrong - never when things work as expected.
4) grep, killall, date .. . need to add the full path to those too, not just ifconfig
5) it is purely a style question - do whatever you prefer.

BTW - the grep statement isn't very specific - 'up/Up/uP/UP' will be matched anywhere in any line - I'd make a longer regex to be conservative that it reports UP only when truly working.  Perhaps checking the routes would be better? I'm just thinking out loud.

An example: [http://blog.jdpfu.com/files/kernel-cleanup.sh](http://blog.jdpfu.com/files/kernel-cleanup.sh)

Note how I use exit codes?   0 = ok ; anything else means something bad.

---

### Post by davaweb on 2015-06-28
I tried testing in another way:```
if [ ! -c /dev/net/tun ] ;
``` but it failed because there was a tun file in /dev/net/ even when not connected to the vpn.

Is there a 'reference' where I can read about the commands and syntax in the script you wrote for linux headers?

I'm not understanding what I'm reading there and 'cut and paste' doesn't help one learn.

Many thanks,

---

### Post by TheFu on 2015-06-28
Almost all commands have manpages - use the **man** command to access those.  **man ifconfig** - for example.  For shell scripting, each shell has a slightly different language, but most are based on Bourne Shell (sh), so if you review a programming reference about that - you get knowledge of how to work with sh, ksh, bash, and other related shells for programming.  There is also The bash scripting guides.
* [http://www.tldp.org/LDP/Bash-Beginners-Guide/html/Bash-Beginners-Guide.html](http://www.tldp.org/LDP/Bash-Beginners-Guide/html/Bash-Beginners-Guide.html)
* [http://www.tldp.org/LDP/abs/html/](http://www.tldp.org/LDP/abs/html/)

and many tutorials around the internet trying to teach bash ... 

* [https://www.howtoforge.com/tutorial/linux-shell-scripting-lessons/](https://www.howtoforge.com/tutorial/linux-shell-scripting-lessons/)
* [https://www.ibm.com/developerworks/library/l-bash/](https://www.ibm.com/developerworks/library/l-bash/)

I learned years ago by reading an O'Reilly book - _UNIX Power Tools_ Linux scripting is NOT different from Unix scripting. We all use bash, ksh, sh ... so those parts are identical. Plus 90% of the external commands are the same - sometimes there are different option or different results, but for the most part grep is grep is grep. If you use more complex regex's, sometimes the regex in older greps is slightly different than the newer ones - also sort has some new options on Linux that haven't made it into Solaris or HP-UX or AIX yet.  But those are edge situations - mostly things are the same.

---

