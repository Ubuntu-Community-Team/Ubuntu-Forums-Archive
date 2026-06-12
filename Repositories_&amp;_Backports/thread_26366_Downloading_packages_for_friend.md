---
title: "Downloading packages for friend"
date: 2005-04-12
forum: Repositories &amp; Backports
---

### Post by OldPlanet on 2005-04-12
I have just installed Hoary on the computer of a friend, and he doesn't have any internet connection. Is there any easy way i can download the packages of certain applications (and all their dependencies), write them to a CD, and then install them on his computer?

I wrote all the files in my /var/cache/apt/archives to a CD. Then i copied all the packages on the CD to my friend's harddrive, and ran dpkg -i * in the folder i have copied the packages into. I wanted to install excactly the same packages as i had on my system, but when i did this he ended up with several broken packages.

And does all the packages i install really go to /var/cache/apt/archives? I have for example XMMS installed, but i can't find any XMMS package in /var/cache/apt/archives.

---

### Post by maurom on 2005-04-12
First of all, make sure you have all downloaded packages in the cache (don't run apt-get autoclean or apt-get clean).

Then, AFAIK, there are three alternatives:

1. Use the apt-zip utilities (apt-get install apt-zip), which allows you mark packages for installation in one machine (non-networked), and then download those packages in another machine with Internet connection, so you can transfer that files in a zip-drive or cd-rom to the original machine and then install them there.

2. Make a full backup of your archive, copy it into a cd, restore in the non-networked machine and then use apt-get dist-upgrade, aptitude or synaptic to fully install the packages. The following steps were taken from [www.ubuntuguide.org](www.ubuntuguide.org)

To backup downloaded repositories cache...
mkdir -p $HOME/backup/var/lib/
sudo cp -R /var/lib/apt/ $HOME/backup/var/lib/
mkdir -p $HOME/backup/var/cache/
sudo cp -R /var/cache/apt/ $HOME/backup/var/cache/
mkdir -p $HOME/backup/etc/apt
sudo cp -R /etc/apt/ $HOME/backup/etc/
sudo chown -R $USER $HOME/backup/

To restore downloaded repositories cache...
sudo cp -fR $HOME/backup/var/* /var/
sudo cp -fR $HOME/backup/etc/apt/* /etc/apt/

3. Make a backup of your archive, copy it into a cd-rom, then copy to any folder in the destination machine.
Use the apt-ftparchive utility to transform the folder into an "usable" repository

See apt-doc for more information

I'm currently using the third option to upgrade my dial-up networked machine... ;-) 

(please excuse my english, my natural language is spanish)

---

### Post by UbuWu on 2005-04-13
It can be done easier... don't remember exactly how, but if you search the forums you can find a way to make a cd repository which you can just add as an extra source to your repositories.

---

