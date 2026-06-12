---
title: "Can't Post Files to /var/www using Filezilla via SFTP on 14.04"
date: 2014-08-26
forum: Server Platforms
---

### Post by Chris of Arabia on 2014-08-26
A bit of background first. I have had this server running and posting files into /var/www before, but it doesn't seem to have taken kindly to the upgrade to 14.04 I did a short while back. It's sitting on a home network and has no public facing presentation. It's not intended to be set up for multiple users, I just need it to behave as if I was posting to my ISP, I guess as a development/pre-production environment. BTW I know 14.04 moved the public apache2 directory to /var/www/html, but assuming I can get it working to /var/www, I can apply the same principles to the new folder.

The server is running openssh-server, and I can connect via an SFTP session in Filezilla to the server without a problem, and navigate the file structure as I need to. What it won't allow me to do though, is post files into /var/www. I get the message back

> [SIZE=2]Error:	/var/www/config_inc.php: open for write: permission denied
Error:	File transfer failed[/SIZE]

For the purposes of trying to get it working, I ran the following instructions inside PuTTY

> sudo useradd webby
sudo passwd webby

sudo usermod  -g www-data webby
sudo chmod -R g+w /var/www

Now in theory, that should have created my new user 'webby', given it a password, added it to the group www-data, and then given the members of the www-data group the permission to write files. But seemingly not. Neither my new user nor my admin account 'chris', both of which are members of www-data, can write into /var/www.

I know I'm missing something, but what?

---

### Post by TheFu on 2014-08-26
What does ```

ls -al /var/www 
```
show?  Sounds like a trivial file/directory permissions problem.  If you don't understand those - time to learn. There is a nice Linux file/directory permissions tutorial here: [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
Don't just read it - type everything in and follow along. DO NOT COPY/PASTE!!!!  Type it.

---

