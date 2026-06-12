---
title: "[Tablet] SU password 13.10"
date: 2016-05-17
forum: Ubuntu Phone and Tablet
---

### Post by Vertechs on 2016-05-17
I need to use sudo but none of the default passwords seem to work. I never entered another password anywhere. I've tried re-installing but its still the same issue

---

### Post by PaulW2U on 2016-05-17
I think some clarification and further information is needed here. Are you saying that you have installed Ubuntu 13.10 Saucy Salamander on a tablet?

Ubuntu 13.10 hasn't been supported since 17th July 2014 but in any case there are no **default** passwords.

In order to use administrator privileges it is usual to use the password of the user that installed Ubuntu which is often the only user that exists on a system.

Have you tried using **sudo** before the commands that you wish to use as an administrator?

See also [RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Vertechs on 2016-05-18
Sorry it wasn't very clear in my post. I have Ubuntu Touch 13.10 installed on my nexus 7 2012 version because it was the last version that supported grouper. When I try to use a command with sudo in front, it asks for a password. I've tried "Ubuntu" and every other default password I could think of, none worked.

---

### Post by PaulW2U on 2016-05-18
> **Vertechs said:**
> I've tried "Ubuntu" and every other default password I could think of, none worked.
There is **no default** password. 

If you are logged in as the user that has administrator privileges then the only password that *should* work will be that user's password. Now that you've confirmed you are using **sudo** I'm out of ideas as you obviously are aware of your own log-on password.

---

### Post by Vertechs on 2016-05-18
Ubuntu Touch does not support multiple user accounts, and I never was asked to enter a password, so I'm not sure what it would be anyway.

---

### Post by donquichot2016 on 2016-05-18
On Ubuntu Touch 15.04 it's the password you use to unlock the screen. This can be a passcode or a password.

---

### Post by Vertechs on 2016-05-18
There is no screen lock on 13.10, just a swipe to open. Would it be possible to run the generic version of 16.XX on grouper?

---

### Post by donquichot2016 on 2016-05-19
Apparently it's possible to install at least desktop Ubuntu 14.04 on grouper: [askubuntu thread]("http://askubuntu.com/questions/633788/installing-ubuntu-touch-on-nexus-7-2012-now-that-it-is-no-longer-supported"), [blog post]("https://www.e-vanicek.cz/2016/01/jak-na-novejsi-desktopove-ubuntu-na-starem-nexusu-7-2012.html") & [wiki]("https://github.com/Tasssadar/multirom/wiki/Grouper-Native-Desktop-Linux"). Though I don't know if that works smoothly.

---

