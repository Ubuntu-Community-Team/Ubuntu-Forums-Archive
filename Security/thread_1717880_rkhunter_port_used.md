---
title: "rkhunter port used"
date: 2011-03-30
forum: Security
---

### Post by MIUbN00b on 2011-03-30
Hi.  I'm relatively new to Ubuntu and these forums.  I ran rkhunter, and saw this warning in the check for backdoor ports:

[14:45:09] Warning: Network TCP port 32982 is being used by /usr/bin/python2.6. Possible rootkit: Solaris Wanuk
           Use the 'lsof -i' or 'netstat -an' command to check this.


I also saw these warnings toward the bottom:

[14:45:15]   Checking /dev for suspicious file types         [ Warning ]
[14:45:15] Warning: Suspicious file types found in /dev:
[14:45:15]          /dev/shm/pulse-shm-2975823788: data
[14:45:15]          /dev/shm/pulse-shm-3216784154: data
[14:45:15]          /dev/shm/pulse-shm-359382702: data
[14:45:15]          /dev/shm/pulse-shm-3785353997: data
[14:45:15]          /dev/shm/pulse-shm-1925386408: data
[14:45:15]          /dev/shm/pulse-shm-3905958751: data
[14:45:15]          /dev/shm/pulse-shm-3982440352: data
[14:45:15]          /dev/shm/pulse-shm-2987384528: data
[14:45:15]          /dev/shm/pulse-shm-3923458849: data
[14:45:16]   Checking for hidden files and directories       [ Warning ]
[14:45:16] Warning: Hidden directory found: /dev/.udev
[14:45:16] Warning: Hidden directory found: /dev/.initramfs

I was wondering first of all about the first warning, the port.  I have a feeling that the second set of warnings are false positives, but I would be open to thoughts on that as well.

Thanks so much in advance for your help.

---

### Post by Karlchen on 2011-03-30
Hello, MIUbN00b.

These lines > [14:45:15]   Checking /dev for suspicious file types [ Warning ]
[14:45:15] Warning: Suspicious file types found in /dev:
[14:45:15]          /dev/shm/pulse-shm-2975823788: data
[...]
[14:45:15]          /dev/shm/pulse-shm-3923458849: data
[14:45:16]   Checking for hidden files and directories       [ Warning ]
[14:45:16] Warning: Hidden directory found: /dev/.udev
[14:45:16] Warning: Hidden directory found: /dev/.initramfscan very likely be found on any Ubuntu system and do not spell any real danger. They seem to be common false positives. They can be avoided by modifying the /etc/rkhunter.conf file and uncommenting the appropriate #ALLOWHIDDENDIR= lines.

The warning which should be looked into is the first one > [14:45:09] Warning: Network TCP port 32982 is being used by /usr/bin/python2.6. Possible rootkit: Solaris Wanuk
           Use the 'lsof -i' or 'netstat -an' command to check this.Have you run either "lsof -i" or "netstat -an" in order to find out what is going on on port 32982 perhaps? And if so what did you find?

You might also use chkrootkit in order to crosscheck the rkhunter warning about  potential rootkit activity.

Kind regards,
Karl

---

### Post by MIUbN00b on 2011-03-30
Thanks for your reply, Karl.

I ran chkrootkit and the only thing potentially suspicious was this:

Searching for suspicious files and dirs, it may take a while... The following suspicious files and directories were found:  
/usr/lib/pymodules/python2.6/.path /usr/lib/pymodules/python2.6/PyQt4/uic/widget-plugins/.noinit /usr/lib/firefox-3.6.16/.autoreg /usr/lib/xulrunner-1.9.2.16/.autoreg

I ran "lsof -i" and here were the results:

    COMMAND    PID     USER   FD   TYPE DEVICE SIZE/OFF NODE NAME 
 firefox-b 2048 <username>   41u  IPv4  41xxx      0t0  TCP <username>-desktop:40xxx->74.125.225.16:www (ESTABLISHED) 
 firefox-b 2048 <username>   49u  IPv4  41xxx      0t0  TCP <username>-desktop:60xxx->74.125.225.20:www (ESTABLISHED) 
 firefox-b 2048 <username>   50u  IPv4  42xxx      0t0  UDP <username>-desktop:51xxx>home:domain  
 firefox-b 2048 <username>   52u  IPv4  42xxx      0t0  UDP <username>-desktop:46xxx->home:domain  
 firefox-b 2048 <username>   55u  IPv4  42xxx      0t0  TCP <username>-desktop:56xxx->vip2.vl413.slb6.mlp1.peakwebhosting.com:www (ESTABLISHED) 
 firefox-b 2048 <username>   61u  IPv4  42xxx      0t0  UDP <username>-desktop:38xxx->home:domain  
 firefox-b 2048 <username>   63u  IPv4  41xxx      0t0  TCP <username>-desktop:60xxx->74.125.225.20:www (ESTABLISHED) 
 firefox-b 2048 <username>   66u  IPv4  41xxx      0t0  TCP <username>-desktop:44xxx->yx-in-f102.1e100.net:www (ESTABLISHED)
 
