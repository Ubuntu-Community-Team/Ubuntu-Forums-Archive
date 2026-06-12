---
title: "How to run EvE online with Wine in Ubuntu 9.04?"
date: 2009-09-17
forum: Wine
---

### Post by Struki on 2009-09-17
If anyone has any idea on the topic, it would be great if he could lay it out here in plain text, in a step-by-step manner so I can actually understand what am I soposed  to do. Have in mind I'm a new user (of linux) but I know how to use a computer.

Thanks

---

### Post by terrraatech on 2009-09-17
right click on eve.exe and select "with Wine Programmstarter" I think because my Linux is German

---

### Post by Dragonfi on 2009-09-18
EDIT: I checked, and EVE is not yet in Play On Linux's database, so you should do what terraatech says, for now at least. You could still try and install (or reinstall) it trough PlayOnLinux, since it has some easy to use interfaces to more complex wine settings. (especially if it's not working correctly out of the box.)

Also, you could try Play On Linux, I'm not sure if they have included EVE Online, but there is a great chance that they done.

The advantage of using PlayOnLinux, is that (if the game is in it's database) will run setup scripts to run the game properly.

Link:[http://www.playonlinux.com/en/download.html]("http://www.playonlinux.com/en/download.html")

To get it just open a terminal and type the following instructions:
```
sudo wget [http://deb.playonlinux.com/playonlinux_jaunty.list](http://deb.playonlinux.com/playonlinux_jaunty.list) -O /etc/apt/sources.list.d/playonlinux.list
sudo apt-get update
sudo apt-get install playonlinux
```

I essentially quoted the instructions for Jauntry from the page I linked.

The first command will add their repository. (the server you connect to, and download from when using synaptic, add/remove, apt-get, etc.)
The second and third are updating the local database and installs playonlinux.
When installing, the computer migth complain that playonlinux's repo cannot be verified, that's normal at the moment, (since they do not provide security-keys.)

After this you can run playonlinux, to install/configure/play EVE, they have further instructions on how to do that on their site.

Also, Welcome in the world of Open Source, I hope you enjoy your time with us.

Good luck with getting the game running, I would join you in EVE, but my videocard keeps me back at the moment.

PS: if something is unclear in my post, feel free to ask.

---

