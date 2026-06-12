---
title: "virtual box will not start in /etc/rc.local"
date: 2013-03-27
forum: Virtualisation
---

### Post by lance bermudez on 2013-03-27
My /etc/rc.local file has 
VBoxManage startvm fedora-18-lxde --type headless
exit 0

at the end. my server has to gui and I have to ssh in issue the command "VBoxManage startvm fedora-18-lxde --type headless" just to run this virtual server. I thought that  by putting the command in /etc/rc.local it would startup when the server does each time the server is restarted

---

### Post by SeijiSensei on 2013-03-27
This is just a guess, but /etc/rc.local is designed to run tasks as the root user before any of the desktop environment is started.  There's no X server running at that point, nor have any users logged in.  VirtualBox is designed to be run by ordinary users from a normal desktop session.  How that is done varies across desktop environments.  I use KDE so I can't help much with regular Ubuntu and the Unity desktop, but from reading [this]("http://askubuntu.com/questions/814/how-to-run-scripts-on-start-up"), putting the command in $HOME/.gnomerc might be the way to go.

---

