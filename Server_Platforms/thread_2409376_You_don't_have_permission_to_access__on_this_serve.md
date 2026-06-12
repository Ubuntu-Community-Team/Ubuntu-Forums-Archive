---
title: "You don't have permission to access / on this server after changing permissions"
date: 2019-01-01
forum: Server Platforms
---

### Post by sstacker on 2019-01-01
I am using AWS, I have an EC2 instance running Ubuntu 18.04 with Apache2. 
When I connect to my website using ip address I get > 403 Forbidden [COLOR=#000000][FONT=&amp]You don't have permission to access / on this server.[/FONT][/COLOR]
I am not sure when the problem started, but I think it has something to do with me typing sudo chown -R ubuntu:ubuntu /var/www and sudo chmod -R 770 /var/www.
I typed these 2 commands because I am using FileZilla to upload files to the website and at first I did not have permission from FileZilla so I had to do that.

Is it really what's causing the problem? Or it's something else?

Thanks

---

### Post by Holger_Gehrke on 2019-01-01
I'd say it is. Apache on Ubuntu usually runs as user www-data, group www-data with /var/www/html as DocumentRoot. By setting the ownerships and permissions on all files in /var/www the way you did, you've forbidden Apache from accessing anything. The solution should be as simple as changing the group ownership with 'sudo chgrp -R www-data /var/www', which would grant Apache full access (which might be problematic or not, depending on whether or not you're running any scripts that can / should write into files; you might want to do a 'chmod g-w /var/www/' to forbid the group (www-data / Apache) writing to files and directories and re-enable writing only for directories and files that need to be written to).

Holger

---

### Post by howefield on 2019-01-01
Thread moved to the "*Server Platforms*" forum.

---

### Post by volkswagner on 2019-01-01
You will learn over time about file permissions. It's one of those things
that takes practice, mistakes, reading, troubleshooting and employing better practice.

Always think twice before blindly issuing a chown/chmod/chgrp -R (recursive) command.
When you install a web application like Wordpress or other, there are usually specific 
permissions for folders and files. When you perform a recursive change, it applies to folders
and files. Rarely will a file need write and execute permissions.

FTP is not the best way to modify website content. Consider using ssh with scp. You can also
log in via ssh and modify files with text editor like nano. Always make a backup of a file
before editing.

Often times you can add yourself to the www-data group to allow you to write files to
the directory. 

Some people like to put websites inside their home directory, to give better control on permissions.

I have a poor memory, so I keep a cheat sheet of valuable commands (like the following).
# To recursively set permissions only on directories!
```
sudo find /path/to/base/dir -type d -print0 | xargs -0 chmod 755
```

# To recursively set permissions only on files!
```
sudo find /path/to/base/dir -type f -print0 | xargs -0 chmod 644 
```

---

