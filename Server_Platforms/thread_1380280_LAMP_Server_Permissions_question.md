---
title: "LAMP Server Permissions question"
date: 2010-01-13
forum: Server Platforms
---

### Post by KnottyMars on 2010-01-13
Hello All, 

I have a LAMP server running Ubuntu 8.04.03 Server edition running smoothly. Ive setup several websites on the server and all are ok, but I constantly have trouble with permissions. 

Everytime I setup a new domain to host, I setup a user specific to that domain. This allows SSH login specific to the domain. The problem I have is that everytime I setup ownership in the virtual directories for the users they belong to, the settings dont seem to stay. 

Initially it seems to work ok, but when I install Joomla and setup the webspace, I always seem to have to login to the server itself to chmod the folders I need to have writable. I cant chmod properly from my FTP client which is weird. 

Does anyone have any tips or anything to suggest on how to manage permissions? 

Currently I am doing the following: 

```

sudo mkdir -p {name of domain}/{public,private, etc...}

sudo usermod -g www-data {my user name}
sudo chown -R www-data:www-data /var/www/{directory for the domain}
sudo chmod -R 775 {folder path I need to change}

```

This works for a while but as I add new things to Joomla and I want to modify the folders, I always have to go back and redo the chmod and the chown commands to get them where I want. 

Any tips would be appreciated. 

Thanks,

---

### Post by bluefrog on 2010-01-14
must use setgid capabilities.

given joe member of the users group

if ls -al /home/
drwxrwxr-x jane users data

if joe mkdir /home/data/test
then ls -al /home/data/
drwxrwxr-x joe joe test

if you use setgid
chmod g+s /home/data
then joe mkdir /home/data/test1
ls -al /home/data/
drwxrwxr-x joe joe test
drwxrwxr-x joe users test1

Notice the difference of group ownership

---

### Post by Lars Noodén on 2010-01-14
> **KnottyMars said:**
> ...

Currently I am doing the following: 

```

sudo mkdir -p {name of domain}/{public,private, etc...}

sudo usermod -g www-data {my user name}
sudo chown -R www-data:www-data /var/www/{directory for the domain}
sudo chmod -R 7**5**5 {folder path I need to change}

```


You probably want to fix the group permissions on that directory so that the web server *cannot* write to it.  Otherwise, if something goes differently than expected, it would be possible for a visitor to upload something and then run it.  The group **www-data** should not have write access to anything on the web server.

---

### Post by KnottyMars on 2010-01-14
I think i see what you are doing. I also think I see the problem in what Im doing. I just tried setting up another domain to test it out.

I noticed I was including a group when I just needed to specify the user. Thanks for steering me in the right direction. 

Now that I have granted ownership to the user, the chmod from my FTP client works like a charm. 

Thanks

EDIT: thanks for the info Lars. what should I run to remove r/w from that group? Im pretty new to a non Gui server, but Im getting there :) thankfully it only affects one domain that Im using at the moment, but Ill be sure to make r/w specific to the user

---

### Post by Lars Noodén on 2010-01-14
> **KnottyMars said:**
> EDIT: thanks for the info Lars. what should I run to remove r/w from that group? Im pretty new to a non Gui server, but Im getting there :) thankfully it only affects one domain that Im using at the moment, but Ill be sure to make r/w specific to the user

Cool.  Shell is the way to go.  The example above with mode 755 will work or you can write the same thing this way:

```

# without the -R, just the one directory will get changed,
# with the -R everything including the regular files will get changed
sudo chmod **u=rwx,g=rx,o=rx** {folder path I need to change}

```

I recommend approaching the shell interface as scripting, with just-in-time learning.

---