I also ran "netstat -an" but the results scrolled super fast and I was not able to see the appropriate port.

I hope this is helpful, and I would appreciate your thoughts.

Thanks Again!

EDIT: I ran rkhunter again, and port 32982 showed up as the rest ( [Not Found] )...could rkhunter be functioning improperly if I do have a problem? (the only other difference being that I had restarted my computer between the first run and the second run of rkhunter).

---

### Post by Karlchen on 2011-03-31
Hello, MIUbN00b.

I suspect rkhunter allowed itself to be fooled by the port number.
rkhunter did not report any other piece of evidence which might support the suspicion that your machine might be infected by the  Solaris Wanuk rootkit?

Unless rkhunter keeps complaining about the same port 32982, I doubt that your Ubuntu machine has been infected by a Sun Solaris rootkit. (It might have been modified to "support" Debian based Linux versions?!)

You might use Shields Up by [www.grc.com]("http://www.grc.com") in order to check whether your machine listens on open ports without your knowledge. In particular you might check whether it listens on port 3298.
--

About the chkrootkit line complaining about > /usr/lib/pymodules/python2.6/.path  /usr/lib/pymodules/python2.6/PyQt4/uic/widget-plugins/.noinit  /usr/lib/firefox-3.6.16/.autoreg /usr/lib/xulrunner-1.9.2.16/.autoreg Seems to be a common false positive. It can be found on any Ubuntu system which has got Firefox 3.6.16 and Python 2.6.
Yet, you might inspect the folder contents of the listed (hidden) folders and check whether you can spot anything fishy in there.

Kind regards,
Karl

---

### Post by MIUbN00b on 2011-03-31
Thanks so much Karl.  Rkhunter did not report any other evidence of Solaris Wanuk, the only warnings were the ones that I posted in the first post.  I also checked ShieldsUp and there were no ports open.  I'll keep a close eye on my system for a bit, but it appears that I was worried over nothing...

...though as I like to say, I would much rather worry about nothing than worry about something! :)

Thanks again!!

---

### Post by Karlchen on 2011-03-31
Hello, MIUbN00b.

Good to know that at the moment you have got no reason to be worried. And, you're welcome. :)

Cheers,
Karl

---

### Post by uRock on 2011-03-31
Moved to Security Discussions

---

### Post by brian_p on 2011-03-31
> **MIUbN00b said:**
> Thanks so much Karl.  Rkhunter did not report any other evidence of Solaris Wanuk, the only warnings were the ones that I posted in the first post.  I also checked ShieldsUp and there were no ports open.  I'll keep a close eye on my system for a bit, but it appears that I was worried over nothing...

...though as I like to say, I would much rather worry about nothing than worry about something! :)

Thanks again!!

If you look you will find this:

> Solaris.Wanuk.Worm is a worm that spreads by exploiting the Sun Solaris Telnet Remote Authentication

Even less cause to worry then. Which isn't to say rkhunter won't come up with something equally nonsensical in the future.

---

### Post by MIUbN00b on 2011-04-01
True, True, thanks Brian

---

### Post by spiffymap on 2011-04-13
I got this warning from rkhunter today too, and when I do

netstat -an | fgrep 32982

I see this:

tcp        0      0 a.b.c.d:993        w.x.y.z:32982    ESTABLISHED

a.b.c.d is the host running rkhunter and w.x.y.z is a remote host connecting to imaps. In other words, NOTHING IS LISTENING ON PORT 32982 - but the remote host is using that port for its outbound connection.

The output format from netstat is different between Solaris and Linux, so I suspect that whoever wrote the rkhunter test for that Solaris rootkit failed to take this into account, and rkhunter is misinterpreting that remote outbound port as a local listening port.

---

