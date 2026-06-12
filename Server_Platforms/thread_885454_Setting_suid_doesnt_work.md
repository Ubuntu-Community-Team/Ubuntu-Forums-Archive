---
title: "Setting suid doesnt work"
date: 2008-08-10
forum: Server Platforms
---

### Post by micdhack on 2008-08-10
I have a directory which many people write on it. I have also php scripts that move files and other file operations which require ownership by www-data. So i though creating a bash script that looks like this

```

#!/bin/bash
chown -R www-data:www-data /var/www/incouol/development

```

so i save it and i do

```
sudo chown root:root script.sh
sudo chmod 4755 script.sh
```

From ssh console when i execute the file 
```
./script.sh
```
i get errors as well when run this command by a php script through web

php script:
```
<?
exec("./script.sh");
?>
```

To verify that privileges are ok i did an ls -la
```
-rwsr-xr-x 1 root      root        66 2008-08-10 12:03 script.sh
```

I tried every possible combination but still i get nothing. Any ideas?

---

### Post by RealPSL on 2008-08-10
You are walking a dangerous line making a script setuid enabled and worst yet trying to execute it through the web. I do not have the apparmor rules in front of me but that is one thing that could be blocking the execution.  The easiest way to find limit the cause of the problem is to install the php5-cli package.

```
sudo apt-get install php5-cli
```

You can then use the php binary to run the script. If this works we can determine that the failure is a result of something Apache is doing. You should also check the web server logs to see what it said.

---

### Post by micdhack on 2008-08-10
i am well aware of the dangers thats why the file doesnt get input, only changes ownership to a specific folder and is owner by the root which is the only one that has write permissions.

Even if apache blocks the script or it is a php thing still this doesnt explain why i cant execute the file even from a ssh console without getting erros for root permission.

I found how to bypass the problem by setting on /etc/sudoers for www-data user sudo access to this file without password. But i think that this is not the most secure way to do it.

---

