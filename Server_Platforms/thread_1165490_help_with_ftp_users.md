---
title: "help with ftp users"
date: 2009-05-20
forum: Server Platforms
---

### Post by brown_ghost on 2009-05-20
hello to all, I'm a newbie and a bit overload with info but I still can't figure out how setup users to specific folders. Ok I just did a clean install of Ubuntu server 9.04. I install vsftpd, added users and I'm able to log in to home folder, I wanted to create users for my office workers as well as some of our clients and I want all our clients to only have permission to their home folders and my office workers to their home folders as well as our clients so that when clients log in to upload/down load files they only have permissions to their home folders and my office workers can go into their(client) folders and grab/drop files there, in short: clients to home folder only, co-workers to their home folder only as well as any client home folders. How can I do this? and I'm a bit confused by the instructions below, if I clear "chroot_local_user=YES" does that mean that everyone has access to home or root?

Securing FTP

There are options in /etc/vsftpd.conf to help make vsftpd more secure. For example users can be limited to their home directories by uncommenting:

chroot_local_user=YES

You can also limit a specific list of users to just their home directories:

chroot_list_enable=YES
chroot_list_file=/etc/vsftpd.chroot_list

I also noticed that when I log in to server from my ubuntu desktop pc that I have via ssh I'm able to see all folder from operating system and under home folder I see all folders for users I have created along a ftp folder, when I log in from a windows pc via ftp using one of those user names it just takes me to the users home folder and I'm able to drop files there, my question is what is the ftp folder there for if files are gonna go to home folders?

---

### Post by sickdude on 2009-05-20
There are a few things to keep in mind in this case, if i understand correctly that is.

Ftp is not ssh. When you use ssh you are able to see everything, especially when you sudo your way in.

When you correctly configure ftp then you can only go in your home dir (/home/username) and you can not go back (/home/) this because of the fact that you chrooted the user.

I could give you a example of a neat working ftp config file, but i use proftpd. Which is better documented by the Ubuntu community, and works a bit more user friendly.


A little tip on the side, dont disable a option like this:

#chroot_local_user=YES

Simply do it like this:

chroot_local_user=NO

You never know what config file does with its defaults, unless its documented of course ;-)

---

