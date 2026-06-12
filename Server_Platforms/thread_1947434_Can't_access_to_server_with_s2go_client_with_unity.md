---
title: "Can't access to server with s2go client with unity"
date: 2012-03-26
forum: Server Platforms
---

### Post by albatros78 on 2012-03-26
Hi,
I installed Ubuntu 11.10 and can not seem to log on with client x2go of unity: the start of the remote session is without problems, until I can see the logo "X2GO" tab of the remote session, but then, instead of displaying the desktop server, the client disconnects from the server without showing any error.
I tried to use custom commands to the client as a gnome-session, gnome-session-fallback, unity, unity-2d-shell, but without any result;
Instead the problem does not occur as accessing kde session.
 
Can anyone help me?
thanks a lot

---

### Post by albatros78 on 2012-03-27
Nobody can help me??
Thnks

---

### Post by albatros78 on 2012-04-11
Help me!!

---

### Post by rpremuz on 2012-04-11
I also have this problem.

Nobody replied so far probably because you posted the question in this server category of the forum. I'd say we'd better ask it in the Desktop Environments category: [http://ubuntuforums.org/forumdisplay.php?f=329](http://ubuntuforums.org/forumdisplay.php?f=329)

I'm also considering the X2Go Community forum:
[http://x2go-community.org/main-menu/forum/](http://x2go-community.org/main-menu/forum/)

-- rpr.

---

### Post by albatros78 on 2012-04-14
Thank you,
have you solved?

---

### Post by rpremuz on 2012-04-14
I've managed to solve this issue by installing the **x2goserver-xsession** package besides **x2goserver** package on Ubuntu 11.10 with Unity:

```
$ sudo apt-get install x2goserver-xsession
```

(None of the x2go manuals I've read so far did not mention this package but after installing x2goserver package apt-get says:

```
Suggested packages:
  x2goserver-printing x2goserver-compat x2goserver-xsession
  x2goserver-fmbindings x2goserver-pyhoca

```
so I tried to add x2goserver-xsession and it was helpful!)

After that the following settings in the x2goclient enabled connecting to the x2goserver:

Session type: GNOME

Session type: Custom desktop
Command:
gnome-session-fallback
gnome-session --session=ubuntu-2d
gnome-session --session=ubuntu

Take great care at writing this command strings into the x2goclient. The options are saved in the ~/.x2goclient/sessions file and you can check it with a text editor.

--rpr.

---

### Post by albatros78 on 2012-04-15
YES!!!! :guitar::guitar:

SOLVED! SOLVED! SOLVED!

Thanks a lot now it works.
 You have been legendary!:p

---

### Post by Yo Nas on 2012-04-16
Works like a charm :)
Thanks rpremuz!

---

