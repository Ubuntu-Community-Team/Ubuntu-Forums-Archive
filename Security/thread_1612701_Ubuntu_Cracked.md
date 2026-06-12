---
title: "Ubuntu Cracked???"
date: 2010-11-03
forum: Security
---

### Post by farlander762 on 2010-11-03
My wife was using the computer earlier working on an office document when all of the sudden the cursor moved right, then left, then up, then down.  Immediately after that the mouse moved up and logged her off and then logged our daughter on (daughter's acct does not require password).  At this point my wife killed the machine with the power switch and then powered off the modem and router also.  

I searched through all of the logs and could only find the following as relevant entries.  This is from auth.log.  I have only included today's log but everything looks similar except for the log entry at 11:35:36/37.  Remote Desktop is not enabled but unfortunately I don't know what else to look for.  I ran update manager and hit the "Check" button and everything is up to date.

This machine is running 10.04 32 bit.

HELP!!!


```
Nov  3 06:23:37 Medion-Ubuntu gdm-session-worker[1073]: pam_succeed_if(gdm:auth): requirement "user ingroup nopasswdlogin" not met by user "lance"
Nov  3 06:23:39 Medion-Ubuntu gdm-session-worker[1073]: pam_unix(gdm:session): session opened for user lance by (uid=0)
Nov  3 06:23:39 Medion-Ubuntu gdm-session-worker[1073]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :0
Nov  3 06:23:42 Medion-Ubuntu polkitd(authority=local): Registered Authentication Agent for session /org/freedesktop/ConsoleKit/Session2 (system bus name :1.31 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_US.utf8)
Nov  3 06:25:01 Medion-Ubuntu CRON[1567]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov  3 06:25:01 Medion-Ubuntu CRON[1567]: pam_unix(cron:session): session closed for user root
Nov  3 07:17:01 Medion-Ubuntu CRON[1892]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov  3 07:17:02 Medion-Ubuntu CRON[1892]: pam_unix(cron:session): session closed for user root
Nov  3 07:30:01 Medion-Ubuntu CRON[1922]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov  3 07:30:01 Medion-Ubuntu CRON[1922]: pam_unix(cron:session): session closed for user root
Nov  3 08:17:01 Medion-Ubuntu CRON[1930]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov  3 08:17:01 Medion-Ubuntu CRON[1930]: pam_unix(cron:session): session closed for user root
Nov  3 10:07:14 Medion-Ubuntu gdm-session-worker[1077]: pam_succeed_if(gdm:auth): requirement "user ingroup nopasswdlogin" not met by user "lance"
Nov  3 10:07:17 Medion-Ubuntu gdm-session-worker[1077]: pam_unix(gdm:session): session opened for user lance by (uid=0)
Nov  3 10:07:17 Medion-Ubuntu gdm-session-worker[1077]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :0
Nov  3 10:07:21 Medion-Ubuntu polkitd(authority=local): Registered Authentication Agent for session /org/freedesktop/ConsoleKit/Session2 (system bus name :1.31 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_US.utf8)
Nov  3 10:17:01 Medion-Ubuntu CRON[1660]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov  3 10:17:01 Medion-Ubuntu CRON[1660]: pam_unix(cron:session): session closed for user root
Nov  3 11:17:01 Medion-Ubuntu CRON[2038]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov  3 11:17:01 Medion-Ubuntu CRON[2038]: pam_unix(cron:session): session closed for user root
Nov  3 11:35:36 Medion-Ubuntu gdm-session-worker[2100]: pam_succeed_if(gdm:auth): requirement "user ingroup nopasswdlogin" was met by user "zaigh"
Nov  3 11:35:37 Medion-Ubuntu gdm-session-worker[2100]: pam_unix(gdm:session): session opened for user zaigh by (uid=0)
Nov  3 11:35:37 Medion-Ubuntu gdm-session-worker[2100]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :1
Nov  3 11:35:40 Medion-Ubuntu polkitd(authority=local): Registered Authentication Agent for session /org/freedesktop/ConsoleKit/Session4 (system bus name :1.67 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_US.UTF-8)
Nov  3 12:23:49 Medion-Ubuntu gdm-session-worker[1068]: pam_succeed_if(gdm:auth): requirement "user ingroup nopasswdlogin" not met by user "lance"
Nov  3 12:23:51 Medion-Ubuntu gdm-session-worker[1068]: pam_unix(gdm:session): session opened for user lance by (uid=0)
Nov  3 12:23:51 Medion-Ubuntu gdm-session-worker[1068]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :0
Nov  3 12:23:55 Medion-Ubuntu polkitd(authority=local): Registered Authentication Agent for session /org/freedesktop/ConsoleKit/Session2 (system bus name :1.31 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_US.utf8)

```

---

### Post by mr-woof on 2010-11-03
do you have ssh installed?

---

### Post by CharlesA on 2010-11-03
> **mr-woof said:**
> do you have ssh installed?

Remote Desktop is probably enabled and exposed to the internet.

Disable it: System > Administration > Remote Desktop.

---

### Post by mr-woof on 2010-11-03
he does say remote desktop isn't enabled charles

---

### Post by CharlesA on 2010-11-03
That would be the only way that the mouse would move in the current session and log them out.

---

### Post by mr-woof on 2010-11-03
aha :) Wonder if he has a router with upnp on?

