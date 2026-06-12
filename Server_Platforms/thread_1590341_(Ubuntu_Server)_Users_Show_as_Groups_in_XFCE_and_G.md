---
title: "(Ubuntu Server) Users Show as Groups in XFCE and Gnome"
date: 2010-10-07
forum: Server Platforms
---

### Post by Zanthir on 2010-10-07
On my Ubuntu Server 10.04 box, I was using XFCE and was trying to set up Subversion. One of the steps is to add the user www-data to the subversion group. Foolishly, instead of doing this from the command line like a pro, I tried to do it from XFCE. Then I tried from Gnome (after installing it). Then I ended up doing it from the command line anyways.
 
The problem is the instructions tell you to go to gnome-system-tools>users in gconf-editor and check "show all users." When I was in XFCE, I couldn't find anything like xfce-system-tools, or "show all users," and checking "show all users" under gnome-system-tools didn't work. So, since the gnome-system-tools didn't seem to work in XFCE, I installed Gnome. Same problem.
 
In the end, I learned that these users were showing up as groups only in the GUI, but were in fact both groups and users. And adding www-data to the subversion group took about a minute to look up the command and type it in from the command line.
 
My question is this, is there any way to fix this? Or is this just one reason for perhaps installing Xubuntu if I want to use XFCE with my server instead of installing Ubuntu Server and then adding XFCE?

---

### Post by sheilaellen on 2010-10-10
I think this problem may not be Xubuntu-specific as I've just come across it in Ubuntu (Maverick Meercat).

---

### Post by SeijiSensei on 2010-10-10
By default, a group is created with the same name as each user and that group is designated as the user's primary group in /etc/passwd.  Typically the group has no other members except the user, and group members have no rights to the user's home directory by default since /home/user has 700 permissions.  

Does that answer your question?  I use neither XFCE nor GNOME.

---

### Post by Zanthir on 2010-10-11
Basically, I'm wondering why the way users are setup in Ubuntu Server is different than in a normal desktop edition, and possibly what the difference is. 
 
As far as I can tell they are functionally the same from the command line whether in Gnome, XFCE, or just in the Ubuntu Server shell.
 
I'll probably just file a bug about this. I'm marking this solved (since I'm moving it to bugs in launchpad).

---

### Post by arrrghhh on 2010-10-11
Honestly if you're using the Server edition, you probably shouldn't be using a DE to create users... That's just my .02.  If you want a GUI/DE, install ubuntu-destkop not server.

---

