---
title: "Users, Groups, Chown, Confused?!"
date: 2011-01-17
forum: Server Platforms
---

### Post by DanHorniblow on 2011-01-17
I have been using ubuntu server for a few months now, but I still don't fully understand how to set permissions.

My server is running Apache with a web root within my home directory.

There is a PHP file manager installed, how do I give both my user, and the www-data user full permisions to read and write?

I currently have to chown my user to that directory whenever I want to make a change, then chown it back to www-data when I am finished so the file manager has write permissions.

---

### Post by endotherm on 2011-01-17
it sounds like adding yourself to the www-data group would be the easiest way to access the data after it is posted. I would probably also look into using setgid or setuid on the web root folder to force all files created within that folder to take on the group or user id of the web root. check to make sure the effect on executables is what you want though. 
[http://linuxmall.blogspot.com/2009/08/how-to-setuid-setgid-and-sticky-bit.html](http://linuxmall.blogspot.com/2009/08/how-to-setuid-setgid-and-sticky-bit.html)

that way, all files you create in the web root, (even as your normal user) will be "reowned" by the folder to <youruser>:www-data in the case of setGID, or www-data:www-data if you use both setGID and setUID. you will have to rely on the group permission however to control your access in the later case, so as pipemartinm said, chmoding the dir to 775 would be required in this case. if you just use setGID, you could use 755 instead as long as www-data does not require write access to the files (it shouldn't).

---

### Post by pipemartinm on 2011-01-17
If you **need **for your normal user to be able to edit the directory you can add it to the www-data group ```
/usr/sbin/usermod -a -G www-data user
``` and then change the directory to be writable by the owner and the group ```
chmod 775 /var/www/html/directory -R
```The **far** easier solution however is to just use sudo before any commands you run as user so that they run as root.
```
sudo vim /var/www/html/directory/page.html
```

---

### Post by DanHorniblow on 2011-01-17
I have created a group which both my user and the apache user and members.
How would I give this group full permissions of my home directory?

---

### Post by pipemartinm on 2011-01-17
Change the directory permissions so it's owned by that group

```

groupadd mygroup
mkdir mydir
chown -R myuser:mygroup mydir
ls -la mydir

```

Then set the permissions so it's writable by group members
```

chmod 775 mydir -R 

```

---

### Post by pipemartinm on 2011-01-17
Also, you should read through this before screwing around too much: [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by CharlesA on 2011-01-17
> **DanHorniblow said:**
> I have created a group which both my user and the apache user and members.
How would I give this group full permissions of my home directory?
That is not something you'd want to do.

If you want to have a folder in your home directory you can create a virtualhost and point it to that folder.

---

### Post by DanHorniblow on 2011-01-17
Right here is my problem, in my home directory there is a directory called public_html and another called dropbox.

The other day I followed a tutorial on installing dropbox on ubuntu server.

I have got a PHP file manager in /home/danhorniblow/public_html/college/files/files I want dropbox to sync its files to that directory instead of the one in my home folder that it has created.

Dropbox runs under the user danhorniblow. The file manager runs under the user www-data. How would I give them both read/wite privelages?

---

### Post by endotherm on 2011-01-17
> **DanHorniblow said:**
> Right here is my problem, in my home directory there is a directory called public_html and another called dropbox.

The other day I followed a tutorial on installing dropbox on ubuntu server.

I have got a PHP file manager in /home/danhorniblow/public_html/college/files/files I want dropbox to sync its files to that directory instead of the one in my home folder that it has created.

Dropbox runs under the user danhorniblow. The file manager runs under the user www-data. How would I give them both read/wite privelages?

well, I would start by adding danhorniblow to the www-data group, as pipermartinm suggested, but CharlesA's suggestion of an apache virtualhost is probably the best long term solution. 

/usr/sbin/usermod -a -G www-data danhorniblow

---

### Post by DanHorniblow on 2011-01-17
is www-data a group or a user?

---

### Post by endotherm on 2011-01-17
> **DanHorniblow said:**
> is www-data a group or a user?
both, just as DanHorniblow is both a user and a group.

---

### Post by DanHorniblow on 2011-01-17
oh that explains a few things :)

so if I was to add the danhorniblow user to the www-data group and then run sudo chown -r www-data:www-data /home/danhorniblow/public_html

would that give both the danhorniblow user and the www-data user full permissions in that directory?

---

### Post by endotherm on 2011-01-17
> **DanHorniblow said:**
> oh that explains a few things :)

so if I was to add the danhorniblow user to the www-data group and then run sudo chown -r www-data:www-data /home/danhorniblow/public_html

would that give both the danhorniblow user and the www-data user full permissions in that directory?

not quite but it's the first step. the second is to provide rwx rights to the owner group if they are not already set. as pipermartinm said, you do that with:
```
sudo chmod -R 775 <web root dir path>
```
then both the owner user and the owner group will have read write and execute permissions. 

this is not really a very secure configuration. if your user becomes comprised it can be used to destroy your web content or to post alterations to your site (like malware distribution). be sure you are comfortable with your level of risk and exposure for your usecase.

---

### Post by DanHorniblow on 2011-01-17
do you know the command for adding danhorniblow to www-data?

Considering this is just a home server I use to host my college work and projects, I don't think its that much of a risk. Or is it?

---

### Post by endotherm on 2011-01-17
for the command, see the bottom of post 9, or adapt pipermartinm's snippet, or use the "Manage Groups" feature of System->Administration->Users and Groups.

as for your risk analysis, my big question is, is the service accessible from outside your lan. if it is, then setting up a public website is not somthing I would recommend for a novice. there is jsut too much to consider. if that is not enough to worry you, then the assesment is based on the sensitivity and recoverability your data and how long it would take you to get back to functional after a cataophstrophic event (like someone leveraging a PHP exploit, and getting root on your server, and using it to attack your internal infrastructure). there is also a reputation factor if your server gets rooted and starts spewing malware/spam. risk analysis is not simple.

if your server only serves your lan and you have a router at your gateway, I'd say you are mostly good.

---

### Post by DanHorniblow on 2011-01-17
My server has got port 80 for HTTP traffic and port 443 for SSH trafic forwared to it from my router. I have setup a no-ip domain to my router.

Backups are done daily to another server on my LAN which is not on the internet.

I have implemented these sequrity messures:
Installed and configured shorewall to only allow port 80 and 443.
Changed "ServerTokens Full" to "ServerTokens Prod" in apache config
Turned off ServerSignature for apache
Disable root login via SSH
created a group called admin and added danhorniblow to it
only members of admin can sudo
installed Denyhosts to prevent from brute force attacks via SSH
installed Tiger security system scanner
installed Chkrootkit
installed Logwatch
Manualy update the server every few days (if there are any updates)


You sound like you know more about security than me. Do you think this is sufficient?

---

### Post by endotherm on 2011-01-17
> **DanHorniblow said:**
> My server has got port 80 for HTTP traffic and port 443 for SSH trafic forwared to it from my router. I have setup a no-ip domain to my router.

Backups are done daily to another server on my LAN which is not on the internet.

I have implemented these sequrity messures:
Installed and configured shorewall to only allow port 80 and 443.
Changed "ServerTokens Full" to "ServerTokens Prod" in apache config
Turned off ServerSignature for apache
Disable root login via SSH
created a group called admin and added danhorniblow to it
only members of admin can sudo
installed Denyhosts to prevent from brute force attacks via SSH
installed Tiger security system scanner
installed Chkrootkit
installed Logwatch
Manualy update the server every few days (if there are any updates)


You sound like you know more about security than me. Do you think this is sufficient?
it does look like you have been doing your homework. I do have a background in system and network security, but I do not have a lot of experience locking down apache or PHP, so the specifics of your apache config are best posed to experienced webmasters. 

I will say, your ssh security looks alright, though most around here would suggest you move to Keys instead of passwords. 

the problem is that you can only use tools to address known security issues. you for instance have installed denyhosts to address the specific known attack, bruteforcing.
since ssh has a well known surface and has been under constant attacks for decades now, the attack vectors are reasonably well known. apache itself is also well known, though it is very complex so the danger is less that it will get exploited, and more that it will be misconfigured in an exploitable way.

with PHP, there is much more danger, since the security comes part in it;s configuration and the way it works with apache, but also in the exact code that uses the langague features. it takes a very knowledgeable programmer to write code that is robust enough to stand up to all of the attacks possible on each of the individual features. to prevent sql/script injection, there is no one setting one can flip to make the problem go away; each page must be crafted to ignore dangerous inputs. when it comes to securing applications that you yourself post, the key is not in indentifying known vulnerabilities in the langague, but instead in using the features so that unknown vulnerabilities still can't be exploited to hurt you. 

the modifications you have made to your web roots permissions, have weakened your security against unknown exploits, by providing more access to your folder than is minimally required. it's not a signifigant weakening, but it does provide another small crack in your armor, if another security mechanism fails. 

put simply, to thwart one type of attack, you change a config or add a new utility to remediate it. to address unknown attacks of all types however, you layer your defenses, granting as little permission as possible to each operation, so that hopefully, when a new type of attack arises, you are in as good a place to fight it as can be. 

so thats enough pontificating. check this out:
[http://www.ibm.com/developerworks/opensource/library/os-php-secure-apps/index.html](http://www.ibm.com/developerworks/opensource/library/os-php-secure-apps/index.html)
[http://www.devshed.com/c/a/PHP/Secure-PHP-Programming/](http://www.devshed.com/c/a/PHP/Secure-PHP-Programming/)

---