---

### Post by farlander762 on 2010-11-03
Per a quick Synaptic search, SSH is not installed.  I was just reading the thread titled "Precautions?" and saw SSH mentioned but it was commented that SSH was only important if Remote Desktop was enabled.

Remote desktop is not enabled.  It is under System >> Preferences on my machine.

---

### Post by Rasa1111 on 2010-11-03
weird. 

 I know you said remote desktop is not enabled.. 

But do you have it set to not start at startup?

in Startup Applications? 

 I would go into startup apps and make sure it [remote desktop] is unchecked. 

 Interested to learn more from more experienced folks....

---

### Post by farlander762 on 2010-11-03
UPNP was on, but is now off and I have changed my router access password.

---

### Post by CharlesA on 2010-11-03
SSH doesn't provice graphical access.

If someone got in, it would be a good idea to backup yer stuff and reinstall.

---

### Post by farlander762 on 2010-11-03
Odd, when I checked in Startup Apps I found that Bluetooth Manager, Remote Desktop, Ubuntu One, and Visual Assistance were all turned on (everything was on).  I generally keep those turned off as I don't see any reason for them to be active.  I may have forgot to turn them off when I set this machine up last time.  About two months ago a lightening storm corrupted this machine and I had to wipe it and start completely over.

---

### Post by mr-woof on 2010-11-03
sounds like that could be the problem, it'll probably be best to back up any personal data, wipe and re-install

---

### Post by kaldor on 2010-11-03
> **mr-woof said:**
> sounds like that could be the problem, it'll probably be best to back up any personal data, wipe and re-install

Why would that change anything for him?

---

### Post by farlander762 on 2010-11-03
Crap.  

I called the cable company and asked them to reset my public IP address (they did).  I have found that DSL providers change IP's almost daily but cable providers rarely change them.  Maybe it will make some A-hole's day a little harder trying to find me again.  The guy at the cable co. said he could not see past my router with his equipment.  

Is there another log I should check?

It really is too bad that hot lead moving at high velocity cannot be transmitted across the Internet...

Thanks for all your help.  Fortunately, I really don't keep useful info on our confusers.

---

### Post by t.rei on 2010-11-03
turn off internet
reset router
flash router
delete ~/.ssh/authorized_keys
change password
check permissions on password files
run rkhunter and maybe clamav
check all running programs and processes (via ps ax)
check all configuration, boot scripts, logon scripts (bash too!) and startup programs
and so on and so forth...

