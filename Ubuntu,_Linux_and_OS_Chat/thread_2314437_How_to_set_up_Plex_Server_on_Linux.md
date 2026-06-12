---
title: "How to set up Plex Server on Linux?"
date: 2016-02-21
forum: Ubuntu, Linux and OS Chat
---

### Post by arpit3 on 2016-02-21
I want to set-up Plex Server on my Linux.  I tried following this guide here: [http://techchomps.com/how-to-set-up-the-plex-media-server-on-linux/](http://techchomps.com/how-to-set-up-the-plex-media-server-on-linux/)  but whenever I start the service with systemd: sudo systemctl start plexmediaserver.service the computer restarts. I don't know why this problem is happening. Can anyone help?

---

### Post by ajgreeny on 2016-02-21
What version of Ubuntu are you using?

I have been using Plex for a 2 years now and on my Xubuntu 14.04 it starts automatically at boot up, but of course, there has been a move from upstart to systemd in 16.04 which may affect this now, and I have not attempted to install on anything later than 14.04.

I use VBox to try out later Xubuntu versions so I am about to try installing Plerx on Xubuntu 16.04 and I will report back my success or failure.

---

### Post by ajgreeny on 2016-02-21
OK, I have just installed Plexmediaserver_0.9.15.3.1674-f46e7e6 on my VBox installation of Xubuntu 16.04 64bit and all is working as it should.  I did not have to start the server as it does so automatically at boot, and it works beautifully, just as it should.

I do not subscribe to the plex-pass which you will be prompted to do, but I do register the server, and login with a username and password, which you will also be prompted to do when you first go to the webpage-manager.  Life is made a lot easier in terms of file permissions if you add yourself to the group plex and add user plex to your own group.

You get to the webpage-manager in a web-browser with the URL [http://localhost:32400/web/index.html](http://localhost:32400/web/index.html) and this is where you will be asked to register, etc etc, and then set up your libraries of media; photos, videos, music, etc etc.

Try to name your media files and manage them as is suggested at [https://support.plex.tv/hc/en-us/categories/200028098-Media-Preparation](https://support.plex.tv/hc/en-us/categories/200028098-Media-Preparation) as it will make life a lot easier for you.

Good luck; let us know how it goes and ask again if you have problems.

---

