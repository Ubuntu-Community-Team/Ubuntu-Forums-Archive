---
title: "Chroot FTP Jail?"
date: 2010-07-30
forum: Server Platforms
---

### Post by NamiJason on 2010-07-30
I'm a newbie to Ubuntu and linux in general.  I had some limited use in college and now I've recently setup my own server to host websites for my clients.  

I need to find a way to create users who are constrained to their public_html folder.  Ive searched literally 20 or so forums to try and understand CHROOT and setting up a jail, but my expertise has been so limited I'm having trouble decoding a lot of what is going on and I haven't seen any clear posts that answer what it is I'm looking for.  I've been able to setup webpages and get them running fine, but now I  need to start dealing with clients ability to FTP into their site.

To me it seems pretty simple:
Create a user, allow them FTP access only, and constrain them to their /srv/www/webpage.com folder so that they can not go anywhere else and upload/change files.   

I'm not looking for so much as a list of steps to do although that would be nice, but an an understanding of what each step does so that I can get a better grasp on what I'm doing.

Thanks.

Running Ubuntu 10.04 LTS

---

### Post by arrrghhh on 2010-07-30
Perhaps the official [Basic Chroot doc](https://help.ubuntu.com/community/BasicChroot) from Ubuntu will help ya :D

---

### Post by vandorjw on 2010-07-30
> I need to find a way to create users who are constrained to their public_html folder.I don't know how much you know about the unix/linux file structure but I think it might be helpful to write down some basic ideas.

When you created a folder and/or file, there are 3 groups you need to take a look at.
The owner of the file/folder. The "group" that this file/folder belongs to..and all other people.
using the chown (change owner) and chmod (change permissions) commands you can restrict who has access to what files.

**_For example:_**

**chown bob:webcreators /srv/var/www**
*this command just made "bob" the 'owner' of the folder 'www' and it belongs to the group 'webcreators.*


[B]
chmod 000 /srv/var/www[/B]
*No one has permission do do anything. (read, write or execute)*
Lets change that...

**chmod u+w /srv/var/www**
*after this command the user bob (remember we made his the owner of the folder) has "write" permissions.*

**chmod u-w /srv/var/www** 
*This took write permission away from bob.*

u = owner
g = group
o = others

+w = add write
+r = add read
+x = add execute

-w = remove write permission
-r = remove read
-x = remove execute

**So...how could this info help you?**

We'll lets add all your users that want to make web-pages to the group "webadmins" (you'll likely have to create this group.) Give everyone in this group either read or write permission to folders that they need. and everyone else..the others...take their permissions away.

So, lets say that you have /srv/var/www/*many user-folders*/

You could give your GROUP Read and Execute permission to WWW and then, if they need to upload files...give them "write" permision to their own personal folder. Their own personal folder, they should receive ownership of it...and the groups should not have read, write or execute permissions.

[B]
How is this different from chroot?[/B]
even if users do not have "read" "write" and execute permissions, on files and folders, they can still see that files exist. Lets say that user1 has placed a file1 in his folder that contains his password and bank information. Even though user2 cannot edit or read **that** file...what he or she can do is **copy** that file, place it in his own folder, change the permissions and read it. (the original file will remain unchanged and user1 won't know anything has been compromised... If this is not an issue, I think just restricting folder and file permissions will work for your purposes.

A chroot simply will not allow user1 and user2 to even know of each others existence... so automatically, they will not be able to read or write to each others folders...



I hope that this informations / suggestions will help you, in case you don't get the chroot working right away.

Cheers - CC7

---

### Post by arrrghhh on 2010-07-30
Excellent guide, thank you for that CC7.

---

### Post by NamiJason on 2010-07-30
CC7,

Thanks for the quick reply.  I am familiar with the user permissions and owners.  If I understand this correctly I don't think it is exactly what I'm looking for.  Have patience with me though since I may be missing some crucial piece of info that I'm not aware of that is making my thought process incorrect.  I appreciate the longer, dumbed down version just incase.

Maybe I need to be more clear.  If I create a user, even though they don't have permissions and I have setup the passwd file like this:

ftpuser:x:1004:1004::/srv/www/website.com:/bin/sh 

regardless of their permissions they can still move up and down inside the server.  

I want the ftpuser to only be able to connect through some ftp type of software (ie not ssh) and only remain inside their website folder with read and write permission (no execute).  Changing ownership and permissions won't do this because they can still wander around.  I'd like it so when they connect they only know of their folder and they can only go down, not up.

---

### Post by vandorjw on 2010-07-31
Hey NamiJason,

I understand exactly what you want to do now. I have never set up the ftp - chroot before myself. The most I have done is follow the gentoo guide and set up a 32 bit enviroment inside my 64 bit server. I'll take a look into how to set up a chroot ftp jail. I probably won't reply until after 12 east standart time. gtm -5

cheers CC7

ps: this seems to have a pretty good guide. I'll take a look through it in the morning. published by red-hat. don't know how old it is.

[http://www.faqs.org/docs/securing/chap29sec294.html](http://www.faqs.org/docs/securing/chap29sec294.html)

---

### Post by inphektion on 2010-07-31
you are slightly over-complicating this but it's not your fault.  when thinking about creating a chroot it can be a difficult thing to do correctly and there are various ways to do it.  for example if you want a chroot for someone who ssh's into your server there is a chroot parameter right in sshd (if its newer version).  

Luckily for you I believe you only want chroot for FTP users.  I'd suggest getting vsftpd.  right in its config files it has options for chrooting users to the folder they login to.

this is what you want.  so if they manage a site at /var/www/site1
you have a ftp user named site1admin and when he ftp's in he is chrooted to /var/www/site1

if you have another site at /var/www/site2 then same deal with different user.  Take a look at chroot options built into vsftpd.  if you get stuck post your vsftpd.conf file and I can tell you what to modify to fix any remaining problems.

---

### Post by GreenDance on 2010-10-02
> **inphektion said:**
> you are slightly over-complicating this but it's not your fault.  when thinking about creating a chroot it can be a difficult thing to do correctly and there are various ways to do it.  for example if you want a chroot for someone who ssh's into your server there is a chroot parameter right in sshd (if its newer version).  

Luckily for you I believe you only want chroot for FTP users.  I'd suggest getting vsftpd.  right in its config files it has options for chrooting users to the folder they login to.

this is what you want.  so if they manage a site at /var/www/site1
you have a ftp user named site1admin and when he ftp's in he is chrooted to /var/www/site1

if you have another site at /var/www/site2 then same deal with different user.  Take a look at chroot options built into vsftpd.  if you get stuck post your vsftpd.conf file and I can tell you what to modify to fix any remaining problems.

Hi inphektion, AFAIK there is a slight glitch, (I could be wrong, but I don't think I am), let's say for example **User1** uploads a .php file that shows directory listings, it would be possible to go up levels and read other directories of the users and system files, so even though vsftpd has locked **User1** into his/her directory when uploading files, the .php file would grant **User1** to read all other files/folders on the server as the **User1** directory isn't locked to **User1**.

If I am wrong, can someone please correct me, I love to learn :)

---