tbh - once in a system it is REALLY hard to get whoever, no matter what system, back out if he/she knew what he/she was doing. 

I'd suggest:
* Copy private, non-executable! data to an external backup. 
* While not having your computer connected to the router, disconnect it from the internet and put it back to defaults, or better fully flash it with the newest firmware. Configure it. Hook it back up to the internet.
* Get a fresh iso from the official ubuntu site using a different machine than the infected.
* Use new passwords for that install! 

Yes I am a little paranoid. But intrusion into someones computer is to be taken serious nowadays. Theres money to be made and blame to be diverted...

Or you can do it the windows way, run the rkhunter and the virus check and claim your computer to be safe :D

---

### Post by CharlesA on 2010-11-03
> **kaldor said:**
> Why would that change anything for him?

If a machine has been compromised, you can never be sure that everything is 100% removed. Reinstalling the OS is the only way to make sure the machine is clean.

> **t.rei said:**
> turn off internet
reset router
flash router
delete ~/.ssh/authorized_keys
change password
check permissions on password files
run rkhunter and maybe clamav
check all running programs and processes (via ps ax)
check all configuration, boot scripts, logon scripts (bash too!) and startup programs
and so on and so forth...

tbh - once in a system it is REALLY hard to get whoever, no matter what system, back out if he/she knew what he/she was doing. 

I'd suggest:
* Copy private, non-executable! data to an external backup. 
* While not having your computer connected to the router, disconnect it from the internet and put it back to defaults, or better fully flash it with the newest firmware. Configure it. Hook it back up to the internet.
* Get a fresh iso from the official ubuntu site using a different machine than the infected.
* Use new passwords for that install! 

Yes I am a little paranoid. But intrusion into someones computer is to be taken serious nowadays. Theres money to be made and blame to be diverted...

Or you can do it the windows way, run the rkhunter and the virus check and claim your computer to be safe :D

Geez. That's way overkill. There isn't any need to do 90% of that.

Backing up yer data and reinstalling is all that would be needed tbh.

---

### Post by mr-woof on 2010-11-03
here is a question for the people in the know, ie not me :)

If as discussed, we think that the remote desktop was compromised, so the attacker could move the mouse etc. If ssh was compromised on a desktop machine, how would you know while you were using it?

---

### Post by farlander762 on 2010-11-03
Double crap.

---

### Post by CharlesA on 2010-11-03
> **mr-woof said:**
> here is a question for the people in the know, ie not me :)

If as discussed, we think that the remote desktop was compromised, so the attacker could move the mouse etc. If ssh was compromised on a desktop machine, how would you know while you were using it?

The auth.log would show a successful authentication.

Of course, that is easily removed if someone was able to get access.

@OP: Has it happened again?

You can check listening services by running this from a terminal:

```
netstat -ln
```

---

### Post by mr-woof on 2010-11-03
ah right, thanks charles. :) 

what's happened now op?

---

### Post by farlander762 on 2010-11-03
Doesn't appear to have happened again.  I have no idea what this says...

