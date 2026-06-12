---
title: "Proper permissions/owneship management on a web server"
date: 2013-11-09
forum: Server Platforms
---

### Post by zkvvoob on 2013-11-09
Hello,

Please help me figure out this situation:

I have a Ubuntu 12.04 server with ISPConfig 3 installed. Whenever a site is created, ISPconfig automatically creates folders under /var/www/clients/ and assigns ownership to a user like "web9" and a group "client1". Now, I use my own user to access the server via SFTP and said user is a member of the **root **group. Nevertheless, it is not granted permissions to either read or write to the new site's web (i.e. public_html) folder. The solution is simple, I get it - use **chown **and I have access. However, that results in the website platform (like Wordpress, for instance) to stop functioning properly.

So, could someone please explain to me in layman's terms how to manage my users and groups so that the owner of folders under /var/www is not changed and yet so that I could still upload/edit/delete files and folders there.

Thank you!

---

### Post by prshah on 2013-11-09
If the group "client1" has write access to the files, then add "client1" to your user's groups; eg ```
sudo adduser USER client1
```

---

### Post by zkvvoob on 2013-11-09
Thank you for taking the time to reply to me. I though I had tried this before but I went ahead and added my (ftp) user to the client1 group ahead anyway. So, here's the result:

```
zkvvoob@server:~$ sudo adduser zkvvoob client1
[sudo] password for zkvvoob:
The user `zkvvoob' is already a member of `client1'.
```

Then I proceeded to try and upload a random file to /var/www/clients/client1/web9/web which is owned by web9:client1 and has permissions 755. Here's the ftp output:

```
Status:    Connecting to <snip>...
Response:    fzSftp started
Command:    open "zkvvoob@XXX.XXX.XXX.XXX" 22
Command:    Pass: **********
Status:    Connected to *IP*
Status:    Starting upload of C:\Users\zkvvoob\Desktop\shakespeare1.jpg
Command:    cd "/var/www/clients/client1/web9/web"
Response:    New directory is: "/var/www/clients/client1/web9/web"
Command:    put "C:\Users\zkvvoob\Desktop\shakespeare1.jpg" "shakespeare1.jpg"
Error:    /var/www/clients/client1/web9/web/shakespeare1.jpg: open for write: permission denied
Error:    File transfer failed
Status:    Starting upload of C:\Users\zkvvoob\Desktop\shakespeare1.jpg
Status:    Retrieving directory listing...
Command:    ls
Status:    Listing directory /var/www/clients/client1/web9/web
Command:    put "C:\Users\zkvvoob\Desktop\shakespeare1.jpg" "shakespeare1.jpg"
Error:    /var/www/clients/client1/web9/web/shakespeare1.jpg: open for write: permission denied
Error:    File transfer failed
Status:    Starting upload of C:\Users\zkvvoob\Desktop\shakespeare1.jpg
Status:    Retrieving directory listing...
Command:    ls
Status:    Listing directory /var/www/clients/client1/web9/web
Command:    put "C:\Users\zkvvoob\Desktop\shakespeare1.jpg" "shakespeare1.jpg"
Error:    /var/www/clients/client1/web9/web/shakespeare1.jpg: open for write: permission denied
Error:    File transfer failed
Status:    Retrieving directory listing...
Command:    ls
Status:    Listing directory /var/www/clients/client1/web9/web
Status:    Directory listing successful
```

I simply don't understand.

---

### Post by prshah on 2013-11-09
> upload a random file to /var/www/clients/client1/web9/web which is owned by web9:client1 and has permissions 755. 

7**5**5 indicates that the group "client1" has no WRITE access. Either login as web9, or give the files and directories write permissions for group, eg permissions 7**7**5 or 7**6**5 (preferred for non-directories) ```
chmod 765 web
# OR
chmod g+w web

```

Please post back if you need more clarifications. Also remember that to MODIFY/OVERWRITE any existing files, those particular files must also have group write access permissions.

---

### Post by zkvvoob on 2013-11-09
Ah, magic! :D

Thank you, PRShah! One more thing: what (safe) permissions should the **files** have so that I can edit them through the FTP program?

---

### Post by prshah on 2013-11-10
> **zkvvoob said:**
> what (safe) permissions should the **files** have so that I can edit them through the FTP program?

I would SUGGEST 664 [ usr=rw- (6), grp=rw- (6), others=r-- (4) ]

Note that directories MUST have the executable bit (x) set, otherwise they cannot be entered or listed.

I really don't see any reason to leave files as executable on webservers, esp HTML, CSS, PHP or their like. I don't know if cgi, perl or such files require "x" to be set.

Point of order: You can really EDIT files via FTP; you can only overwrite, create or delete them. For editing, the usual procedure would be to SSH into the box and use an editor such as pico or vi.

---

### Post by zkvvoob on 2013-11-10
I see now. Thank you very much once again!

By the way, I didn't really mean "edit" the files via FTP, just download, open, edit on my computer and re-upload them to the server.

---

