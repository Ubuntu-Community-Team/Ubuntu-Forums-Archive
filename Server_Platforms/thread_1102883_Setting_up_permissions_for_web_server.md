---
title: "Setting up permissions for web server"
date: 2009-03-22
forum: Server Platforms
---

### Post by botfish on 2009-03-22
I'm setting up a vps using Ubuntu LAMP and need some advice on how to setup permissions, and where to put my webroots.

Currently on my development server my web roots are in
/var/www/domain.name/htdocs 
all files below /var/www are owned by myuser and in group myuser. File permissions are -rw-r--r-- myuser myuser
The problem with this is if I want php to have write access to a file I have to change its permissions to -rw-rw-rw-.

I'm having trouble understand how I should setup my production server.

Should my webroots be in my home directory i.e. ~/www/domain.name/htdocs?
What should the user and group of files in the www directory be?
Where does the group www-data fit in to all this?

I will be using proftp as a FTP server.

Thanks for any help.

---

### Post by asimons999 on 2009-03-22
for mine I had my normal OS user as the owner of most things, and then created a group called www-users, and then preceded to add www-data to that group. Then if any software needs to access those files, you would just add the required user to the www-users group.

Though most software would probably be need to be configured to put the right permissions on new files / folders..

Eg: "force user", "force group", the one for putting the permission (mind blank right now), for Samba.

---

### Post by botfish on 2009-03-22
Thanks for your reply. I guess I was looking for a best practice way to do it. It seems like everyone has their own way of doing it - there is not right or wrong way?

---

