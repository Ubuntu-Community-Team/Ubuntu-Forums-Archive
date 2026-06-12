---
title: "LTSP and booting HPt5000"
date: 2010-12-04
forum: Server Platforms
---

### Post by keiffee30 on 2010-12-04
I got myself a HP t5000 series Thin client to use on my LTSP 10.04. I changed the Bios to boot PxE. 

When i restart the thin client it asks for a DHCP and finds the LTSP-DHCP server all is good.

[LIST]
[*]Its got a IP address ok, the boot process starts. ok

[*]I get the Splash screen for Ubuntu. and all is going well. ok 

[*]I no get a login screen. All is going very well. (As normal with Ubuntu).

[*]I can login all is good the login starts and i get the start up sound.
[/LIST]
But then where normally one would expect to get a desktop, one gets a login screen. Not knowing the full boot procses im not sure where to start to look. Knowing linux there would be a log file somewhere, that stores the LTSP Terminal Bootup/login process and would tell me where its stopping/failing. 

The good news is that when i boot a fat client in all works ok and i an able to get in with a desktop.

---

### Post by keiffee30 on 2010-12-05
Here is what the /var/log/auth.log output said when i try and login 


[LIST]
[*]Dec  3 20:05:23 ubuntu-ltsp sshd[13642]: Accepted password for keiffee from 192.168.0.80 port 57163 ssh2

[*]Dec  3 20:05:23 ubuntu-ltsp sshd[13642]: pam_unix(sshd:session): session opened for user keiffee by (uid=0)

[*]Dec  3 20:05:26 ubuntu-ltsp sshd[13726]: subsystem request for sftp

[*]Dec  3 20:05:30 ubuntu-ltsp polkitd(authority=local): Registered Authentication Agent for session /org/freedesktop/ConsoleKit/Session122 (system bus name :1.1747 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_GB.UTF-8)

[*]Dec  3 20:05:38 ubuntu-ltsp sshd[13726]: Received disconnect from 192.168.0.80: 11: disconnected by user

[*]Dec  3 20:05:38 ubuntu-ltsp sshd[13642]: pam_unix(sshd:session): session closed for user keiffee

[*]Dec  3 20:05:38 ubuntu-ltsp gnome-keyring-daemon[13814]: dbus failure unregistering from session: Connection is closed

[*]Dec  3 20:05:38 ubuntu-ltsp gnome-keyring-daemon[13814]: dbus failure unregistering from session: Connection is closed

[*]Dec  3 20:05:38 ubuntu-ltsp polkitd(authority=local): Unregistered Authentication Agent for session /org/freedesktop/ConsoleKit/Session122 (system bus name :1.1747, object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_GB.UTF-8) (disconnected from bus)
[/LIST]

it looks to me that i have logged out ... when im trying to login ??? could anyone put some more light on this for me

---

### Post by keiffee30 on 2010-12-11
I have worked on this all over the week and i have now fixed it. This little HP thin client is working faster than my normal PC. Me thinks i will be getting more of this little boxes and replaying my old fat PC's

---

### Post by lsatkins on 2011-02-03
So what exactly did you do to fix this?  I'm having the same problem.  I can get to the Ubuntu log in screen and when I log in I get the music and it starts to load the desktop then just freezes and kicks me back out to the login screen.

---

### Post by sygard on 2011-02-07
I just stumbled across this exact problem, could you please explain how you fixed this?

My installation works well with my laptop, so there has to be something with the HP t5000 client. I'm leaning towards the graphics card, but who knows...?

All help is appreciated,
Tor Martin.

---

### Post by keiffee30 on 2011-04-01
Sorry guys for not getting back to you sooner. 

Ok what i did?????

After looking at all the log files and testing the charoot, updating and all pulling what hair i had out. i tried the user that is on the main LTSP server for its admin. (not full root more a super user). 

I logged in as LTSP-local-user and found that this account logged all the way into the HP client. and it run with no problems. i run fast too. 

I then tried to log into the HP using 1 of the other LTSP users (me, wife, kid1,kid2) and my account and both the kids account bombed out back to login... but the wifes account logged in all the way. 

This to me would say that its something in the user setup / account on the Main Server that needs to be set before you get a nice login. i might be able to send you a list of "groups" that the LTSP-local-user has and a user that dont log in to see if this is the same or not. But it looks like its a rights thing more so than a hardware issue. 

Hope this helps. 

BTW the LTSP is a "strate off the CD" install and a sudo apt-get update, updated charoot, and SSH keys but apart from that there is nothing changed. I will be looking at getting Skype and Firefox on the client PC. There something about video playing over the LTSP being slow so i will be looking at putting this on the client too but im just happy that its working and printing and the LAMP is working too on the same box. 

and sorry for the delay in replying

---

