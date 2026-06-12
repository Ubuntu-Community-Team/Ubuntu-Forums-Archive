---
title: "NIS client not creating home directories."
date: 2012-12-19
forum: Server Platforms
---

### Post by OmegaHarvest on 2012-12-19
Hey There

I have recently setup and configured a NIS server and client. Everything seems to be behaving well as when I type 'ypcat passwd' on the server and client I'm displayed the users I would be expecting on both.

However, having modified LightDM to give me the 'Login' option so I can login as a network user, I am unable to do so. If I delibratly type in a incorrect password, i am naturally told the login is incorrect. However, if I type the correct password, the screen goes blank for a few seconds, then kicks me back into the login screen. This implies to me that authentication is working.

I have set full permissions (777) on the home directory of the client (this is a test network so I'm not so concerned about security yet) but I notice there is no home directory created for the user I'm trying to login as. 

I did use a guide for 10.10 so something may have changed as im now using 12.04?

Apologies if I've missed anything out here. Still teaching myself so please ask if you need any logs posted.

Thanks in advance :)

P.S. If it helps, I created the user having the issue but have not added him to any groups yet, just specified a username, home directory and password. Perhaps this is where I'm going wrong?

---

### Post by OmegaHarvest on 2012-12-19
I manually created the home directory and gave the user full permissions and it logged on straight away so that was clearly the issue. If anyone knows what steps I missed to have it automagically create the home directory that would be great :D

---

### Post by dannyboy79 on 2012-12-19
what command did you use in creating that user?

---

### Post by steeldriver on 2012-12-19
> **OmegaHarvest said:**
> However, if I type the correct password, the screen goes blank for a few seconds, then kicks me back into the login screen. This implies to me that authentication is working.

Sounds like *login* authentication is working, but the X session is unable to start - a common reason for that is if the server is unable to write an .Xauthority file - either because of the $HOME directory permissions or because there's a residual $HOME/.Xauthority file owned by another user (typically root - but if you copied stuff from another user account to the new home dir it could be the old user's file)

---

### Post by OmegaHarvest on 2012-12-19
> **dannyboy79 said:**
> what command did you use in creating that user?

I did 'sudo useradd -d /home/testuser -m testuser' and then updated the NIS databse files with 'sudo make' in the /var/yp/ directory. All seemed to work well.

> **steeldriver said:**
> Sounds like *login* authentication is working, but the X session is unable to start - a common reason for that is if the server is unable to write an .Xauthority file - either because of the $HOME directory permissions or because there's a residual $HOME/.Xauthority file owned by another user (typically root - but if you copied stuff from another user account to the new home dir it could be the old user's file)

The home directory permissions on the client are root/groups/everyone full permissions. This is a username that's never been used before on the client. I literally installed it, configured NIS and got to testing.

---

### Post by dannyboy79 on 2012-12-19
hmm, that command with the -m option should have created the users home directory. weird, not sure why it didn't work

---

### Post by OmegaHarvest on 2012-12-20
Thanks anyway guys. Going with OpenLDAP now anyway as it does what im after but better!

---

### Post by SeijiSensei on 2012-12-21
Just to provide some closure, NIS doesn't create any home directories.  Usually NIS was used in conjunction with NFS with /home mounted from an NFS server.  NIS offers a way to have centralized authentication and user management in such a configuration.  It can work without NFS, of course, but then you need to create the home directories on each client machine manually.

---

