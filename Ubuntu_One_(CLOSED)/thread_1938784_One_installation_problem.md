---
title: "One installation problem"
date: 2012-03-10
forum: Ubuntu One (CLOSED)
---

### Post by tobiaf on 2012-03-10
Hi

I installed today Lubuntu 12.04 beta 1 and I'm having problems setting up Ubuntu one. When i run ubuntuone-installer the standard windows pops up. I press "sign me in with existing account" and suddendly the window turns into a grey color and the programm freezes.
Here is what i get:

```
tobia@smeagol:~$ ubuntuone-installer 
tobia@smeagol:~$ QGtkStyle was unable to detect the current GTK+ theme.
Unhandled error in Deferred:
Unhandled Error
Traceback (most recent call last):
Failure: ubuntuone.platform.credentials.CredentialsError: dbus.Dictionary({dbus.String(u'errtype'): dbus.String(u'CredentialsError')}, signature=dbus.Signature('ss'))



```

any idea? 

PS ```
tobia@smeagol:~$ u1sdtool -s
State: READY
    connection: Not User With Network
    description: ready to connect
    is_connected: False
    is_error: False
    is_online: False
    queues: IDLE

tobia@smeagol:~$ 

```

---

### Post by disabled20191128 on 2012-03-10
Hi,

It seems that you have found a bug...

Take a look at 

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by bitterblackale on 2012-05-08
I'm still getting the 'CredentialsError' when I try to run U1 from the Unity menu, but I managed to get filesync to work:

sudo ubuntuone-installer

ignore timeout errors, go through to 'finish'

close the programme

open terminal, run:
u1sdtool -c

then
u1sdtool -s

---

### Post by M_Mynaardt on 2012-05-08
Perhaps you installed it (inadvertently) with the Gnome dependencies?

I've not had too much trouble with using Ubuntu One in Lubuntu.  Here's the post I made about this; [http://ubuntuforums.org/showthread.php?t=1949533]("http://ubuntuforums.org/showthread.php?t=1949533")

***However,*** it's not my idea at all.  I got the instructions to install Ubuntu One without Gnome stuff here; [http://askubuntu.com/questions/82978/how-can-i-run-ubuntu-one-on-xubuntu]("http://askubuntu.com/questions/82978/how-can-i-run-ubuntu-one-on-xubuntu")

Hope that helps...

---

