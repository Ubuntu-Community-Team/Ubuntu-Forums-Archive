---
title: "Ubuntu restricted desktop"
date: 2018-03-05
forum: Ubuntu, Linux and OS Chat
---

### Post by john.ts on 2018-03-05
Hello,

Is there a way to restrict ubuntu (any flavor) for a user?
The only thing I want for the user to be able to access is:
- Chromium or Chrome or Firefox
- a text editor
- to be able to connect to a VPN connection.

I have seen a lot of "kiosk" setups but all of them have the browser to lock the session. although I do not mind this, I do not know how to allow the user to connect to a vpn.

I could not find anything that would allow the user to have a desktop but be limited to run/access only limited applications or settings. As a result, a very lockdown user. 

Any suggestions?

---

### Post by wyliecoyoteuk on 2018-03-05
You can do this via membership of groups.
For example if they are not in the sudo group they will be unable to install software or change system files.
[https://www.howtogeek.com/howto/ubuntu/see-which-groups-your-linux-user-belongs-to/](https://www.howtogeek.com/howto/ubuntu/see-which-groups-your-linux-user-belongs-to/)
If you create a blank desktop profile and only add the icons for the applications that you want them to use.They will not be able to add any themselves.
You need the dconf-tools package for that
[https://wiki.gnome.org/action/show/Projects/dconf?action=show&redirect=dconf](https://wiki.gnome.org/action/show/Projects/dconf?action=show&redirect=dconf)
[https://wiki.gnome.org/Projects/dconf/SystemAdministrators](https://wiki.gnome.org/Projects/dconf/SystemAdministrators)

---

