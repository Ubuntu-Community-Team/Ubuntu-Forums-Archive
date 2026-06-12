---
title: "How to allow logins when there is a shutdown in progress"
date: 2010-06-24
forum: Server Platforms
---

### Post by Stilgar on 2010-06-24
I've searched everywhere for this but haven't found anything. But its a weird thing I want to do so I'm not surprised.

I've got a server that I just use for backing up and archiving files. Since I don't need access to it often I just keep it powered off. I set up wakeonlan and have port 9 and port 22 forwarded to it. 

I travel fairly often, and how its set up now, I can send the magic packet to the connection its on and wakeonlan kicks in and powers up the server. Then I can sftp into and access the files I need and then shut it down again in ssh.

It all works good until there's a power outage. For some reason after a power outage wakeonlan doesn't work. 

Here's a workaround for this: I can set the system to automatically power up after a power outage. Problem is, the computer could be on for a week or more, wasting power before I log in and turn it off. So the workaround for that is to put a "deadman's switch" where a script will run at startup that will run "shutdown -q -P +5" which will power off the system after five minutes. 

After I run wakeonlan I can ssh in and run "shutdown -c" to cancel that shutdown and still use it. If there's a power outage, once power is restored, the system will start up and then automatically shutdown again and be ready for the next wakeonlan signal I send.

Everything is flawless, except one problem. When "shutdown -q -P +5" executes, it disables all new logins. If I'm fast enough I can ssh in before the shutdown program disables logins, but not always. What I want is a way I can run shutdown without disabling logins. Anyone know how to do this?

---

### Post by VH-BIL on 2010-06-24
I dont know if shutdown is the same as poweroff but you can try that. If poweroff dosnt have the timer functions you want you can try script them.
Example:
```
#!/bin/bash
echo "Shutting down in 5 minutes..."

# sleep intervals are in seconds 60x5=300
sleep 300

poweroff
```

I assume the script will be run with administrative permissions. If you log in and it is shutting down you can use:
```
killall <script name>
```
I don't know if this will behave any different the shutdown but it is worth a try.

---

### Post by Stilgar on 2010-06-24
I've tried that. What happens is login isn't enables until after all of the startup scripts are finished. But when that script is finished, the system is powered off.

I'm pretty sure I've tried putting "sleep 300 ; halt" in a seperate script and running "autohalt.sh &" to background it, but I can't remember what happened when I tried that. I'll try it again and see what happens.

---

### Post by VH-BIL on 2010-06-24
I think backgrounding it should work as the system shouldn't wait for the script to finish.

---

### Post by koenn on 2010-06-25
man shutdown:

when a delayed shutdown is in progress, a file /etc/nologin is created, this prevents users from logging in.

so logically, deleting that file or preventing it from being created would solve your problem
(although, if you *wanted* the shutdown to begin with, why don't you just let it  and use your wake-on-lan ? 

anyway, although /etc/nologin is well documented in man pages and all over the web, I haven't found it on my ubuntusdesktop.
 /etc/init.d/bootmisc.sh does mention something about /var/lib/initscripts/nologin

YMMV :)

---

### Post by Stilgar on 2010-06-28
Sorry for not getting back to you all, been busy over the weekend :)

Thanks koenn you pointed me in the right direction. When you schedule a shutdown /etc/nologin does get created. I didn't have to delete it because with the help of grep I found the following in /etc/pam.d/sshd:

```
# Disallow non-root logins when /etc/nologin exists.
account    required     pam_nologin.so

```

I just commented out that line and now I can login while shutdown is running.

Yeah I know what I'm doing is odd, but thats why I like linux, there's no restrictions on what you can do. 

Now I can access my files whenever I want (as long as I can find an internet connection), but I don't have to waste power by keeping the computer on all the time. If the power goes out the computer will restart and set the wakeonlan setting again and then power down by itself.

Thanks all!

---

