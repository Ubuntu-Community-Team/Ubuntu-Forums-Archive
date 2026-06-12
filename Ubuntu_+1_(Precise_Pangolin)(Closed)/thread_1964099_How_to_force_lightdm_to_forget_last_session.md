---
title: "How to force lightdm to forget last session?"
date: 2012-04-23
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by getaceres on 2012-04-23
Hello, I've installed Ubuntu Precise and I wanted to try Kubuntu Active, so I installed it along the standard Ubuntu and Kubuntu installation.
Once I saw it and I noticed that I was redirected to Plasma Active no matter if I selected the normal KDE session I uninstalled it from within the active session. Now when I boot my machine it tries to start with Plasma Active and since it doesn's exist it sayis it's going to start the default session, but instead of getting to Unity (I don't care if 2D or 3D) I'm thrown to an empty screen with only the wallpaper.
If I try to reset lightdm (sudo service lightdm restart) it tries to start the same session (Plasma Active) which doesn't exist and also, there's a bug in Plasma Active which doesn't let me log out. So I'm stuck and I cannot force lightdm just to ask my password and forget about the last session. 
Where does lightdm save this configuration? How does it remember the last session? Can I force it to ask for my password so I can change the session manually?

---

### Post by grahammechanical on 2012-04-23
LightDM remembers the last session for every user. Yes?

Try file system /etc/lightdm/lightdm.conf.

In that file on my system I have this:

> [SeatDefaults]
user-session=ubuntu
greeter-session=unity-greeter

I only have Unity and no other user interface.

another place you might want to look is 

file system /var/lib/AccountsService/users

There you will find a text file for your user. What dose it list the XSession as? XSession=ubuntu?

We use System Settings>User Accounts to set automatic Log in to on or off.

Regards.

---

