---
title: "Starting the X11 Desktop"
date: 2009-03-10
forum: Server Platforms
---

### Post by mistypotato on 2009-03-10
Hello,

After installing the X11 desktop environment on Intrepid 8.10 server, the GUI doesn't launch.

It still boots to the console.

There was no additional information and Googling didn't result in the answer.

Anyone know how to start (and automatically start) the X11 GUI?

thx

---

### Post by mistypotato on 2009-03-10
hmmmm....

I tried

/etc/X11/ sudo X                                (locked up)
/etc/X11/openbox  sudo openbox       (nothing)   
/etc/X11/  sudo xkb                             (nothing) 
/etc/X11/  sudo Xsession                    (command not found)
/etc/X11/  exec openbox-session        (Failed to open the display environment variable)

---

### Post by linuxisevolution on 2009-03-10
type startx or sudo startx.

---

### Post by linuxisevolution on 2009-03-10
sudo /etc/init.d/gdm start


That will work if you have gdm.

---

### Post by mistypotato on 2009-03-10
ok,

using the guide on installing a GUI on a server was too much for this newbie.

Dropping back to punt.

Re-installing 8.10 server and THIS time, sudo apt-get install ubuntu-desktop is the newbies choice.  :P

Gladly sacrifice a bit of performance and security for the ease of installing the ubuntu-desktop.

The reason I chose to install the SERVER version and then add the ubuntu-desktop (instead of installing the non-server version) is that it's easier to add all the LAMP components etc during the server install...at least for me.

Down the road one day, when I'm more knowledgeable with this stuff, I'll reinstall a bare, clean server only.  And by then I might have a shot at actually working from the command line ;)

---

