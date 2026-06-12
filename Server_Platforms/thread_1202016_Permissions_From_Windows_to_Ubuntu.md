---
title: "Permissions: From Windows to Ubuntu"
date: 2009-07-01
forum: Server Platforms
---

### Post by localfiend on 2009-07-01
Hi all.  I've recently set out to set up a Linux server to host files and a small private/secured company website.  I'm used to working in a windows environment (SBS 2003, IIS 7.0 for web and ftp) and have almost no experience with Linux.

Through some browsing here, and a lot of searching on google I've learned to use some basic Linux commands and have installed the 9.04 server edition.  I've got apache2 up and running, vsftpd for file transfers, and OpenSSH for windows so that I can make remote changes.

Currently I am using dreamweaver to design my site (It's fast and easy - and has worked great with all the windows servers I'm used too).  However, my lack of linux knowledge fails me when trying to do research in the area of permissions.  I am used to the windows concepts of groups.  I create a user, add him to a group, assign permissions to folders inside the website for that group and everything is good to go.

Can someone point me to some helpful reading material that explains the best/easiest/fastest way to get my permissions squared away?  As things stand right now, any web content I upload via vsftpd/dreamweaver gives me access denied errors when I try to bring things up in a browser.  I can't seem to get my site to work for anyone let alone password protecting sections and having multiple levels of access.  

(Keep in mind that until this past week I had no clue what any of the basic Linux commands were mkdir, ls, rd, adduser, sudo, apt-get are all new to me.)

---

### Post by jhannah on 2009-07-02
The concept of groups and users as implemented by NTFS ACLs is indeed present in Linux but there is another factor that, although also part of NTFS ACLs, isn't really used very often.

Beyond ownership, you need to also concern yourself with the mode settings of files and directories. Take the below directory structure as an example:

my_dir (directory) (user: user1, group: group1) (mode: rwx------)
|_ my_file1 (file) (user: user1, group: group1) (mode: rw-rw-rw-)
|_ my_file2 (file) (user: user1, group: group1) (mode: rw-rw----)
|_ my_subdir (directory) (user: user1, group: group1) (mode: rwx------)
   |_ my_file3 (file) (user: user1, group: group1) (mode: rw-rw-rw-)

The mode bits determine how the user/group applies to a given file or directory. r stands for 'read', w stands for 'write' and x stands for 'execute' (or in the case of directories, cd into). In this case, only user1 (or root, since root is not subject to permissions such as these) can access my_dir and everything below it. That is because only user1 has access to cd into my_dir, even though they have permissions below it, they could never reach the first directory in the tree and are thus denied access to the rest. The same goes for files. Permissions can seem daunting at first but once you read a little more, I think they will make great sense. Check out [http://www.freeos.com/articles/3127](http://www.freeos.com/articles/3127) for a longer and better written explanation of permissions.

That all being said, I can probably give you a set of permissions that will accomplish what you need. By default, Apache is configured to run under the www-data user and the www-data group and will serve content from /var/www. Although /var/www is owned by the user and group root, the last three mode bit settings are for everyone else and the /var/www directory should have r-x which means anyone else can read from it and cd into it. Depending on how exactly you might want to restrict permissions on your files, you could probably get away with simply making sure all of the directories are 'r-x' by checking 'ls -l /var/www/directory' and changing incorrect directories with 'chmod o=rx /var/www/directory'. The same would go for files but you can omit the 'x' in this case unless its an executible file such as a script of binary that you intend to run from a shell.

To get a quick look at the permissions for a given directory and below, you can use:

```
find /var/www/directory -ls
```

This will recurse through /var/www/directory and provide an ls for each directory or file. As always, check out the man pages for find and chmod for more details.

---

### Post by localfiend on 2009-07-06
Thanks jhannah, thats the kind info I was looking for.  I'll do some reading and see if I can't figure things out.  It's been so long since I've used the command line for anything that all of this stuff is a bit overwhelming.

---