```
lance@Medion-Ubuntu:~$ netstat -ln
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 127.0.0.1:59918         0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
tcp6       0      0 ::1:631                 :::*                    LISTEN     
udp        0      0 0.0.0.0:68              0.0.0.0:*                          
udp        0      0 0.0.0.0:54376           0.0.0.0:*                          
udp        0      0 0.0.0.0:5353            0.0.0.0:*                          
Active UNIX domain sockets (only servers)
Proto RefCnt Flags       Type       State         I-Node   Path
unix  2      [ ACC ]     STREAM     LISTENING     4456     /tmp/.winbindd/pipe
unix  2      [ ACC ]     STREAM     LISTENING     4977     /tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     7090     /tmp/ssh-oyLKFg1233/agent.1233
unix  2      [ ACC ]     STREAM     LISTENING     4615     /var/run/cups/cups.sock
unix  2      [ ACC ]     STREAM     LISTENING     7132     /tmp/.ICE-unix/1233
unix  2      [ ACC ]     STREAM     LISTENING     7152     /tmp/orbit-lance/linc-4fa-0-6f040f999a237
unix  2      [ ACC ]     STREAM     LISTENING     7409     /tmp/orbit-lance/linc-4d1-0-2aed753da3634
unix  2      [ ACC ]     STREAM     LISTENING     7549     /tmp/orbit-lance/linc-500-0-2049334137067
unix  2      [ ACC ]     STREAM     LISTENING     6846     /tmp/keyring-y1vz7X/control
unix  2      [ ACC ]     STREAM     LISTENING     7558     /tmp/keyring-y1vz7X/ssh
unix  2      [ ACC ]     STREAM     LISTENING     7560     /tmp/keyring-y1vz7X/pkcs11
unix  2      [ ACC ]     STREAM     LISTENING     7986     /tmp/orbit-lance/linc-514-0-5fec20469b741
unix  2      [ ACC ]     STREAM     LISTENING     8003     /tmp/orbit-lance/linc-50e-0-4b72d871c0f4a
unix  2      [ ACC ]     STREAM     LISTENING     8005     /tmp/orbit-lance/linc-50d-0-5c3c7606c104d
unix  2      [ ACC ]     STREAM     LISTENING     8084     /tmp/orbit-lance/linc-512-0-2bb5d71f9be65
unix  2      [ ACC ]     STREAM     LISTENING     8065     /tmp/orbit-lance/linc-511-0-6e06fac88c551
unix  2      [ ACC ]     STREAM     LISTENING     8371     /tmp/orbit-lance/linc-513-0-3bb8d01e114
unix  2      [ ACC ]     STREAM     LISTENING     8263     /tmp/.esd-1000/socket
unix  2      [ ACC ]     STREAM     LISTENING     8271     /home/lance/.pulse/8ae0228d5d2fddc00453ee464c4f9a81-runtime/native
unix  2      [ ACC ]     STREAM     LISTENING     8322     /tmp/orbit-lance/linc-55e-0-1c60a3886a063
unix  2      [ ACC ]     STREAM     LISTENING     8545     /tmp/orbit-lance/linc-565-0-21fe631b5d179
unix  2      [ ACC ]     STREAM     LISTENING     8734     /tmp/orbit-lance/linc-564-0-2a7224e91e42
unix  2      [ ACC ]     STREAM     LISTENING     8789     /tmp/orbit-lance/linc-580-0-2287d8704d248
unix  2      [ ACC ]     STREAM     LISTENING     8819     /tmp/orbit-lance/linc-51a-0-5d2b149cb5d01
unix  2      [ ACC ]     STREAM     LISTENING     9171     /tmp/orbit-lance/linc-598-0-30a1a6b0e920d
unix  2      [ ACC ]     STREAM     LISTENING     9192     /tmp/orbit-lance/linc-595-0-30ed2b33f2aea
unix  2      [ ACC ]     STREAM     LISTENING     9225     /tmp/orbit-lance/linc-596-0-1e833b88ca8f
unix  2      [ ACC ]     STREAM     LISTENING     9267     /tmp/orbit-lance/linc-594-0-182d4e8a33476
unix  2      [ ACC ]     STREAM     LISTENING     9309     /tmp/orbit-lance/linc-597-0-2ebe85e751b63
unix  2      [ ACC ]     STREAM     LISTENING     9394     /tmp/orbit-lance/linc-5ae-0-2e4e895c400d
unix  2      [ ACC ]     STREAM     LISTENING     9465     /tmp/orbit-lance/linc-5b6-0-6760e8f84b9be
unix  2      [ ACC ]     STREAM     LISTENING     10874    /tmp/orbit-lance/linc-5be-0-3633f7bc660e9
unix  2      [ ACC ]     STREAM     LISTENING     10942    /tmp/orbit-lance/linc-5c5-0-3633f7bcafdde
unix  2      [ ACC ]     STREAM     LISTENING     11008    /tmp/orbit-lance/linc-5c8-0-2d3094bbe96ce
unix  2      [ ACC ]     STREAM     LISTENING     949967   /tmp/orbit-lance/linc-b5c-0-2fcee5df1f4be
unix  2      [ ACC ]     STREAM     LISTENING     12949    /tmp/orbit-lance/linc-5e9-0-5f04cafc45cb
unix  2      [ ACC ]     STREAM     LISTENING     46188    /tmp/orbit-lance/linc-612-0-6b3c0d7557375
unix  2      [ ACC ]     STREAM     LISTENING     953377   /tmp/orbit-lance/linc-b74-0-324dcc68d7906
unix  2      [ ACC ]     STREAM     LISTENING     67442    /tmp/orbit-lance/linc-7b6-0-3905bf7e8422c
unix  2      [ ACC ]     STREAM     LISTENING     3892     /var/run/dbus/system_bus_socket
unix  2      [ ACC ]     STREAM     LISTENING     2582     @/com/ubuntu/upstart
unix  2      [ ACC ]     STREAM     LISTENING     4161     /var/run/acpid.socket
unix  2      [ ACC ]     STREAM     LISTENING     5784     @/var/run/hald/dbus-vtz0rGOMGK
unix  2      [ ACC ]     STREAM     LISTENING     7103     @/tmp/dbus-4Gqmb5r1O9
unix  2      [ ACC ]     STREAM     LISTENING     4976     @/tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     4458     /var/run/samba/winbindd_privileged/pipe
unix  2      [ ACC ]     STREAM     LISTENING     5789     @/var/run/hald/dbus-gNp7GHxAFW
unix  2      [ ACC ]     STREAM     LISTENING     3952     /var/run/avahi-daemon/socket
unix  2      [ ACC ]     STREAM     LISTENING     5083     @/tmp/gdm-greeter-pjEjmzfa
unix  2      [ ACC ]     STREAM     LISTENING     5225     @/tmp/gdm-session-bTbWolvh
unix  2      [ ACC ]     STREAM     LISTENING     7131     @/tmp/.ICE-unix/1233
```


