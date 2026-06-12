---
title: "Samba Security Question"
date: 2007-05-22
forum: Server Platforms
---

### Post by skrimpy on 2007-05-22
I am very new to this!  Please forgive and be gentle with me!

I have my Ubuntu machine and an XP machine.  I develop on localhost (on my ubuntu machine) but I edit stylesheets with an editor in XP.  I set up Samba to allow me to access my www files stored on my Ubuntu machine through my CSS editor on my XP machine.  

This is working perfectly and I am very pleased.  

I enter my username and password into Samba to mount the Ubuntu directories on my XP machine - XP then does its drive mapping thing and I can read and write those directories straight from windows.  

I am curious if I set up my Samba server to require a username/password at specific intervals (say an hour or two) throughout the day?  I keep all my work on my Ubuntu machine where outside of the CSS editor the Windows machine is mostly for personal use and games.  It's not so secure and  I don't like the thought of it being waltzed up to somehow and someone getting at work files over the network.

Can this be done?  Do I make sense?  A friend says he cannot think of how this would be done over a windows or novell server, but I was hoping Samba maybe could...  Thanks for listening ;)

---

### Post by tgm4883 on 2007-05-22
I forget what it is called (I use NFS now), but you can set specific directories to reauthenticate which will then prompt for the username/password again.

---

### Post by skrimpy on 2007-05-23
> **tgm4883 said:**
> I forget what it is called (I use NFS now), but you can set specific directories to reauthenticate which will then prompt for the username/password again.

can anybody else recall what this is?

---

### Post by tgm4883 on 2007-05-23
Took me 9 minutes of searching, but here it is.

Google

samba revalidate

Click on the first link

Read thread

Follow links posted

Etc.


You may want to install SWAT as it makes it much easier to configure SAMBA (or Webmin)

---

