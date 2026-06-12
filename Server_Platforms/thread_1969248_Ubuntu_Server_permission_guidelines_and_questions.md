---
title: "Ubuntu Server permission guidelines and questions"
date: 2012-04-29
forum: Server Platforms
---

### Post by dlboutwe on 2012-04-29
I am fairly new to the linux community but I am powering through most of my issues thus far thanks to the wealth of information online regarding solutions to various issues. One problem that I am having has been kicking my butt for the past few days and I can't seem to form a google query direct enough to find a solution. Let me give you a little back story.

I recently rented a VPS and installed Ubuntu Server 10.10 on it. I installed it with the defaul LAMP stack, mail server, and ssh options. Everything was going swimmingly, until I came across the permissions for ftp (installed vsftpd) and other web development issues. My situation is that I would like to create a development environment where I can add developer to certain projects, but I want to restrict permission to those specific directories for both regular access and ftp access. For example:

in my /var/www directory, I have 2 sub-directories, call them 'a' and 'b', so the I would add developers to groups 'deva' and 'devb' and chown those directories to be something like don:deva 755

Now, that is all well and good for regular access, but a few of my projects are wordpress related and allowing for the full range of wordpress functions (i.e. uploading crap!), to me, would seem to take a separate group to own the wordpress folders. When I change the owner of everything in the /var/www/ directory to www-data, all is well and good but the devs would then need to be added to the www-data and have access to the other projects and I understand that to be unsafe.

To sum up the entirety of my issue:

How do I set my permissions so that 

a) The developers in the different groups only have rw access to their specific projects.

and

b) Wordpress can upload files.

If I get some better insight on these topics, I feel like I can fix the ftp situation on my own, but these are what is really stumping me.

Thanks in advance for any support!

---

### Post by nothingspecial on 2012-04-30
*Thread moved to **Server Platforms**.*

---

### Post by Jonathan L on 2012-04-30
Hi dlboutwe

> 
in my /var/www directory, I have 2 sub-directories, call them 'a' and 'b', so the I would add developers to groups 'deva' and 'devb' and chown those directories to be something like don:deva 755

but a few of my projects are wordpress related and allowing for the full range of wordpress functions (i.e. uploading crap!), to me, would seem to take a separate group to own the wordpress folders. When I change the owner of everything in the /var/www/ directory to www-data, all is well and good but the devs would then need to be added to the www-data and have access to the other projects and I understand that to be unsafe.

To sum up the entirety of my issue:

How do I set my permissions so that 

a) The developers in the different groups only have rw access to their specific projects.

and

b) Wordpress can upload files.



Here's how I'd go about it.

Let's say web server is running as www-data:www-data and /var/www is  whatever:www-data 555

/var/www/a is whatever:deva, 775 and group-sticky
/var/www/b is whatever:devb 775 and group-sticky
/var/www/wordpress is www-data:whatever and 755 or whatever:www-data and 775 and group-sticky

Group sticky (chmod g+t file) is essential for shared work: it means that any file created in that directory will inherit the group from that directory.  Subdirectories also inherit group-sticky on creation.  Change everybody's umask to 002, so they permit group-write.

Each person in deva can create and edit all the files in a/, devb people can do it b/ and word press, runnign as the file web server, can write in wordpress/

Does that look like it will solve your requirements?

FTP: for vsftp, edit the config file /etc/vsftpd.conf and set umask to 002

Hope that helps.

Kind regards,
Jonathan.

---

### Post by dlboutwe on 2012-04-30
Jonathan,

That has helped tremendously. I am not sure exactly what I was thinking on that whole issue, but your post was excellent and informative. I need to learn more about the sticky bit and the unmask, but your post has solved my immediate problem.

Wordpress has 90% functionality, but I think that is because I restricted the www-data's ownership exclusively to the wp-content folder and that is fine for me now that I have the ftp working.

I really appreciate your help with this issue, thank you.

Don

---

### Post by Jonathan L on 2012-04-30
> That has helped tremendously. I am not sure exactly what I was thinking on that whole issue, but your post was excellent and informative. I need to learn more about the sticky bit and the unmask, but your post has solved my immediate problem.

Wordpress has 90% functionality, but I think that is because I restricted the www-data's ownership exclusively to the wp-content folder and that is fine for me now that I have the ftp working.

Hi Don

Group-inheritence in my opinion is a necessity for any shared directories.  You can also do it with the bsdgroups mount option.  In BSD, group inheritence was the normal way; Linux modelled this on the System V behaviour, which gives you groups from the current process.  But as very, very, few people are know how to manipulate the primary group of the current process, what happens is they get a group they don't know how to control.  Most people understand the idea of public directories, however, and expect things to be shared there.

In general, if you find yourself using chmod and chown, it means your groups, umask, and permissions are probably not set up correctly.  When done correctly, every file gets a sensible set of permissions.  I wrote [http://ubuntuforums.org/showpost.php?p=11884837&postcount=9](http://ubuntuforums.org/showpost.php?p=11884837&postcount=9) recently, which perhaps has material which would interest you if you're new to umask and permissions and so on.

Thanks for kind words.

Regards
Jonathan.

---

### Post by laughing-boy on 2012-05-30
Thanks for the really useful article. I found that

```
chmod g+t
```didn't work on my server, but needed to use the group sticky bit instead:

```
chmod g+s
```- Thanks again.

---

### Post by bab1 on 2012-05-30
> **laughing-boy said:**
> Thanks for the really useful article. I found that

```
chmod g+t
```didn't work on my server,
The sticky bit (as currently used) restricts file deletion if the user is NOT in the same group (and others(o) have rwx).  This is set on directories only.> 

 but needed to use the group sticky bit instead:

```
chmod g+s
```- Thanks again.
This is not a sticky bit.  It's a sgid (set group ID) bit.  See [**_[COLOR="Blue"]here[/COLOR]_**]("http://www.zzee.com/solutions/unix-permissions.shtml#setuid").

---

### Post by Morbius1 on 2012-05-30
> **laughing-boy said:**
> Thanks for the really useful article. I found that

```
chmod g+t
```didn't work on my server...
I believe that's because of a typo in the other post:
> **Jonathan L said:**
> Group sticky (chmod g+t file) is essential  for shared work: [COLOR=Blue]it means that any file created in that directory will  inherit the group from that directory.[/COLOR]  Subdirectories also inherit  group-sticky on creation. 
I've never heard it referred to as a "group sticky" before but if you read the description that follows it describes "chmod g+s". There is no such thing as a "chmod g+t" to my knowledge.

The term "sticky" refers to a directory where a file may only be removed or renamed by a user if the user has write permission for the directory and the user is the owner of the file, the owner of the directory, or root. I don't know of a corresponding sticky feature applied to groups. Maybe in BSD?

---