auth.log says:
```

Nov  3 13:13:51 Medion-Ubuntu sudo:    lance : TTY=unknown ; PWD=/home/lance ; USER=root ; COMMAND=/usr/sbin/synaptic --hide-main-window --non-interactive --parent-window-id 77594663 --update-at-startup
Nov  3 13:17:01 Medion-Ubuntu CRON[2132]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov  3 13:17:01 Medion-Ubuntu CRON[2132]: pam_unix(cron:session): session closed for user root
Nov  3 13:27:30 Medion-Ubuntu sudo:    lance : TTY=unknown ; PWD=/home/lance ; USER=root ; COMMAND=/usr/sbin/synaptic
Nov  3 14:17:01 Medion-Ubuntu CRON[2554]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov  3 14:17:01 Medion-Ubuntu CRON[2554]: pam_unix(cron:session): session closed for user root
Nov  3 15:17:01 Medion-Ubuntu CRON[2631]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov  3 15:17:01 Medion-Ubuntu CRON[2631]: pam_unix(cron:session): session closed for user root
```

Nothing weird has happened since the initial event.

---

### Post by CharlesA on 2010-11-03
That looks fine. VNC (port 5900) isn't listening and SSH (port 22) isn't listening.

As for the auth.log stuff, it's just cron checking to see if there something that needs to be run. I've got a bunch of that stuff in auth.log.

---

### Post by The Cog on 2010-11-03
Do you have a user zaigh that you know about?

---

### Post by farlander762 on 2010-11-03
zaigh is my daughter's account.  There are only two accounts on the system and the "intruder" logged my account out and logged into hers.

---

### Post by WeAreLinux on 2010-11-03
Is there any good reason why people always suggest disabling Remote Desktop? If you don't need it, removing it altogether would be the best idea :)

