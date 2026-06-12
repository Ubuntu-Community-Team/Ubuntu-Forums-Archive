---
title: "Stateless LTSP5 profiles?"
date: 2008-06-03
forum: Server Platforms
---

### Post by NaterGator on 2008-06-03
Hello Ubuntuers!

I'm normally a gentoo user so I'm not completely familiar with Ubuntu ditros, so please pardon my stupidity.


I've got a running LTSP5 server (using xubuntu 8.04) with 12 thin clients and everything is working as it is supposed to re: the wiki. The clients are pleasingly fast and LTSP5 is easier to work with than previous versions (the MueKow/chrooted idea was great) however I've hit a snag.

These terminals provide internet access to a staff of about 200 at our summer camp and the server is not all that robust (athlon xp and 512mb of ram, hence xfce!). Also, the staff are by-and-large completely unfamiliar with linux, so I've laid Xfce out so that they'll be able to find stuff they need when they look for it like they would in windows. 

We have 12 users (staff1-staff12) that they login as (ideally with no password, still working on that) but even logging in seems to be a problem for the staff. My vision is to create sort of pseudo-kiosks where the user-profile is reset after each logout, and where the users are automatically logged into the next user account (staff2 will log in if staff1 already is, and so on). I want our staff to be able to save files to the desktop to open and work on in office, etc, and then email or whatever, but I don't want those files to persist past their current session. In other words I'll rewrite the /home/(user)/ directory at logout. 

LDM is confusing me though (I want GDM daggumit!) and I'm not sure how to go about dumping profiles. Is the best approach to this scripts that run on login/and or logout? And does anybody know of a way to automatically login the next available session? I'm kinda at a loss because I can't find much on LDM nor how to configure it easily. If I can get this done I'll happily streamline the process and write a wiki, because I feel like this is probably something that quite a few people would like to do.


Thanks!
-----Nate

---

### Post by lykwydchykyn on 2008-09-25
I'm guessing summer camp is over, so maybe this is just for posterity, but here are my suggestions from working with similar situations:

 - To get a fresh user account each time, I use rsync in the login scripts (my clients don't use a DE, they just run progs from ~/.xsession).  I have a basic home directory configuration stored in /etc/profiles.d/thinclient/, so at login I do:
rsync -qr --delete /etc/profiles.d/thinclient/ $HOME/

 - Autologin with LDM can be set up in the lts.conf file.  Probably the best thing to do is to assign a default login to an IP (since only one machine at a time is getting an IP), rather than worrying about having the logins be sequential.  so you could make entries like this in lts.conf (assuming your DHCP range is 192.168.1.101 - 192.168.1.112):

[192.168.1.101]
LDM_AUTOLOGIN=True
LDM_USERNAME = staff1
LDM_PASSWORD = foopasswurd

[192.168.1.102]
LDM_AUTOLOGIN=True
LDM_USERNAME=staff2
LDM_PASSWORD = barpasswurd

etc etc.

Hope that helps somebody, maybe for next year?

---

### Post by NaterGator on 2008-09-25
Thanks for the advice, always good to see the community willing to help, even on issues that aren't today's hot topic. I got it all setup shortly after this post, however. LTSP5 worked wonders on a cheap 2.4ghz athlonxp machine with 2gb of ram. I was quit impressed with the user experience despite having to serve so many clients.

---

