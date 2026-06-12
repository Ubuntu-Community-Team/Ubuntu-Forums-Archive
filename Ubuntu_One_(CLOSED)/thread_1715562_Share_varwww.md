---
title: "Share /var/www"
date: 2011-03-27
forum: Ubuntu One (CLOSED)
---

### Post by al_mic on 2011-03-27
Hi, 

I am trying to share my /var/www file between two computer by using Ubuntu One.

It seams that I can only synchronise directories from my home directory.

Do you know what should I do so that my /var/www dir from this PC will become synchronised ?

The goal is to have the same files used on another PC in /var/www


Thanks.

---

### Post by Scott Deagan on 2011-03-27
I'm new to Ubuntu One (only just got it working on 10.10)  and do not know how to sync anything outside of the home directory. Perhaps you could simply move your web directory (DocumentRoot) to your home directory? I take it that since you are using /var/www that you are not using named virtual hosts. If this is the case:

1. Create a directory called "www" (or whatever) in your home directory.
2. sudo vi /etc/apache2/sites-enabled/000-default
3. Change the line **DocumentRoot /var/www** to **DocumentRoot /home/[username]/www**.
4. Save and exit the editor (if using vi, :wq).
5. cp -R /var/www/* /home/[username]/www/
6. Restart Apache: sudo /etc/init.d/apache restart
7. Right-click on the www directory you created, select Ubuntu One, then "Sync Folder".

I know it's not exactly what you asked for, but it's a workaround that will work ;)

---

### Post by al_mic on 2011-03-27
Yes, I did think on changing the Document root on Apache or creating a symlink to my home dir, but I wanted to know if there is really no option of synchronising a directory from outside of /home.

Thanks for your answer anyway. Really good step by step tutorial.


So, does anyone know how can a directory like /var/www be synchronised with Ubuntu One?
I imagine that besides the graphic mode of right clicking on a directory and selecting the sync option, there is also a command that I can execute in a terminal.

---

### Post by Scott Deagan on 2011-03-28
According to this it's not possible: [https://wiki.edubuntu.org/UbuntuOne/FAQ/CanISyncAFolderOutsideMyHomeFolder](https://wiki.edubuntu.org/UbuntuOne/FAQ/CanISyncAFolderOutsideMyHomeFolder)

---

### Post by al_mic on 2011-04-04
Oh..
At least now I know.

Thank you!

---

### Post by duanedesign on 2011-04-06
Ubuntu One will not follow a symlink. You would have to move the folder into Ubuntu One folder (or $Home) and put the symlink where the folder used to be.

---

