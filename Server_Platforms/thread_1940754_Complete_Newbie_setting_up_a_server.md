---
title: "Complete Newbie setting up a server"
date: 2012-03-14
forum: Server Platforms
---

### Post by Stutopia on 2012-03-14
Hi, I am completely new to Ubuntu and Linux in general and do not have programming skills. I have therefore found the advice on many websites confusing but have somehow muddled through. I have an old laptop which I have decided to use as a media server and have installed Ubuntu 10.04. I have loaded lots of mp3s onto it and named the folders by artist/album. I have installed Media Tomb and have been able to access this through my other windows PC which I will be using as the end device.
 
Questions: 
 
Can I use EasyTag to name my mp3s as many of them do not have the right information and are being shown as unknown in Windows Media Player on the end device?
 
Can I reset the files that Media Tomb has already found so that once Easy Tag is complete I can re-populate the database withthe right track information attached?
 
If I uninstall programs to free up disk space for media, what are the essential programs I should retain in order to continue using Ubuntu as a media server? I do not want to crash the whole system and lose all my data by removing the wrong file.
 
Thanks

---

### Post by cj13579 on 2012-03-15
Can I recommend a different application to MediaTomb... Subsonic. I has loads of great features (including Tag editing) and looks great. Downloading and installing it is easy too:

(Shamelessly stolen from their site) 

First, install Java: 
```
sudo apt-get install openjdk-6-jre
```

[Download]("http://www.subsonic.org/pages/download.jsp") the Subsonic .deb package and install it: 

```
sudo dpkg -i subsonic-x.x.deb
```

Notice that the installer configures your system to start Subsonic automatically when booting. After installing, open the Subsonic web page on [http://localhost:4040](http://localhost:4040).

Check out the full features [here]("http://www.subsonic.org/pages/features.jsp").

---

### Post by Bucky Ball on 2012-03-15
Welcome. Good choice with the current long-term support release for server applications: 10.04 LTS. Supported until April 2015. 12.04 LTS is out at the end of April and is also supported for five years.

LTS releases are intended for servers and production machines and their aim is stability, reliability and long support life. Servers are generally not intended for upgrading to the newest (and generally unstable) release every six months. Good start. ;)

As for removing programs, you won't be making much room. Much better option was to start with a base system (a regular server install) and add what you want (a lightweight desktop environment like xfce4 or lxde so you have a desktop to work on rather than a terminal) then build it up from there using a package manager. Working out what to strip back to get back to a simple base system and DE will take forever, be a series of breaking packages and tweaking to fix and is not really worth the effort.

---

