---
title: "LAMP help"
date: 2006-08-02
forum: Server Platforms
---

### Post by lokirulez on 2006-08-02
Hello all, 

I am trying to install LAMP (Linux-Apache-MySQL-PHP) on my Xubuntu 6.06 system. I went through the howto found here [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

Everything seemed to install fine, then I tried to set the root password for mysql with ```
mysql> SET PASSWORD FOR 'root'@'localhost' = PASSWORD('yourpassword');
```

I must have done something wrong because I got some error, I don't remember what it was exactly. Anyway I had a few more problems, so I decided that I would reinstall everything from scratch. I started by removing all the packages via ```
sudo apt-get remove pacakgename
```I wanted to make sure that the packages where gone so I ran locate mysql, and to my surprise there were several directories. So I began manually removing them, but this seemed like it would take too long. So I figured that when I reinstalled the packages they would just overwrite the previous ones. 

After I reinstalled everything, I am left without mysql...when I type mysql at the command prompt, I get 'No such file or directory.' My question is, even though I manually removed some directories, shouldn't they have reinstalled? Also does the apt-get remove actually get rid of anything?:(

---

### Post by Glut on 2006-08-03
standard apt-get remove will remove the data files, but not the configuration files (which are very small, so if you install again your configuration remains) to remove entirely you will need the --purge switch, i.e. apt-get remove --purge
I'm not sure why the binary has not been reinstalled. You may want to reinstall mysql again: apt-get install mysql --reinstall

---

### Post by lokirulez on 2006-08-03
That did not work for me. I removed all the pacakges with 
**sudo apt-get remove --purge packagename** and reinstalled them with 
**sudo apt-get install packagename --reinstall** after, I tried to run mysql and I got 'command not found.' 

The packages install without a hint of an error, what is happening here?:confused:

---

### Post by Glut on 2006-08-03
That's rather bothersome. I'd give it a go with a higher level tool such as aptitude, or download the file myself and install it with dpkg -i packagename.

---

