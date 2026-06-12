---
title: "Thin client loads the image but ....."
date: 2010-01-08
forum: Server Platforms
---

### Post by prasadvj on 2010-01-08
Hi All,

I have installed Ubuntu 9.04 Server Edition and also LTSP server. I have configured the /etc/ltsp/dhcpd.conf file as per my requirement and have built the ltsp client. 

Now when I boot (start) the thin client it load the image and displays the login screen. When I login with a username and password it enters loads the desktop and immediately returns back to the login screen.

I have also run the commands ltsp-update-sshkeys and ltsp-update-image but no changes. How can I resolve this problem? 

Thanks is anticipation

Prasad

---

### Post by PlaidTiger on 2010-05-18
Ditto. I am having a similar problem with 10.04 and a slower HP thin client. Boot up, login screen, and login seem to work correctly, but before I can see the full desktop it resets back to the login screen. (After it plays the login sound, though.) I have tried both of the default 64 bit and 32 bit 10.04 Alternate LTSP installs at this point.

---

### Post by rwmarch on 2010-06-03
> **PlaidTiger said:**
> Ditto. I am having a similar problem with 10.04 and a slower HP thin client. Boot up, login screen, and login seem to work correctly, but before I can see the full desktop it resets back to the login screen. (After it plays the login sound, though.) I have tried both of the default 64 bit and 32 bit 10.04 Alternate LTSP installs at this point.


I am also having this problem.
Has the cause been determined?  Has this been solved?

---

### Post by MikeUK on 2010-06-07
I have just ungraded from 8.04LTS to 10.4LTS (5th June 2010)
I have I believe the same problem
I can load the TFTP image, get to the login screen, login, I then get the boot sound, it loads the session background and then resets back to the login screen again?

I tried LTSP-update-sshkeys followed by ltsp-update-image with no noticeable effect.

When I get a chance I'm going for a long dig in the log files to see If I can find anything useful?

---

### Post by MikeUK on 2010-06-07
I did some digging and found this in /var/log/auth.log

Jun  5 16:50:25 Hex sshd[25576]: Accepted password for xxxx from 192.168.x.x port 59228 ssh2
Jun  5 16:50:25 Hex sshd[25576]: pam_unix(sshd:session): session opened for user home by (uid=0)
Jun  5 16:50:34 Hex sshd[25684]: subsystem request for sftp
Jun  5 16:50:39 Hex polkitd(authority=local): Registered Authentication Agent for session /org/freedesktop/ConsoleKit/Session5 (system bus name :1.58 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_CA.UTF-8)
Jun  5 16:50:41 Hex gnome-keyring-daemon[25756]: dbus failure unregistering from session: Connection is closed
Jun  5 16:50:41 Hex sshd[25684]: Received disconnect from 192.168.x.x: 11: disconnected by user

I shall go looking further, if I find anything else I'll add it to this thread

---

### Post by MikeUK on 2010-06-10
I tried using the session options and was able to get a working xterm so I knew that I did have a working link back to the LTSP server.
I tried to get into the client using the Screen01=shell option, but all i got was a scrambled screen.
Based on this my assumption was that the Xorg driver was playing up?
It could be the wrong driver or the correct driver but mis-configured?
I set the lts.conf file for the terminal to XSERVER=vesa
Problem for now sort of solved I can login an dout without issue and screen resolution is OK

Next step is to try the correct driver via XSERVER= and see if that works?

---

### Post by MikeUK on 2010-07-09
For the savage driver I found switching off DRI  solved my problem

in lts.conf


in a per client basis X_OPTION_01="\"DRI\" \"off\""

---

### Post by Subscript on 2010-08-17
As per help from #ltsp channel angels ;) I tried this solution, and it worked for me.

Just disable compiz for all users.

```

sudo gconftool-2 --direct --config-source xml:readwrite:-/etc/gconf/gconf.xml.mandatory --type string --set /desktop/gnome/session/required_components/windowmanager metacity



```

---

