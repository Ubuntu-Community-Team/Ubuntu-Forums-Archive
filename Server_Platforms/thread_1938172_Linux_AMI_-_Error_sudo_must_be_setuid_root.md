---
title: "Linux AMI - Error: sudo: must be setuid root"
date: 2012-03-09
forum: Server Platforms
---

### Post by pavi_elex on 2012-03-09
I am using Amazon Linux AMI. I do not have password of root. I am just a user.
I was executing commands using sudo. It did not ask me any password and command was executed fine.
Ex- sudo rm -r /home/username/directoryname
or sudo yum install software-name 
and it was working fine.
But unfortunately I have set permission of /usr/bin is 777 (drwxrwxrwx).
that is why permission of /usr/bin/sudo is become 777 (-rwxrwxrwx).
Now when I am using any sudo command , I get an error
       ```
sudo: must be setuid root 
```The changing permission of /usr/bin will solve the problem but I am not able to change the permissions of any file. when I use chmod to change it, 
it says:
       ```
 chmod: changing permissions of `filename': Operation not permitted 
```and when I use sudo chmod 
 it says :
    ```
 sudo: must be setuid root 
``` I do not have root password. even I am not permitted to see root directory.
Please solve this problem. I am not able to execute any command now.

---

### Post by Jon Monreal on 2012-03-09
Perhaps you can talk to Amazon? Without the ability to execute any command, I don't see how you would fix the problem.

---

