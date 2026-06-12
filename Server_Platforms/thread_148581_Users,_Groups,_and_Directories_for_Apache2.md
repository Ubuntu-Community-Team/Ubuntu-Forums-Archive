---
title: "Users, Groups, and Directories for Apache2"
date: 2006-03-22
forum: Server Platforms
---

### Post by Ewald on 2006-03-22
I am running Apache2 and would like some advice and suggestions on directory structure and permissions for running virtual hosts.

User and Group in the Apache config file is set to www-data. Do I need to be added to this group?

I am planning on putting the virtual hosts in the /var/www directory. For example, /var/www/vhost1, /var/www/vhost2, etc. I will be the only person with access to the server. 

Root currently owns /var/www. Should I become the owner of /var/www so I can make new files and directories, or should I leave root as the owner? What are some of the best practices for setting directory and file permissions of web content?

Thanks

Ed

---

### Post by Ewald on 2006-03-23
Here is what I have done.

1. I added myself to the www-data group.
```
sudo adduser myuser www-data
```

2. I created a new directory for my virtual host data.
```
sudo mkdir /var/www/myvhost
```

3. I changed the owner and group of the new directory.
```
sudo chown myuser:www-data /var/www/myvhost/
```

Now, I can add the html, log, cgi-bin directories for this virtual host as needed. Any files and directories I add, however, will default to my users group, not www-data. Will I have to change the group of every file I create here? What about the log directory, will www-data need write permission?

Any other advice? I'm surprised that there haven't been any replies to this. Is this the proper forum?

Thanks

---

### Post by kmi on 2006-03-24
According to LordHunter317 in [this]("http://ubuntuforums.org/showthread.php?t=146223") thread :

[QUOTE=LordHunter317]You shouldn't make the user a member of the www-data group.  That's for Apache and Apache only.

What you should do, is simply give the user ownership of /var/www.  There's no reason for Apache to own it, nor should it.  The person editing the files should own it.  

You just have to make sure to give Apache read access to all the files in there.   The simpliest way to do that is to ensure they're world readable.

So, to sum up:***NEVER EVER EVER EVER EVER SET PERMISSIONS ON ANYTHING TO 777.***  I can't stress that enough.  It's never a solution.

To control /var/www, do the following:```
sudo chown me.me -R /var/www
sudo chmod -R o=rX /var/www
```

In your specific case, take yourself out of the www-data group:```
sudo deluser me www-data
```

Logout and in to make the membership changes work.  This is likely the reason why it didn't work before.[/QUOTE]

That's what I've done... :)

---

### Post by Ewald on 2006-03-24
Thanks for the help kmi, that was exactly what I was looking for. I searched the forums, but apparently not well enough ;) .

This turns out to be a very easy solution. The things that were confusing me initially were the significance of the User and Group directives in Apache, and permissions for the log files.

I'm still not exactly sure what the User and Group directives do, but they don't seem to have any relevance here.

I thought I would have to make the log files for each vhost writeable to Apache in some way. However, I now own them with the permissions -rwxr-xr-x, and Apache is writing to them without a problem.

---

