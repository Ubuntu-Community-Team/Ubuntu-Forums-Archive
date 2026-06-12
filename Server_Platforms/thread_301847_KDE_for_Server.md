---
title: "KDE for Server"
date: 2006-11-17
forum: Server Platforms
---

### Post by baylors on 2006-11-17
I was just wondering if I could install KDE to Ubuntu server? I have found several articles on how to do this but as a noob it doesn't seem to be going well. One article says to do this...
sudo apt-get install aptitude
sudo aptitude install kubuntu-desktop

It downloads and from what I can see installs but after a reboot I'm back to standard non-graphical interface](*,) . Where do i go from here? 

Thanks.

---

### Post by bernied on 2006-11-17
Have you tried, from the command line:

startx

If that gets you in, then you need to change your default runlevel so that you get a graphical login at startup - I think.

---

### Post by baylors on 2006-11-17
Yes. That doesn't work either. I was looking in the documents section and it also said that the server doesn't have xwindows either so i installed that as well and still back to command line after reboot. I have successfully installed Gnome, but coming from M$ KDE is a little easier for me. I would rather have KDE but I guess I'll just deal with Gnome. Thanks for the quick relpy.

---

