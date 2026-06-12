---
title: "Chroot sftp users. In case your folder to chroot is not /home/user"
date: 2023-01-19
forum: Tutorials
---

### Post by kaynemo2 on 2023-01-19
Hi all! Posting this because I wish someone has done the same when I struggled with this seemingly simple task. 
Hope this helps someone.

[B]TASK
[/B]
- Let&#8217;s say we are in need to have a sftp access to our server for a certain user.
&#8232;
- Let&#8217;s also say we need the user we are giving access to to be limited to his/her folder without any way of browsing the system, let alone modify and or execute anywhere besides the user&#8217;s folder.&#8232;&#8232;Let&#8217;s also assume that the folder we are creating for the user is not simply /home/user, but like in my case is located on a separate volume in a far away folder. All the tutorials on internet I&#8217;ve found were using /home/user as the user&#8217;s folder. And it took my dumb ass _several hours_ to figure out why my user **WOULDN&#8217;T** get access to the folder I needed him to - that is because **NO ONE** mentioned that the chain of ownership and permissions needed for chrooting an sftp user has to start **ALL THE WAY** from the /

- I also needed this user to have the least amount of folders to click on before he/she could be able to upload/download. At the same time, from my side, I needed a uniform way to create folders so that I&#8217;d know where to upload the content (also I already had a huge FTP (before I made it into a sftp connected system) archive from a previous install, that I was reluctant to completely scratch and start over. To make my life easier I simply added **ONE **folder to each existing user folders with the same name to respect the permission/ownership necessity for chrooting sftp users. Surely I had to move all the existing content to the new additional folder, but since I used **MOVE** command instead of **COPY** - it was very fast despite the amount of files and folders inside each user's "homes".

If you are like me - this is the answer:

- we have a user [B]john
[/B]- he needs to be allowed via sftp and chrooted to a folder that is locally **/mnt/sdb1/POK/FTP/john/john/&#8232;  **<--- there is a reason there are 2 "john" folders - read on


**SOLUTION**

1. Create a user:[INDENT]1.sudo useradd john
[/INDENT]
[INDENT]2. sudo passwd john[/INDENT]
[INDENT]3. sudo usermod -d /home/john john   (home directory)&#8232;[/INDENT]
 
2. Create a folder for future ftp access:[INDENT]1. In case of a long chain of folders, create a double folder name at the end of the chain: /mnt/sdb1/POK/FTP/john/john/useable_folder (read/write is the last one in the chain)
[/INDENT]
[INDENT]2. Make sure that every single folder in the chain EXCEPT /useable_folder are set the following way:
[/INDENT]
[INDENT=2]1. owned by root (sudo chown root:root /mnt, sudo chown root:root /mnt/sbd    and so on all the way to the /mnt/sdb1/POK/FTP/john/john)[/INDENT]
[INDENT=2]         2. set permissions to all of the above folders to 0755 (sudo chmod 0755 /mnt) 
[/INDENT]
[INDENT=2]      3. set /useable_folder to be owned by john (sudo chown john:john /mnt/sdb1/POK/FTP/john/john/useable_folder)[/INDENT]
[INDENT=2]         4. set /useable folder permissions to 0777 (sudo chmod 0777 -R /mnt/sdb1/POK/FTP/john/john/useable_folder)&#8232; - or whatever other permissions you want - that will be the folder your user can manipulate in. 
[/INDENT]
 
3. open /etc/ssh/sshd.config in nano :[INDENT]1. Do this modification (uncomment the second line) :   &#8232;&#8232;
[/INDENT]
 
 
```
#Subsystem sftp /usr/lib/openssh/sftp-server&#8232;
Subsystem sftp internal-sftp&#8232;
```[INDENT]2. Add the following lines to the end of file:&#8232;&#8232;[/INDENT]
 
 
```

Match user john&#8232;  
ChrootDirectory /mnt/sdb1/POK/FTP/john/john/&#8232;  
ForceCommand internal-sftp&#8232;  
AllowTcpForwarding no&#8232;

``` 
4. Save the file and exit and restart sshd (sudo systemctl restart sshd)&#8232;

5. **Optional**: you can set what kind of access your sftp user has to the server. Initially, it is /bin/bash or /bin/sh which allows for the user to ssh to the server with his credentials. For security reasons if you need to limit this user ONLY to sftp connections without an option for a ssh login, add this to /etc/passwd file instead of /bin/bash or /bin/sh at the end of the line with users credentials:&#8232;&#8232;/usr/libexec/openssh/sftp-server&#8232;&#8232;Don&#8217;t forget to restart the sshd after this.&#8232;&#8232;If you get any errors on login through FileZilla - first make sure it is connecting via sftp (you can set it in the preferences, or you can type full address in the address field &#8212;>   sftp://10.20.30.40) , next thing to check is the correct owner and permission on the entire chain of folders from / to the /useable_folder. I&#8217;ve had to double check it a few times, because some of the attributes wouldn&#8217;t stick.

---

### Post by coffeecat on 2023-01-19
@kaynemo2, I've moved this post from Networking & Wireless to the Tutorials section. I've also removed the now-superflous solved and tutorial tags from the thread title.

Thank you for your interest, but please see our Tutorials Guidelines: [https://ubuntuforums.org/showthread.php?t=2143602](https://ubuntuforums.org/showthread.php?t=2143602)

In particular:

> **Tutorials should be supported.**
You are expected to offer support for your tutorial, within practical limits. If you fail to respond to requests for help or clarification within a reasonable time, or fail to update your tutorial, the thread will be closed or removed.

---

### Post by kaynemo2 on 2023-01-19
Thanks. I was just trying to help, actually.

---

