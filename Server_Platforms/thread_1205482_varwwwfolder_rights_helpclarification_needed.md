---
title: "/var/www/folder rights help/clarification needed"
date: 2009-07-06
forum: Server Platforms
---

### Post by jaime256 on 2009-07-06
Okay. I have set up the **Apache2** on my test server and here's what I've done so far.
1. created a directory under /var/www/folder.

2. Changed my docroot to this folder so I can put all my html files in that folder. I've done this and tested it, it does work for me.
 
3. The folder is still owned by root, but I don't want to change the ownership or anything like that just yet. I did have to manually give myself read and write access on this "folder" not the whole /var/www directory.
 
4. I installed samba and got the shares to show and since I also got the home directory to be shared I can see both, but I can only add/delete files in my home directory. This makes sense since I'm the user/owner. The folder being shared keeps prompting me for a user/password so I can't get to it. I do know it's a rights issue because I can log into my home directory without any problem.

5. Since I'm trying to understand and learn how the rights on the Apache2 server work, I decided to imitate the rights from my nas. The nas has a root account if you will and then you add the user accounts. Hence the smb.conf file. I figured if I just add rights for me to write to this folder so I don't have to worry about locking myself out like some people have done by using root, then that would make sense. Now I understand why the nas does it this way and that makes sense. So this is the reason for setting/testing this up, but I'm not clear about the rights to the folder without having to change owenership I guess. I took a look at this too, but there are no [sourcedocs] to add myself in the smb.conf file so I can read and write to it. I don't even know if this would allow me to access/change files in that root folder either.
[https://help.ubuntu.com/8.04/serverguide/C/configuring-samba.html](https://help.ubuntu.com/8.04/serverguide/C/configuring-samba.html)

Can someone tell me if this would be one correct way of doing this. I just want to have access through samba so I can edit the website like I did from my nas, but this is the one part I'm confused about. Do I really need to change the ownership of the folder to me in order to edit the files or can I do it a different way that still maintains the security of the folder, but so I don't have to ownit? If I have to ownit that's fine, but I just want to understand this rights access on the apache2.

I guess I could change the ownership and that would work or just move the files to a user folder and that may work too, but I would like to find out what the correct way would be so not to move or change things too much. I understand I need to change something, but again, just want to do it correctly. I'm trying to keep this short, but if it's not clear just let me know and I'll try to explain. I should note that since I'm not using a GUI I'm forcing myself to learn this a bit and it's also the reason taking me longer to set this up. I have also ordered an apache2 book so I am trying to figure this out on my own too, but I still need any little guidance you guys can help me with. Thanks.

---

### Post by mobilediesel on 2009-07-06
Go to [http://myy.helia.fi/~karte/install_apache_on_ubuntu.html](http://myy.helia.fi/~karte/install_apache_on_ubuntu.html)
It tells you how to enable the Apache2 Userdir module. You then make a directory under your home directory called public_html of which you obviously have full ownership. Basically:
```
$ sudo a2enmod userdir
$ sudo /etc/init.d/apache2 restart
```
Then under your home directory:
```
mkdir public_html
```
The page I directed you to explains it a bit more clear than I have but it's not too hard.

---

### Post by jaime256 on 2009-07-06
Thank you, I'll take a look at it. I have seen mention of the a2enmod... but just don't know what that is yet...

I took a look at it and that makes a bit more sense. Must that directory be named public_html or can it be anything else as long as the userdir's are activated? Just wondering if Apache only looks for that directory or not.

---

### Post by mobilediesel on 2009-07-06
> **jaime256 said:**
> Thank you, I'll take a look at it. I have seen mention of the a2enmod... but just don't know what that is yet...

I took a look at it and that makes a bit more sense. Must that directory be named public_html or can it be anything else as long as the userdir's are activated? Just wondering if Apache only looks for that directory or not.

I'm not sure if it only looks for public_html or not. You don't have to type public_html in the web address. Just [http://www.whatever.com/~username](http://www.whatever.com/~username) or [http://localhost/~username](http://localhost/~username) will take you to the index.html of "username"

---

