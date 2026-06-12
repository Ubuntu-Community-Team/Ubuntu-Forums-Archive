---
title: "add ubuntu server to gui"
date: 2008-01-24
forum: Server Platforms
---

### Post by NapsterX on 2008-01-24
i was going to add a gui to my ubuntu server and was wondering which would be the best route to go with Ubuntu or Xubuntu ?

---

### Post by Rhubarb on 2008-01-24
Aaah, that's the problem with linux, too much choice  ;)
First of all, there isn't much need for a GUI if you run a server.

If you do want a GUI, then it depends on a few things:

- Do you want a lean and mean server?  If so, use a small desktop with a small memory footprint (go for xubuntu or some small desktop).

- Do you want a full blown GUI that you're familiar with?  If so, go for Ubuntu or Kubuntu.

---

### Post by jfinkels on 2008-01-24
Or Fluxbox, which is "lighter" than Xubuntu.

---

### Post by NapsterX on 2008-01-24
i'm leaning more to the mean and lean side so i think my best bet is Xubuntu plus xubuntu is alot more light weight

---

### Post by NapsterX on 2008-01-24
but which one is better Fluxbuntu or fluxbox ?

---

### Post by jfinkels on 2008-01-24
Xubuntu is not really lightweight, depending on your point of view. It is marginally lighter than GNOME.

---

### Post by NapsterX on 2008-01-24
what is the command line to install fluxbox?
nvm i found it in another post 
server/command-line install
login
sudo su
nano /etc/apt/sources.list
comment(#) out the cdrom & uncomment all the repos
apt-get update
apt-get dist-upgrade
apt-get install x-window-system-core gdm fluxbox rox-filer leafpad eterm synaptic
type> reboot
select fluxbox from the session menu & log in to the gui
use synaptic to continue the build up.

---

