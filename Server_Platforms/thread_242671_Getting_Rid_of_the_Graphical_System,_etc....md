---
title: "Getting Rid of the Graphical System, etc..."
date: 2006-08-24
forum: Server Platforms
---

### Post by louie55 on 2006-08-24
I have installed Ubuntu "Breezy Badger" on a system that I intend to use as a server. I then upgraded to "Dapper Drake". I have installed and configured my server apps. (Apache/PHP5, OpenSSH, ProFTPd, and MySQL). My problem is, the server only has a 3GB drive and 2.8 were being used. I used the GUI application remover and removed a bunch of stuff I didn't need, but I am still only down to 2.1 GB USED. I need more space. I don't really need the Graphical part of Ubuntu as I can run things well enough with the Command-line interface, so I thought getting rid of all the graphical stuff would free up a lot of hard drive space. I don't just want to uninstall it and leave it there, I want to DELETE it off of the hard drive to free up some space. Any tips on how to do this without breaking anything would be appreciated.

Also, if there are any other packages that you know of that take up a lot of hard drive space that I won't need to run the server programs listed above or to administer a server, please let me know what those are and how to remove them. I only need the bare essentials.

Thanks.

P.S. I know there is a "Server" option when installing Ubuntu, but I already have everything configured and didn't want to reinstall.

Louie

---

### Post by dbr on 2006-08-24
Try apt-get remove ubuntu-desktop, or apt-get remove *gnome*
Then, apt-get clean (all as root)

/var/cache/apt/packages will probably have stuff cached, if you've got everything setup, you can probably rm * in it

To see where the space has gone :
du -h --max-depth=1 /
- Ben

---

### Post by lamego on 2006-08-24
You could try to remove every package from the meta-package ubuntu-desktop:
```
apt-cache show ubuntu-desktop | grep "Depends:" | sed "s/Depends://" | tr -d "," | sudo xargs apt-get remove 
```
Please make sure you append a space " " on the end of the line.

---

### Post by schiznik on 2006-08-24
I'm not sure thats the best of ideas - its just asked me to remove things like bash....

---

### Post by snooptodd on 2006-08-25
This wont be easy or quick you should probably save the conf files for the apps you want and reinstall.

That bieng said, I like aptitude to do things like this. It has a funky ui so play with it, read the help, etc. before doing anything big.

openoffice is HUGE that should remove alot of space.

---