Edit: See the next post.

---

### Post by CharlesA on 2010-11-03
> **WeAreLinux said:**
> Is there any good reason why people always suggest disabling Remote Desktop? If you don't need it, removing it altogether would be the best idea :)

Software Center ---> Installed Software ---> Remove "Remote Desktop Viewer", "Remote Desktop" & "Terminal Server Client". Then remove Remote Desktop from your Startup Applications.

Just wanted to say that for future reference.

Remove Desktop Viewer and Terminal Server Client aren't services. Only "Remote Desktop" is.

Can you just remove "vinagre" if you want to remove anything at all.

---

### Post by farlander762 on 2010-11-06
I ran "rkhunter -c" and got the following warnings

```
[07:42:00] Performing filesystem checks
[07:42:00] Info: Starting test name 'filesystem'
[07:42:00] Info: SCAN_MODE_DEV set to 'THOROUGH'
[07:42:01]   Checking /dev for suspicious file types         [ Warning ]
[07:42:01] Warning: Suspicious file types found in /dev:
[07:42:01]          /dev/shm/pulse-shm-1712686805: data
[07:42:01]          /dev/shm/pulse-shm-4071389726: data
[07:42:01]          /dev/shm/pulse-shm-3464514452: data
[07:42:01]   Checking for hidden files and directories       [ Warning ]
[07:42:01] Warning: Hidden directory found: /etc/.java
[07:42:01] Warning: Hidden directory found: /dev/.udev
[07:42:01] Warning: Hidden directory found: /dev/.initramfs
```

I think "pulse" is the audio system, I know what Java is, and I have no idea what udev and initramfs are but I have seen them before.  Does this look suspect to anyone?  

I also ran chkrootkit and got these results

```
Searching for suspicious files and dirs, it may take a while... The following suspicious files and directories were found:  
/usr/lib/xulrunner-1.9.2.12/.autoreg /usr/lib/pymodules/python2.6/.path /usr/lib/pymodules/python2.6/PyQt4/uic/widget-plugins/.noinit /usr/lib/jvm/.java-6-openjdk.jinfo /usr/lib/firefox-3.6.12/.autoreg
```


and


