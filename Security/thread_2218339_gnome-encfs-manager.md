---
title: "gnome-encfs-manager"
date: 2014-04-20
forum: Security
---

### Post by Dondermans on 2014-04-20
When launching gnome-encfs-manager it is listed in the  'Processes' list of the System Monitor, but the GUI does not appear. Hence I cannot mount the encrypted directory.

I am on a fresh install of Ubuntu Gnome 14.04 LTS. Cryptkeeper seems to be porked, because it uses the old notification area which is not available in 14.04 anymore. To access my encfs-directory, I installed gnome-encfs-manager 1.8.8~ubuntu14.04.1, using the terminal:
sudo add-apt-repository ppa:gencfsm/ppa 
sudo apt-get update 
sudo apt-get install gnome-encfs-manager

When I launched gnome-encfs-manager for the first time, I got to the GUI and I was able to mount the encfs directory. Once. I rebooted Ubuntu. When I tried to launch gnome-encfs-manager again, gnome-encfs-manager is listed in the 'Processes' list of the System Monitor. The GUI does not appear.

I tried removing the package using sudo-apt-get remove gnome-encfs-manager and reinstalling it, without avail. Any thoughts?

---

### Post by cariboo on 2014-04-20
Moved to Security Discussions, as this is security related.

---

### Post by Dondermans on 2014-04-21
I can access my data using the terminal. To mount ~/.crypt with raw storage in ~/crypt: 

encfs ~/.crypt ~/crypt 

I marked the thread as solved.

---

### Post by Dondermans on 2014-04-21
Hmm... turns out I cried wolf. 

When gnome-encfs-manager is started, the manager goes directly to the background. The manager can be accessed via a 'task bar' that appears when the mouse cursor is moved to the bottom edge of the screen:
[IMG]http://i.imgur.com/4Y8aVqw.jpg[/IMG]

---