### Post by Chris of Arabia on 2014-08-27
This is what's it's show using the  -al and -la modifiers for the ls command (I've always used the latter previously)
```
[EMAIL="chris@PIGLET2:~$"]chris@PIGLET2:~$[/EMAIL] ls -al /var/www
total 20
drwxrwxr-x  3 root root 4096 May 30 23:56 .
drwxr-xr-x 15 root root 4096 Dec 17  2013 ..
drwxrwxr-x  2 root root 4096 Aug 14 18:44 html
-rw-rw-r--  1 root root  177 Dec 14  2013 index.html
-rw-rw-r--  1 root root   66 Jan 10  2014 phpinfo.php

[EMAIL="chris@PIGLET2:~$"]chris@PIGLET2:~$[/EMAIL] ls -la /var/www
total 20
drwxrwxr-x  3 root root 4096 May 30 23:56 .
drwxr-xr-x 15 root root 4096 Dec 17  2013 ..
drwxrwxr-x  2 root root 4096 Aug 14 18:44 html
-rw-rw-r--  1 root root  177 Dec 14  2013 index.html
-rw-rw-r--  1 root root   66 Jan 10  2014 phpinfo.php

```

Tutorial next...

---

### Post by TheFu on 2014-08-27
As suspected, the cause of the issue is a trivial permissions. They are wrong for what you want to accomplish.

                             So I'm torn.

Should I just provide the answer when it is clear you will be hacked in 20 seconds or should I spend the extra time to guide you to the answer, knowing you have a huge learning curve to get to a point were running a web service it safe - especially if using php?

When I was learning this stuff - a question like this would have been answered with 4 letters - "RTFM" - that isn't acceptable on these forums.  You have all the commands necessary already - it is just the options and what each means that seems to be lacking.

man chmod
man chown
man sudo 
Start reading.  Linux is a multi-user OS - so files access rights are controlled by userid and groupid. Hopefully when you return, the tutorial completed, it will be clear what you've done wrong.  

BTW - the order of options to **ls** doesn't matter.  **man ls** will explain.

Happy learning!  Oh - and please, please, please do not put this system on the internet without a bunch more security knowledge. The internet is a dangerous place. I've added links in my signature to get started.  Just because something works, that doesn't mean it is secured.

---

### Post by nerdtron on 2014-08-27
```
sudo usermod  -g www-data webby
sudo chmod -R g+w /var/www
```

You are correct here but there is something missing. The /var/www is not owned by www-data so even if user webby is a member of www-data he is still won't be able to write on /var/www.
From here, you see that the owner is root.
```
chris@PIGLET2:~$ ls -la /var/www
total 20
drwxrwxr-x  3 root root 4096 May 30 23:56 .
drwxr-xr-x 15 root root 4096 Dec 17  2013 ..
drwxrwxr-x  2 root root 4096 Aug 14 18:44 html
-rw-rw-r--  1 root root  177 Dec 14  2013 index.html
-rw-rw-r--  1 root root   66 Jan 10  2014 phpinfo.php
```
A solution to this is to change the ownership of the /var/www folder to www-data instead of root.
```
sudo chown -R www-data:www-data /var/www
```

Then post the output of "ls -al" to see the changes. Then try writing to the directory using the user webby.

---

### Post by TheFu on 2014-08-27
Don't forget to force directory permissions to stick with the desired group, www-data, not the current primary group whatever that is for the userid logged in.

```
find /var/www -type d -exec sudo chmod g+rwxs {} \;
```

---

### Post by Chris of Arabia on 2014-08-28
Thanks for the updates. Whilst I've not got back to this (life is busy), I have been reading; notably these two responses from askubuntu.com
[INDENT][http://askubuntu.com/questions/46331/how-to-avoid-using-sudo-when-working-in-var-www](http://askubuntu.com/questions/46331/how-to-avoid-using-sudo-when-working-in-var-www)

[http://askubuntu.com/questions/20105/why-shouldnt-var-www-have-chmod-777](http://askubuntu.com/questions/20105/why-shouldnt-var-www-have-chmod-777)
[/INDENT]
I've found those more useful than the link TheFu posted on file permissions - it's good at explaining how to change things, but not so much on how to apply them in any given circumstance, specifically my FTP issue. However, I think I rapidly concluded that ownership of /var/www was probably an issue, but what I wasn't clear on was what would be considered 'best practice' on which user:group should own it, given what I was trying to achieve, and then what the most sensible level of permission those should have. I'm well aware that I've more learning to do, but it's now beginning to come clearer to me. The new information above will help in that, I have no doubt.

Rest assured, I have no intention of ever putting this or any other server on the internet; I'll leave that to the professionals, this is just a sand pit for my own amusement, and dare I say it, education...

---

### Post by TheFu on 2014-08-28
So ... apache runs as the "www-data" user under the www-data group.  The best practice would be for all files accessed by apache to use those and have minimal other permissions.

It is often very convenient to place your userid into the www-data group as well, then allow the group to have r, w, and create permissions in those directories too.

so - ```

sudo chown -R www-data.www-data /var/www
find /var/www -type d -exec sudo chmod g+rwxs {} \;
```
should get everything setup properly.  Then just add your userid to the /etc/group file. No need for any command - **sudo vi /etc/group** and change the line with www-data - append you userid to the end.  Logout, login and type **id** to see the change.  Or use **newgrp** to change if logout is inconvenient.

Until you did that prior reading, you may not have been ready for that information.

Then the next issue if FTP.  Using FTP is clearly NOT a best practice.  sftp/ssh/scp ARE. These are very different tools than FTP, so being accurate is important.

Learning the "why" is very hard over forums. The one-on-one in-person interaction is the best way I know to learn that stuff.  Finding a LUG is normally what I recommend.  Local Universities often host a LUG.

---

### Post by Chris of Arabia on 2014-08-28
OK. All steps described above have been completed, and I can now post files again, and they retain the www-data group as they're uploaded. I will be reading more though...

---

### Post by nerdtron on 2014-08-28
Settings permissions of the /var/www folder and its contents to 777 is a BIG NO. Put simply, this means ANYBODY can READ and WRITE on this directory which is kind of self explanatory.

The correct practice would be restricting the WRITE permissions to only the www-data (apache) and its group (the user you created). Then READ permission is allowed to everybody. A good way to achieve this is to add your user to the group of apache and add write permissions on the group. 
The Fu' suggestion is also a good way to achieve this.

---

### Post by cj13579 on 2014-08-28
> **TheFu said:**
> The best practice would be for all files accessed by apache to use those and have minimal other permissions.

I have my site code under my username and group (Chris:Chris) with only read permission to other. In the past I found that if files and folders were owned or write able by the www-data user then they were susceptible to hacks. This was especially true for 2.x versions of Wordpress.

---

### Post by Chris of Arabia on 2014-08-30
> **cj13579 said:**
> I have my site code under my username and group (Chris:Chris) with only read permission to other. In the past I found that if files and folders were owned or write able by the www-data user then they were susceptible to hacks. This was especially true for 2.x versions of Wordpress.

I saw this kind of quote several times whilst I was searching for answers, and was probably the primary reason for me not changing the ownership on /var/www earlier - I just wasn't convinced I should be doing it. It seems odd that Linux should be so prevalent as the underpinning architecture for the internet, yet a clean answer to a basic question around (S)FTP is seemingly so vague. For me, it doesn't matter, as it's only ever going to be a home box, but I wonder how many who are putting things on the net, are insecure as a result.

As for the LUG idea, as much as I'd like to give one a try, Riyadh may not be as easy to find one as some other places; no harm in looking though.

---

### Post by TheFu on 2014-08-30
Why no clear, exact answer?
Your box is different.
There are people on shared hosting, shared VMs, running SELinux, running AppArmor, on military networks, or just running it as a hobby.  Sometimes there are government laws that require certain settings.  Until now, we didn't know where in the world you were and, until yesterday, that the box was for home use.  

Running a webapp is different from running a static website.  My recommendations are very different for that - I run the app under a different userid, usually on a non-internet connected system, then use a reverse proxy with nginx on the main front-door machine to redirect in/out traffic as needed to the specific port on the specific machine.  Things get complicated quickly.

Securing php webapps is hard. I don't try. Much easier just to never use php.

Oh - and storage for a static website is NFS mounted as read-only. That way, if an attacker gets onto the system, he can't change any of the files.

Backups - lots-o-backups. 60 days - sometimes 120 days.  There are many attacks where having a backup from 3 weeks ago is the only solution. Humans don't always notice when a system is compromised quickly. 2-4 days can easily go by before it is noticed.  Some people (I include myself in this group), may not notice an issue on a machine for 3-6 weeks if it isn't a primary system or used daily.  Hence the need for more backups.  All the backups here are automatic, daily, and not just about data, but permissions, settings, something that can be restored in 30-50 minutes.  Good system backups is the #1 security technique.

There is no question about using FTP - don't.

I can't speak for others, but I'm not here to tell people what to type into a window. I'm hear to teach how to find answers, since everyone has slightly different questions.  When there is a clear answer - I say it.  Don't use FTP, use sftp.  That is clear.

Most cities with a name that I've heard seem to have a LUG.  Riyadh has/had at least 1 LUG according to google, but I don't read Arabic.  I'm a member in 3 different LUGs in my metro area and there are 5 within driving distance.  Most meet at universities here (GA Tech, Emory, SPSU, Kennasaw), but one meets at "Harry's Pizza" - yum.

---

### Post by Chris of Arabia on 2014-08-30
Whilst I'm partial to a slice of pizza, no amount of pepperoni is going to get me over the Arabic language hump - not even if I stay here another 15 years... ](*,)

As for it being a home box, that was in my first post ;)

I'm learning though, and thanks for the help

---

### Post by Craig_Thomas on 2015-08-22
I get TheFU's point that every system is different but really I am pretty sure I am not alone in setting up a Ubuntu/Linux box as a web server for the purpose of web development.
In my time, (several years on and off) I have read a massive amount of contradictory, lazy or downright bad advice about this subject.

From my recent reading session I have heard it is a bad idea to add your user to the www-data group and give that permissions on the /var/www folder.
Unfortunately I still do not have a definitive answer.

I am currently looking at following the example here:
[http://wiki.apache.org/httpd/FileSystemPermissions](http://wiki.apache.org/httpd/FileSystemPermissions)
I will try and report back soon on it's success.

Craig

-- Hoping we are not alone --

That didn't go well:
> [h=1]Forbidden[/h] You don't have permission to access / on this server.



A quick restart fixed the issue.  I guess probably restarting apache might have worked too.

---

### Post by TheFu on 2015-08-22
> **Craig_Thomas said:**
> That didn't go well:

Dude - [necroposting]("http://www.urbandictionary.com/define.php?term=necroposting") is bad.  Please start your own thread for your issue.

---

### Post by Muhammad_Omais on 2016-03-07
**find /var/www -type d -exec sudo chmod g+rwxs {} \;**

This code helped me, thanks for sharing, can you please exactly explain in detail what this line exactly mean. I have never worked with linux just configuring my vps server and i was stuck with the permissions as i was not able to give the permission to the users i created other then the home directory of the user. I would appreciate if you can guide me for a good link which can help in understanding these commands and other commands in details.

What i understood from this line is 
find www folder in var 
what **-type d** mean
-exec chmod command as sudo 
what **g+rwxs {} \;** mean

---

### Post by nerdtron on 2016-03-08
> **Muhammad_Omais said:**
> **find /var/www -type d -exec sudo chmod g+rwxs {} \;**

This code helped me, thanks for sharing, can you please exactly explain in detail what this line exactly mean. I have never worked with linux just configuring my vps server and i was stuck with the permissions as i was not able to give the permission to the users i created other then the home directory of the user. I would appreciate if you can guide me for a good link which can help in understanding these commands and other commands in details.

What i understood from this line is 
find www folder in var 
what **-type d** mean
-exec chmod command as sudo 
what **g+rwxs {} \;** mean

That command means:
-> Find all files inside the /var/www/* folder
-> -type d means "only list Directory names" (folder names only, do not find normal files)
-> -exec means to execute the following command
-> sudo chmod g+rwxs 
sudo to execute the command as root
chmod change the permissions of file/folder
g+rwxs the permissions you want add. meaning all group members will have Read, Write and eXecute permissions, and SetGID bit is set
-> {} \;   -- each find resullt will execute to the  {} as arguments this is a syntax needed find -exec command.

---

