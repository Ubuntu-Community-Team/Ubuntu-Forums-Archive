---
title: "User level for web and mail server"
date: 2019-01-10
forum: Server Platforms
---

### Post by evadave2 on 2019-01-10
Hello all.

Long time viewer, first time poster. I am addicted to Linux and continuing to learn.  I am self-taught and have learned all I know from various sources.  I have taken the time to learn and understand command and arguments and I do not just copy and paste from my sources.

I am looking for advice on my current setup.  I have an even year old computer with Ubuntu Server 18.04.  Multiple hosted sites in "/var/www" and want to create a mail server. The setup works fine at the moment and I do not want to make too many changes unless there is a performance or security issue, so my main questions are


[LIST]
[*]Pros and cons of moving site from "/var/www" to user level.
[*]If favorable to move web server to user level would the premise be the same for a mail server?
[/LIST]

I know I seem long winded and all over the place but I do have a method to my madness and like to bounce off others.  I am not looking for absolute answers, just direction. Thank you in advance to all that reply.

---

### Post by QIII on 2019-01-10
Hello!

Can you clarify what you mean by "user level"?  /var/www is the typical place for your directories.  What makes you think you need to move them?

---

### Post by evadave2 on 2019-01-10
I am looking at moving to /home/[COLOR=#ff0000]user[/COLOR]/www.  I was thinking about putting web server on one user and mail server on another user if there are benefits. 

One thing I did leave out, I partitioned my drive so /home is on a separate partiton to the rest of the OS.

---

### Post by QIII on 2019-01-10
Why were you thinking of doing that? Did you read that somewhere?  Do you really want to expose anything in your /home to the world?

Not so long ago, all web server stuff went in /srv .  That evolved over time and /var/www became a well-accepted norm.  There are some distros that have gone to /var/www/html.  There are still old-school purists who sniff at anyone who puts anything outside of the /srv   directory.

Your /home?  I wouldn't.  Your user account should not be the one that owns those processes/directories/permissions.

By the way, a separate /home partition is generally considered advisable in any case.

You can put your directories anywhere you want if you take the time to set up all your config files and you want the extra headache of administering that.

You'd want to create at least one symlink, name it www, in /var pointing to the directory where you plan to have it.

---

### Post by evadave2 on 2019-01-10
I understand the concern you raise with the /home folder.  Going to backup the drive and go with the norm for now then experiment another time.  

Thanks for the info QIII.

---

### Post by slickymaster on 2019-01-10
*Thread moved to **Server Platforms**.*

---

### Post by The Cog on 2019-01-10
I would discourage moving your www stuff away from /var/www - I can't think of a good reason to move it. Notice that /var/www is probably already owned by a user account such as apache2 or nginx (I forget the actual name) and thiat user is not normally allowed an actual login - it's an account id reserved for the web server process.

Similarly, if you install mail server, it will probably have its own user account name and its own data folder that is already restricted to that account. Other people who understand Linux better than I do have already thought about these issues, and I would need good reason before I meddled with their solution.

That said, if you do have a good reason, don't let me stop you. But do consider the existing security configuration and the effects your change would have.

---

### Post by mastablasta on 2019-01-10
i would guess that the issue here is that /var/www is on / partition while /home is on separate one. chances are that / was created quite small compared to /home. however, this possible lack of space could be solved for example by new partition and then a symbolic link. 

for example is have server on a USB key. if it breaks it is cheap to replace :) but all the data is on separate hard disks. USB stick has relatively low space (16GB in total), so if i started adding websites and email server for multiple users, i would quickly run out of space. 

i believe the Op might have stumbled into a similar issue here = lack of space on / partition where /var is.

---

### Post by SeijiSensei on 2019-01-10
If the issue is permissions, you can add yourself to the www-data group, then run "sudo chmod g+w /var/www".

I manage a public web server where I have a single user that owns all the websites.  They all reside under /home/username/sites.  That user has no other purpose on my server.  The Apache user ("www-data" on Debian/Ubuntu) has limited read permissions to the files in that directory.

You absolutely do not want to fiddle with ownerships and permissions for any mail server.  Programs like Postfix and sendmail are configured to run in a secure manner when installed.  If you need to look at something, use the "sudo" facility to become the administrative ("root") user.  Unless you really know what you are doing I wouldn't change anything.

---

