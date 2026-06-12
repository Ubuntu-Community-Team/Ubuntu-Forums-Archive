---
title: "rdesktop directly login"
date: 2011-01-29
forum: Server Platforms
---

### Post by aba3k on 2011-01-29
There's a way to login directly using rdesktop, instead of logging locally using the gnome session manager? Like, starting x, then typing a user and pass to login direct in a Windows server?

---

### Post by HermanAB on 2011-01-30
Uhmm, are you talking about Linux or Windows?

For Linux, use SSH:
$ ssh -X -C -c blowfish user@server gnome-panel

For Windows, use rdesktop.

---

### Post by aba3k on 2011-02-05
I want to directly login (using Ubuntu) into a Remote Desktop session. Normally one'll be logging using your username to the Gnome desktop, but i want to skip the gnome desktop, logging direct into the remote deskop machine (instead to logging into gnome, and after this using rdesktop to connect to the remote desktop machine).

---

### Post by volkswagner on 2011-02-05
> **aba3k said:**
> I want to directly login (using Ubuntu) into a Remote Desktop session. Normally one'll be logging using your username to the Gnome desktop, but i want to skip the gnome desktop, logging direct into the remote deskop machine (instead to logging into gnome, and after this using rdesktop to connect to the remote desktop machine).


It sounds to me like you want to physically login to a client machine (Gnome) and automatically launch and get logged into a remote desktop session to a remote desktop server. 

Am I close?

---

### Post by aba3k on 2011-02-10
Exactly!

> **volkswagner said:**
> It sounds to me like you want to physically login to a client machine (Gnome) and automatically launch and get logged into a remote desktop session to a remote desktop server. 

Am I close?

---

### Post by volkswagner on 2011-02-10
OK, I'm no expert but you can try adding a script to your /home/user/.gnomerc.

Are you using rdesktop or .tsclient?

---

### Post by aba3k on 2011-02-13
I don't know what .tsclient is, but for what i know i'm using rdesktop, using the gui provide wiht gnome.

> **volkswagner said:**
> OK, I'm no expert but you can try adding a script to your /home/user/.gnomerc.

Are you using rdesktop or .tsclient?

---

### Post by volkswagner on 2011-02-13
You will first want to create the script to make the app launch with your credentials.

I created a simple script in my home directory.

```
#!/bin/bash
sleep 10
/usr/bin/rdesktop servernameoripaddress -u remoteusername -p remoteuserpassword
exit 0
```

Make sure your script is set to executable.

```
sudo chmod 755 /path/to/filename
```

Also, you can add any additional parameters such as screen size, where to pipe sound, etc. to the above string.  I added the 10 second sleep to allow Gnome to start and my wireless network connection time to connect, YMMV.


To launch an application at login go to >System>Preferences>Startup Applications... From there you can add items to startup.  Create a name, browse to your new script, and add a description!

---

### Post by aba3k on 2011-02-15
Thanks.

> **volkswagner said:**
> You will first want to create the script to make the app launch with your credentials.

I created a simple script in my home directory.

```
#!/bin/bash
sleep 10
/usr/bin/rdesktop servernameoripaddress -u remoteusername -p remoteuserpassword
exit 0
```

Make sure your script is set to executable.

```
sudo chmod 755 /path/to/filename
```

Also, you can add any additional parameters such as screen size, where to pipe sound, etc. to the above string.  I added the 10 second sleep to allow Gnome to start and my wireless network connection time to connect, YMMV.


To launch an application at login go to >System>Preferences>Startup Applications... From there you can add items to startup.  Create a name, browse to your new script, and add a description!

---

