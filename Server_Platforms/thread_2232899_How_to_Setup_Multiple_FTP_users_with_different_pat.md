---
title: "How to Setup Multiple FTP users with different paths"
date: 2014-07-04
forum: Server Platforms
---

### Post by TFroehlich3 on 2014-07-04
Hello Everyone,
    I have a webserver that I hosts a couple websites off of for friends with small businesses. I was wanting to setup a FTP client on their end with their own log in info so they could upload their updated website files as they needed instead of having to wait on me to upload them for them. How can I set this up so they can remotely FTP files to their OWN folders? I would like it so once they log in they can only see their one "/var/www/domain.com/public_html" folder instead of them being able to see all the different domain folders on the server to simply eliminate the possibility of them uploading files to the wrong folder. If someone has a tutorial that I could run with that would be awesome!

Thank you!

---

### Post by nerdtron on 2014-07-05
Quick and dirty:

1. Create a folder for each, example: folder1 and folder2.
```
sudo mkdir -p /path/to/folder1
sudo mkdir -p /path/to/folder2
```
2. Create a user for each, example user1 and user2, and assign the folders for them.
```
sudo useradd -d /path/to/folder1 user1
sudo useradd -d /path/to/folder2 user2
```
3. Set password for each.
```
sudo passwd user1
sudo passwd user2
```
4. Change the ownership and permissions for their assigned folder so that only them read and write to it.
```
sudo chown user1:user1 /path/to/folder1
sudo chmod 700 /path/to/folder1
sudo chown user2:user2 /path/to/folder1
sudo chmod 700 /path/to/folder2
```

Now try using Filezilla to connect to the server and see if each user goes to their own directories.

---

### Post by sandyd on 2014-07-06
> **TFroehlich3 said:**
> Hello Everyone,
    I have a webserver that I hosts a couple websites off of for friends with small businesses. I was wanting to setup a FTP client on their end with their own log in info so they could upload their updated website files as they needed instead of having to wait on me to upload them for them. How can I set this up so they can remotely FTP files to their OWN folders? I would like it so once they log in they can only see their one "/var/www/domain.com/public_html" folder instead of them being able to see all the different domain folders on the server to simply eliminate the possibility of them uploading files to the wrong folder. If someone has a tutorial that I could run with that would be awesome!

Thank you!

```

sudo apt-get install pure-ftpd
cd /etc/pure-ftpd
sudo ln -s /etc/pure-ftpd/conf/PureDB /etc/pure-ftpd/auth/10puredb
sudo rm /etc/pure-ftpd/auth/70pam

```

Now, add one user.
```

sudo pure-pw useradd usernamehere -u useruidhere -g usergidhere -d /path/to/folder
sudo pure-pw mkdb
sudo service pure-ftpd restart

```

Now, you can add the rest of the users```

sudo pure-pw useradd usernamehere -u useruidhere -g usergidhere -d /path/to/folder
```
Run 
```

sudo pure-pw mkdb
```
When your done adding the users and pure-ftpd should instantly accept the new users

Make sure that the uid/gid set in pure-pw for the username can access the folder.

---

### Post by sandyd on 2014-07-06
> **nerdtron said:**
> 
```
sudo chown user1:user1 /path/to/folder1
sudo chmod 700 /path/to/folder1
sudo chown user2:user2 /path/to/folder1
sudo chmod 700 /path/to/folder2
```

Now try using Filezilla to connect to the server and see if each user goes to their own directories.

The webserver would then have issues accessing the files.

---

