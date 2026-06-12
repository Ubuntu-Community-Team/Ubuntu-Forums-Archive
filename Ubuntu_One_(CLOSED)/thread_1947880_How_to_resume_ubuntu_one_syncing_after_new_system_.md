---
title: "How to resume ubuntu one syncing after new system installation"
date: 2012-03-27
forum: Ubuntu One (CLOSED)
---

### Post by zacktu on 2012-03-27
When I installed 11.10 I
[LIST]
[*]used dpkg to get a list of all installed programs
[*]copied contents of my /home partition to another drive
[*]installed ubuntu 11.10 allowing the installation to write over my /home
[*]restored /home
[*]restored all installed programs that i wanted to keep
[/LIST]

After the installation I waited a few days before allowing u1 to start up again because I wasn't sure what it would do.  
[LIST]
[*]Some files in my /home partition were newer than those in the u1 repository.  Would u1 replace a file in its repository with the newer file in /home?  
[*]What is the implication of "sync locally" in the u1 dashboard? How is that different from right clicking a folder icon in nautilus and selecting "syncronize this folder"?
[/LIST]

I also use rsync to a NAS, but thought it was good to have a repository in the cloud.  I know exactly what rsync is going to do, but I don't know what u1 is going to do.

What should be my u1 strategy when I install a new system?

---

### Post by duanedesign on 2012-04-06
If you have synced files to your Ubuntu One cloud storage and are now setting up a new computer or re-installing your operating system, it's important to not copy over the following folder from a backup copy you may have saved: ~/.local/share/ubuntuone

As long as you do not copy that folder over, you are safe to setup Ubuntu One on your computer as you normally would following the setup instructions.

The danger of copying ~/.local/share/ubuntuone from a backup to your new computer and then setting up Ubuntu One is that your files will be deleted. The Ubuntu One client will look for information about your local files in ~/.local/share/ubuntuone, see that there were files on the system and see that those folders are empty. Once you setup Ubuntu One, the client will tell the server to delete all the files from the server.

---