```
Checking `z2'...                                            user lance deleted or never logged from lastlog!
user zaigh deleted or never logged from lastlog!
```


I don't know how to run clamav.  I guess it's really no matter.  This thing is getting knocked in the head today...

---

### Post by brian_p on 2010-11-06
> **farlander762 said:**
> 

Does this look suspect to anyone?

Not at all.

> I also ran chkrootkit and got these results


Nothing to worry about there either.

Both these programs are adept at producing spurious warnings and their use for anything serious is best avoided.

---

### Post by ticket on 2010-11-06
Another (rather slim) possibility is that a key combination got stuck and autorepeated.  That just might create the same effect.  However, if that was the case, you would have noticed it happen at least once before.
I'm currently plagued by rare autokey repeat bug, which locks you out of any keyboard entry once it starts. It's a software thing - not hardware.

---

### Post by CharlesA on 2010-11-06
> **brian_p said:**
> Both these programs are adept at producing spurious warnings and their use for anything serious is best avoided.

chkrootkit results look fine.

clamav will more then likely spit back a load of false positives.

---

### Post by HermanAB on 2010-11-07
Congratulations, you are the umpteen gazillionth user that has been compromized thanks to the stupid default security policies of Ubuntu.

Unfortunately, Ubuntu allows users to play with VNC without knowing what they are doing and set very short passwords - a bad combination.  VNC also has Plug And Pray capabilites built in that will automatically open up a home router.

If you want to use any remote access systems, then you have to use very long secure passwords for ALL users. Using a k3wl 4 character password is not a good idea.  Also, VNC is best avoided, rather use SSH.

---

### Post by geoffmcc on 2010-11-07
Not really much help, just being captain obvious.

If you don't use vnc or ssh for any reason might be wise to block them with firewall so if they do happen to get enabled somehow at least the firewall will block them.

---

### Post by HermanAB on 2010-11-07
Well, part of the problem is that VNC will automatically open a home firewall through PnP.  So may think you closed it.  VNC effectively turns an otherwise secure Linux system into an insecure Windows-like system.

---

### Post by geoffmcc on 2010-11-07
> **HermanAB said:**
> Well, part of the problem is that VNC will automatically open a home firewall through PnP.  So may think you closed it.  VNC effectively turns an otherwise secure Linux system into an insecure Windows-like system.

I have no experience with VNC so i will take your word for it, but its to my understanding that UPNP should handle the forwarding of ports, not allow communication to pass threw a firewall.

VNC uses a standard port right, its not just a random high port.

Since you used a windows example. my utorrent uses upnp. But i can still block it with a firewall.

---

### Post by CharlesA on 2010-11-07
> **geoffmcc said:**
> I have no experience with VNC so i will take your word for it, but its to my understanding that UPNP should handle the forwarding of ports, not allow communication to pass threw a firewall.

VNC uses a standard port right, its not just a random high port.

Since you used a windows example. my utorrent uses upnp. But i can still block it with a firewall.

It would forward them on the router, effectively allowing connections from the internet.

---

### Post by geoffmcc on 2010-11-07
> **CharlesA said:**
> It would forward them on the router, effectively allowing connections from the internet.

Im not trying to argue, I just don't get it i guess. Time to do some research since my understanding was the firewall effectively sits between the computer and the router. 

That being said - just because the router knows were to forward the ports doesn't mean the firewall has to accept them, but like i said I might be mistaken (it happens often)

---

### Post by CharlesA on 2010-11-07
> **geoffmcc said:**
> Im not trying to argue, I just don't get it i guess. Time to do some research since my understanding was the firewall effectively sits between the computer and the router. 

That being said - just because the router knows were to forward the ports doesn't mean the firewall has to accept them, but like i said I might be mistaken (it happens often)

Basically, if you use port forwarding, you are opening a "hole" in the firewall on the router to allow certain traffic to pass thru.

UPNP does that automatically, so unless you are running another firewall on yer local machine that effectively blocks all incoming connections (which I think you mentioned, but I could be wrong) you'd still have that service exposed to the internet.

---

### Post by geoffmcc on 2010-11-07
> **CharlesA said:**
> Basically, if you use port forwarding, you are opening a "hole" in the firewall on the router to allow certain traffic to pass thru.

UPNP does that automatically, so unless you are running another firewall on yer local machine that effectively blocks all incoming connections (which I think you mentioned, but I could be wrong) you'd still have that service exposed to the internet.

yea i was refering to something like apf-firewall or UFW

---

### Post by CharlesA on 2010-11-07
> **geoffmcc said:**
> yea i was refering to something like apf-firewall or UFW

Those would block incoming connections, yes.

The only time I enable ufw is when I am on an untrusted network. Since I don't have any listening services installed what is there to firewall?

The only thing that is open to the internet is SSH on my server, which is firewalled. Everything else isn't since they aren't being accessed from the internet.

---

### Post by P4man on 2010-11-07
Did these accounts have different and reasonably strong passwords?

Its better to be safe than sorried, but assuming these accounts didnt have trivial or 3 letter passwords, then Im not quite convinced any hacking took place here. It requires quite a bit of linux knowledge to remotely hijack a linux machine and obtain user account passwords for several accounts. One account might have happened through social engineering/guessing or a brute force attack on a weak password, but none of that is likely to happen for several account. And if you have one (administrator) account, why bother getting others?. 

Im not saying thats impossible, but why would such a hacker than be so incredibly stupid to take over a desktop session? He doesnt need it and its a dead giveaway.

Im thinking what is more likely that happened is something mundane like accidentally enabling mousekeys or something.

Anyway, by all means dont let that stop you from properly setting up the machine so its secure.

---

