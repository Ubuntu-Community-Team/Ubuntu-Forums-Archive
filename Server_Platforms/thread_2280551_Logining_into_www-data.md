---
title: "Logining into www-data"
date: 2015-05-31
forum: Server Platforms
---

### Post by wolfgentleman on 2015-05-31
[CENTER][SIZE=5][B][COLOR=#ff0000]WARNING:
[I]THIS IS POTENTIALLY INSECURE
&
SHOULD NOT BE DONE IN MOST CIRCUMSTANCES[/I][/COLOR][/B][/SIZE][/CENTER]

In this how-to I will provide a one-time version and a shorter over time version. For the latter one, I assume you know how to use chmod.

[SIZE=5]**One-Time**[/SIZE]
```

$ su
Password: 
# su -s /bin/bash www-data

```
Congrats, you're now logged in as www-data!

[SIZE=5]**Regular Basis**[/SIZE]
Create 2 files & make them executable:
[LIST=1]
[*]/usr/sbin/to-www
[*]/usr/bin/auto-www
[/LIST]
Contents of /usr/sbin/to-www:
```

#!/bin/sh
su -s /bin/bash www-data

```
Contents of /usr/bin/auto-www:
```

#!/bin/sh
su -s '/usr/sbin/to-www'

```
To log in as www-data from a regular user, just run 'auto-www' and input the root password. For a sudoer, you can run 'sudo to-www' or 'auto-www'

[SIZE=5]**But why would you want that?**[/SIZE]
For me it was the fact that I host multiple sites and they are managed by the perspective people and some scripts refuse to work with ownership of user:www-data * cough cough drupal cough cough * thus not allowing one user per site. However I did not want to open www-data to SSH and I wanted the individual users to start in their site's directory. So I did this and set their shell to /usr/bin/auto-www, gave them the root password, and added the -p option to both files.
*Note: What I did it is not viable unless you trust your users like I do.*

---

### Post by bab1 on 2015-05-31
> **wolfgentleman said:**
> [CENTER][SIZE=5][B][COLOR=#ff0000]WARNING:
[I]THIS IS POTENTIALLY INSECURE
&
SHOULD NOT BE DONE IN MOST CIRCUMSTANCES[/I][/COLOR][/B][/SIZE][/CENTER]


In this how-to I will provide a one-time version and a shorter over time version. For the latter one, I assume you know how to use chmod.

[SIZE=5]**One-Time**[/SIZE]
```

$ su
Password: 
# su www-data

```
Congrats, you're now logged in as www-data!

By default the user www-data has no login```
www-data:x:33:33:www-data:/var/www:[COLOR="#FF0000"]**/usr/sbin/nologin**[/COLOR]
```
This is what you get with your command```
su www-data
Password: 
su: Authentication failure

```
If you try it as root you get```
sudo su www-data
[sudo] password for bab: 
This account is currently not available.

```
So you hacked the account leaving it insecure.  There is no need to do that.
> 

[SIZE=5]**Regular Basis**[/SIZE]
Create 2 files & make them executable:
[LIST=1]
[*]/usr/sbin/to-www
[*]/usr/bin/auto-www
[/LIST]
Contents of /usr/sbin/to-www:
```

#!/bin/sh
su -s /bin/bash www-data

```
Contents of /usr/bin/auto-www:
```

#!/bin/sh
su -s '/usr/sbin/to-www'

```
To log in as www-data from a regular user, just run 'auto-www' and input the root password. For a sudoer, you can run 'sudo to-www' or 'auto-www'

[SIZE=5]**But why would you want that?**[/SIZE]
For me it was the fact that I host multiple sites and they are managed by the perspective people and some scripts refuse to work with ownership of user:www-data * cough cough drupal cough cough * thus not allowing one user per site. However I did not want to open www-data to SSH and I wanted the individual users to start in their site's directory. So I did this and set their shell to /usr/bin/auto-www, gave them the root password, and added the -p option to both files.
*Note: What I did it is not viable unless you trust your users like I do.*
You should figure out the correct ownership and permissions settings so that you can manage the users permissions (including the Drupal user) via user-group.  I would create a user-group (i.e. www-dev or www-content) and add all the needed users to that.  Then setup a file system that uses the user-group inheritance so that the permissions are applicable to all you users.  You do not need to leave the user www-data vulnerable as you have.  All your mortal users need is access via user-group or not depending on your trust.

Am I missing something here???

---

### Post by wolfgentleman on 2015-05-31
> **bab1 said:**
> By default the user www-data has no login```
www-data:x:33:33:www-data:/var/www:[COLOR=#FF0000]**/usr/sbin/nologin**[/COLOR]
```
This is what you get with your command```
su www-data
Password: 
su: Authentication failure

```
If you try it as root you get```
sudo su www-data
[sudo] password for bab: 
This account is currently not available.

```

I fixed that in my post. I forgot the '-s /bin/bash' on the post.
> **bab1 said:**
> So you hacked the account leaving it insecure.  There is no need to do that.

You should figure out the correct ownership and permissions settings so that you can manage the users permissions (including the Drupal user) via user-group.  I would create a user-group (i.e. www-dev or www-content) and add all the needed users to that.  Then setup a file system that uses the user-group inheritance so that the permissions are applicable to all you users.  You do not need to leave the user www-data vulnerable as you have.  All your mortal users need is access via user-group or not depending on your trust.

Am I missing something here???
I tried using the group system as a way to modify, but the scripts, by default, use user-only write. Setting the ownership to user:www-data activates the Drupal problem, but www-data:user doesn't. The users is just my (best) friend, my dad, and myself. The steps taken are Connect via SSH (user@ip-or-host) > Input User Password > Input Root Password > Use shell as www-data. I don't see any problems. What in that sequence are making www-data insecure?

[I]P.S.: I could make a cron task to fix the permissions, but that is very unappealing with the necessity of exclusions.
P.S. 2: I may set it as a sudo-based solution to remove the whole root thing from the picture, but IDK yet.[/I]

---

### Post by bab1 on 2015-05-31
> **wolfgentleman said:**
> I fixed that in my post. I forgot the '-s /bin/bash' on the post.

I tried using the group system as a way to modify, but the scripts, by default, use user-only write. Setting the ownership to user:www-data activates the Drupal problem, but www-data:user doesn't. The users is just my (best) friend, my dad, and myself. The steps taken are Connect via SSH (user@ip-or-host) > Input User Password > Input Root Password > Use shell as www-data. I don't see any problems. What in that sequence are making www-data insecure?

[I]P.S.: I could make a cron task to fix the permissions, but that is very unappealing with the necessity of exclusions.
P.S. 2: I may set it as a sudo-based solution to remove the whole root thing from the picture, but IDK yet.[/I]

The whole idea of no login is so that there should be no open shell for that user.  The *www-data* user is a system user.  The open shell is a unneeded vulnerability that can be easily avoided with proper directory ownership and permissions.  You almost had it right.  The user-group is what you need to user to control access.  My guess is you didn't set inheritance so the user-group ownership was preserved.  

Controlling the users permissions by setting the user-group ownership also eliminates all the need for scripts or cron jobs to change the permissions.  Ubuntu directories are created with 775 permissions while files have 664 permissions.  I have multiple users that always have access to the specified DocumentRoot along with the system user *www-data*.  

I don't use Drupal, but I assume that there is a *drupal* system user that can be incorporated into the scheme.  I store my data at /srv/www and I use Apache2 (v2.4).  What are the users that need to be accommodated?  Where do you store your DocumentRoot data? 

Would you like to try and set this up so that lyou don't later have to use sudo or su or scripts or cron to accomplish your goal?

---

### Post by cariboo on 2015-06-01
Changed the title, as we don't want any one to think this is a secure way of accessing files in the /var/www/html directory.

---

### Post by TheFu on 2015-06-01
What's wrong with **sudo -s -u www-data**?
This keeps your personal environment. Do not do this if you want to run any GUI programs.

**sudo -i -u www-data** won't work because www-data doesn't have a $HOME.

I've never tried this stuff before. Never needed it in 20+ yrs running UNIX/Linux servers.  Why not just add your userid to the www-data group and setup the directories where you need to drop files with **chmod 2775** permissions (group sticky)?

Or am I missing something subtle?

---

### Post by bab1 on 2015-06-01
> **TheFu said:**
> What's wrong with **sudo -s -u www-data**?
This keeps your personal environment. Do not do this if you want to run any GUI programs.

**sudo -i -u www-data** won't work because www-data doesn't have a $HOME.

I've never tried this stuff before. Never needed it in 20+ yrs running UNIX/Linux servers.  Why not just add your userid to the www-data group and setup the directories where you need to drop files with **chmod 2775** permissions (group sticky)?

Or am I missing something subtle?

That's what I was saying.   It is subtle in the sense that the Drupal  documentation is confusing.   The problem is really twofold (a) how Drupal implements it's architecture and (b) there is very little official Drupal documentation.  It is all left to the users anecdotal experiences (the Drupal wiki).

By the way, there is no group sticky.  It is known as the sgid bit.   ;-)

---

### Post by wolfgentleman on 2015-06-01
> **bab1 said:**
> The whole idea of no login is so that there should be no open shell for that user.  The *www-data* user is a system user.  The open shell is a unneeded vulnerability that can be easily avoided with proper directory ownership and permissions.  You almost had it right.  The user-group is what you need to user to control access.  My guess is you didn't set inheritance so the user-group ownership was preserved.
I still don't see how it's a vulnerability... Root/sudo users are are able to do this *without the scripts*. The scripts just make it easier and more automated. You still need a password. If you can provide *solid* proof that this is insecure, I would love to hear it. I just don't see the insecurity in this. I just don't.
> **bab1 said:**
> Controlling the users permissions by setting the user-group ownership also eliminates all the need for scripts or cron jobs to change the permissions.  Ubuntu directories are created with 775 permissions while files have 664 permissions.  I have multiple users that always have access to the specified DocumentRoot along with the system user *www-data*.
If I use 'user:www-data' it breaks Drupal's automated updates and module installs. If I use 'www-data:user' it breaks the removal of auto-installed stuff from SSH. There is not a way that *I* see to work around Drupal's stupid permission setup.
> **bab1 said:**
> I don't use Drupal, but I assume that there is a *drupal* system user that can be incorporated into the scheme.
I use stock Drupal, not the repository version. Implementing a separate user for the Drupal script is going to be a royal pain in the backside and most definitely not worth it.
> **bab1 said:**
> I store my data at /srv/www and I use Apache2 (v2.4).  What are the users that need to be accommodated?  Where do you store your DocumentRoot data?
I use the stock's parent directory, /var/www, with the addition of a sub-folder for each site.

> **bab1 said:**
> Would you like to try and set this up so that lyou don't later have to use sudo or su or scripts or cron to accomplish your goal?
[CENTER]**[SIZE=4]&#11015;[/SIZE]**[/CENTER]
> **wolfgentleman]Implementing a separate user for the Drupal script is going to be a royal pain in the backside and most definitely not worth it.[/QUOTE]
[HR][/HR]
[QUOTE=cariboo said:**
> Changed the title, as we don't want any one to think this is a secure way of accessing files in the /var/www/html directory.
What you changed it to is not very fitting to the post. would the original title with something like below at the top of the post be more acceptable?
> [SIZE=5]**[COLOR=#ff0000]THIS IS POTENTIALLY INSECURE AND SHOULD NOT BE DONE IN MOST CIRCUMSTANCES[/COLOR]**[/SIZE]
[HR][/HR]
> **TheFu said:**
> What's wrong with **sudo -s -u www-data**?
This keeps your personal environment. Do not do this if you want to run any GUI programs.
Well that's kinda what I did in the first part.
> **TheFu said:**
> **sudo -i -u www-data** won't work because www-data doesn't have a $HOME.
Actually, it does. That is unless ~ is different from $HOME, which from what I understand it isn't. When I setup a fresh Ubuntu 14.04 server and use 'apt-get install apache2' it automatically sets up the www-data user and sets /var/www as it's home.
> **TheFu said:**
> I've never tried this stuff before. Never needed it in 20+ yrs running UNIX/Linux servers.  Why not just add your userid to the www-data group and setup the directories where you need to drop files with **chmod 2775** permissions (group sticky)?
I have never dealt with the group sticky permission, so I have no idea what it is or used for. You'll have to explain what that does.

---

### Post by bab1 on 2015-06-01
> **wolfgentleman said:**
> I still don't see how it's a vulnerability... Root/sudo users are are able to do this *without the scripts*. The scripts just make it easier and more automated. You still need a password. If you can provide *solid* proof that this is insecure, I would love to hear it. I just don't see the insecurity in this. I just don't.

I thought I explained it pretty well.  Security is a mindset not a specific action.  When you are compromised you will never really know how that happened.  A security conscious system administrator never leaves an unneeded vector available for compromise.
> 
If I use 'user:www-data' it breaks Drupal's automated updates and module installs. If I use 'www-data:user' it breaks the removal of auto-installed stuff from SSH. There is not a way that *I* see to work around Drupal's stupid permission setup.

How does it "break[s] Drupal's automated updates and module installs" or "breaks the removal of auto-installed stuff from SSH"?  Just because you can't see a way doesn't mean there isn't a method.  Going back to the first response (re: insecurity), setting the ownership and permissions correctly eliminates that discussion.
> 
I use stock Drupal, not the repository version. Implementing a separate user for the Drupal script is going to be a royal pain in the backside and most definitely not worth it.

I'm not suggesting you implement a Drupal user, I'm asking if there really is one.  I suggest that you at least try what has been suggested.  It eleminates security risks and is helpful in you automating your system.
> 
I have never dealt with the group sticky permission, so I have no idea what it is or used for. You'll have to explain what that does.
This is used to preserve the group ownership when new files and directories are created.  It is a core concept when files and directories are shared by multiple users.

Once again.  I suggest you at least try what @TheFu and I have both suggested.

---

### Post by wolfgentleman on 2015-06-01
> **bab1 said:**
> I thought I explained it pretty well.  Security is a mindset not a specific action.  When you are compromised you will never really know how that happened.  A security conscious system administrator never leaves an unneeded vector available for compromise.
I don't see how it could possibly be a problem though. It's not like I enabled SSH access directly to it. You have to go through user1, user2, or user3 in order to get to www-data. It seems to me that there is no difference if you have extreme trust in your users.
> **bab1 said:**
> How does it "break[s] Drupal's automated updates and module installs"
Drupal's check for "can I write" consists of an "if i_am_owner && is_owner_writable" of which it runs as www-data, thanks to Apache being the calling process.
> **bab1 said:**
> "breaks the removal of auto-installed stuff from SSH"?
I meant modification, not removal. My bad on that, but Drupal creates/downloads/extracts as 755 for directories and 644 for files. Thus, if the user is not www-data it cannot modify auto-installed files & directories.
> **bab1 said:**
> Just because you can't see a way doesn't mean there isn't a method.
That's why I said *"I don't see"* rather than *"there isn't"*. I can guarantee there is a way, it's just not obvious to me.
> **bab1 said:**
> I'm not suggesting you implement a Drupal user, I'm asking if there really is one.  I suggest that you at least try what has been suggested.  It eleminates security risks and is helpful in you automating your system.
No, there isn't. If the one in the repo is like some of the other web scripts, then I could snag it from the repo and there would be. And even if there was, I would be having the same discussion, but with the the Drupal user rather than the www-data user. I would rather not go through the pain of making Apache run as multiple users and even if I did, how would I set Apache to use a password protected user?
> **bab1 said:**
> This is used to preserve the group ownership when new files and directories are created.  It is a core concept when files and directories are shared by multiple users.
Hmm... Would it be able to preserve group write?


*P.S.: I'm going to go ahead and revert the title change and add the big red warning to the top. If you don't like it you can change it back.*

---

### Post by bab1 on 2015-06-01
> **wolfgentleman said:**
>  Drupal's check for "can I write" consists of an "if i_am_owner && is_owner_writable" of which it runs as www-data, thanks to Apache being the calling process.

Have you see this code yourself?  Can you direct me to this code.
> 

I meant modification, not removal. My bad on that, but Drupal creates/downloads/extracts as 755 for directories and 644 for files. Thus, if the user is not www-data it cannot modify auto-installed files & directories.

The default umask (002) supplied permissions are 775 = directory and 664 = files.  In the reading I have done I don't see where Drupal alters that.  I'm sure the repo version of Drupal works like that.  Have you altered the configuration specifications?
> 

That's why I said *"I don't see"* rather than *"there isn't"*. I can guarantee there is a way, it's just not obvious to me.

No, there isn't. If the one in the repo is like some of the other web scripts, then I could snag it from the repo and there would be. And even if there was, I would be having the same discussion, but with the the Drupal user rather than the www-data user. I would rather not go through the pain of making Apache run as multiple users and even if I did, how would I set Apache to use a password protected user?


You seem fixated on "the drupal user"  I never said you should use a drupal (system) user.  Maybe you are confused with the notion of a mortal *_user of Drupal_*.> 

Hmm... Would it be able to preserve group write?
The permissions are not set by sgid.  They are set by the last use of umask.  As I said the default umask is 002 which already has group rw, but there is no reason why a script can't reset the umask to 022 (755/664).  If Drupal has a script that resets the umask you can always set it back or install the repo version which has already worked out these problems.  

What is the umask on the machine you are using?  Post the output of ```
umask
```

What version of Ubuntu are you using?  Post the output of this```
lsb_release -a
```

[COLOR="#0000FF"]Edit:  It appears you can set the Drupal umask settings with this file: ***sites/default/settings.php***     What does it say in there?[/COLOR]

---

### Post by TheFu on 2015-06-01
Set Group ID - setguid - commonly known as the "group sticky bit" is a basic UNIX file system permission. I showed the octal setting, but most of hte time it is seen as **chmod g+s**.  
To learn about it, nothing will replace making a few users, putting them into a few different and same groups and playing around with the user and group permissions for an hour to see the subtle permission changes possible. It has been this way for 40 yrs and needs to be well understood by system admins and anyone who deploys a web-app that is internet facing.

I only posted for sudo and chmod knowledge. Cannot pretend to understand what is in the mind of any other person or F/LOSS project team.

**umask** is userid specific. It is common to override in the ~/.profile or ~/.bashrc.

---

### Post by wolfgentleman on 2015-06-02
> **bab1 said:**
> Have you see this code yourself?  Can you direct me to this code.
I have not poked through the code, but by process of elimination the it can only be satisfied by being the owner.

> **bab1 said:**
> The default umask (002) supplied permissions are 775 = directory and 664 = files.  In the reading I have done I don't see where Drupal alters that.  I'm sure the repo version of Drupal works like that.  Have you altered the configuration specifications?
IDK, but when I use the auto-install it is set as a owner-only write.

> **bab1 said:**
> You seem fixated on "the drupal user"  I never said you should use a drupal (system) user.  Maybe you are confused with the notion of a mortal *_user of Drupal_*.
Ah. So you were referring to making the user that uses Drupal to have Apache run as them for their directory?

> **bab1 said:**
> What version of Ubuntu are you using?  Post the output of this```
lsb_release -a
```
```
No LSB modules are available.Distributor ID: Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:        14.04
Codename:       trusty
```

> **bab1 said:**
> [COLOR=#0000FF]Edit:  It appears you can set the Drupal umask settings with this file: ***sites/default/settings.php***     What does it say in there?[/COLOR]
I can't find it with a search. I'll look for it further when I'm in a better mood. I feel like all I've been doing is arguing about or fixing something today.

---

### Post by SeijiSensei on 2015-06-02
Having just migrated a Drupal site, I'll toss in my two cents.

I created a user to own the Drupal tree, let's call it "drupal".  I unpacked the Drupal tar.gz file in that directory and created a symlink called "current" pointing to that directory.  As the drupal user I ran:
```

$ cd /home/drupal
$ ln -s drupal-7.37 current

```

I then added the Apache user, "www-data" on Ubuntu, to the "drupal" group in /etc/group.

Finally I made the entire /home/drupal/drupal-7.37 tree read-only to user and group with no permissions for other.  I added group-writable privileges to drupal-7.37/sites/default/files, where user file uploads like graphics are stored.

You'll also need to create a couple of group-writable directories to handle module updates.

See these documents:
[https://www.drupal.org/node/244924](https://www.drupal.org/node/244924)
[http://drupal.stackexchange.com/questions/30113/configuring-the-temporary-directory](http://drupal.stackexchange.com/questions/30113/configuring-the-temporary-directory)

The webserver uses /home/drupal/current as its DocumentRoot for the site.

---

### Post by wolfgentleman on 2015-06-02
I had a thought that *may* satiate y'all's problem with the system "vulnerability" that loggin in with www-data created. Even though I don't see how it is insecure in any form.
Requirements:
[LIST=1]
[*]2 users per site:
[LIST=1]
[*]User 1
[LIST=1]
[*]Password: Yes
[*]SSH Login: Enabled
[*]Shell: Script that su's into User 2
[/LIST]

[*]User 2
[LIST=1]
[*]Password: No
[*]SSH Login: Disabled
[*]Shell: /bin/bash
[/LIST]
[/LIST]

[*]Apache MPM setup like [this tutorial]("https://www.howtoforge.com/running-vhosts-under-separate-uids-gids-with-apache2-mpm-itk-on-ubuntu-9.04")
[/LIST]

But then again, this is basically what I am currently doing, except each user is isolated to their own directory. Just some thoughts.

---

### Post by TheFu on 2015-06-02
If you are using passwords for remote connectivity, then you have already failed on the security-side.
I don't see why a 2nd user is desired, but I haven't been following this very closely.

---

### Post by wolfgentleman on 2015-06-02
> **TheFu said:**
> If you are using passwords for remote connectivity, then you have already failed on the security-side.
Yeah, I have been meaning to move to SSH keys instead. So consider the "password" either a password or an SSH key.
> **TheFu said:**
> I don't see why a 2nd user is desired, but I haven't been following this very closely.
So it can be used by Apache's MPM module. It may not be required, I didn't look very deep into making Apache run as multiple users.

---

### Post by TheFu on 2015-06-03
I'd probably just use LXC if I wanted apache compartmentalized beyond what AppArmor can do.

---

### Post by wolfgentleman on 2015-06-03
> **TheFu said:**
> I'd probably just use LXC if I wanted apache compartmentalized beyond what AppArmor can do.
I had to look both of those up...
[LIST=1]
[*]I found the Ubuntu page on AppArmor, but I couldn't get the gist of what it was by skimming. I'll read more later when I'm not so busy.
[*]Correct me if I my Google Foo failed me, but LXC is like a CPanel?
[/LIST]

---

### Post by SeijiSensei on 2015-06-04
> **SeijiSensei said:**
> You'll also need to create a couple of group-writable directories to handle module updates.
Well, Drupal seems even more complicated than I first imagined.

When you update modules in Drupal, you have to have a working account with an FTP or SSH login.  So that means the "drupal" user I discussed above needs a password.  That user also needs to own sites/all/modules and have write privileges there.

I'm guessing all this complexity is required to work in hosted environments, but if you control the whole server like I do, it's a royal pain in the ....

---

### Post by wolfgentleman on 2015-06-04
> **SeijiSensei said:**
> When you update modules in Drupal, you have to have a working account with an FTP or SSH login.  So that means the "drupal" user I discussed above needs a password.  That user also needs to own sites/all/modules and have write privileges there.
You don't need FTP if the directories are owned by Drupal's calling user, 'www-data' in my case. I hate FTP, and would rather the "vulnerability" of logging in as www-data, of which I still don't see it as a vulnerability as the method I show just automates the process that is already doable.

Let's just say, for the moment, logging into www-data is a vulnerability. A sudoer or root can do it *without* my scripts. That means I am not *creating* a vulnerability, I'm *activating* one. That means the system I'm using is *no more vulnerable than a stock system*! So please, tell me how it is wrong to post a how-to that can be done with minimal knowledge. It's as simple as piecing together multiple sources, modifying to work as wanted. It will be achieved one way or another. Where there is a will, there is a way.

*P.S.: @TheFu - I am probably going to move to a CPanel-like system on my other system, using the bigger one for a game servers and my TeamSpeak server.*

---

### Post by bab1 on 2015-06-04
> **wolfgentleman said:**
> You don't need FTP if the directories are owned by Drupal's calling user, 'www-data' in my case. I hate FTP, and would rather the "vulnerability" of logging in as www-data, of which I still don't see it as a vulnerability as the method I show just automates the process that is already doable.

Let's just say, for the moment, logging into www-data is a vulnerability. A sudoer or root can do it *without* my scripts. That means I am not ***creating*** a vulnerability, I'm ***activating*** one. That means the system I'm using is ***no more vulnerable than a stock system***! So please, tell me how it is wrong to post a how-to that can be done with minimal knowledge. It's as simple as piecing together multiple sources, modifying to work as wanted. It will be achieved one way or another. Where there is a will, there is a way.
There are lots of vulnerabilities in Linux if you expose them.  The system is not perfect or even safe at all times.  Just because you *can* do something does not mean the you **should** do it. You are not logging in as a system user.  You are opening a shell for that user which is now available for an attacker.  You never know what might happen.  That shell could remain open when you walk away or otherwise get distracted.  In fact that is why sudo was created.  Too many users with root access meant that there is a possibility of a root shell becoming left open and then becoming a hijacked shell.  So "piecing together multiple sources, modifying to work as wanted. It will be achieved one way or another. Where there is a will, there is a way" is not necessarily the right thing to do; and certainly not something that should be promoted without careful analysis of the consequences. 

My point is that you do not have to do any of what you propose.  If you setup the permissions correctly for the file system branch that you are using for your DocumentRoot you won't have any of the problems you are trying to overcome.

---

### Post by wolfgentleman on 2015-06-05
> **bab1 said:**
> Just because you *can* do something does not mean the you **should** do it.
No, but that doesn't stop anyone. But I do agree there.
> **bab1 said:**
> You are not logging in as a system user.  You are opening a shell for that user which is now available for an attacker.
I'm logging in as a regular user and immediately su'ing into the system user to modify the files owned by it.
> **bab1 said:**
> certainly not something that should be promoted without careful analysis of the consequences.
I'm not promoting it per-se. I'm just saying "this is what I did" and it's the simplest option that worked for me.
> **bab1 said:**
> My point is that you do not have to do any of what you propose.
No, there are other ways of doing it.
> **bab1 said:**
> If you setup the permissions correctly for the file system branch that you are using for your DocumentRoot you won't have any of the problems you are trying to overcome.
First problem with just using permissions to "fix" things, is script's ways of checking if it can modify. Second problem is when trying to fix the first, it breaks user modifiablity. The other options are to modify the script or use complicated Apache configs for running under multiple users along with the same deal as with the www-data system I currently use.

---

### Post by bab1 on 2015-06-05
> **wolfgentleman said:**
> First problem with just using permissions to "fix" things, is script's ways of checking if it can modify. Second problem is when trying to fix the first, it breaks user modifiablity. The other options are to modify the script or use complicated Apache configs for running under multiple users along with the same deal as with the www-data system I currently use.
Setting the permissions on a file system is not "a fix".  There are correct ways of setting the permissions given the circumstances and others not so.  

You don't know what you don't know.  Not once have you said "how do you do that?".  You will never know If what I say works as long as you are not willing to try.  I say it will work and I am willing to try and possibly be proven wrong.

---

### Post by wolfgentleman on 2015-06-05
The users I created, before the www-data setup, for the web portion are setup like this:
```

useradd -b /var/www -g www-data -m -N -s /bin/bash $user
passwd $user
chmod -R ug=rwX,o=r /var/www/$user

```
$user being the username to be created. On the root account I added a cron job that ran a little script that ran chmod on all of the users setup like this based on the directories in /var/www. It worked beautifully. Then came Drupal. It wanted FTP access because it's calling user (www-data) was not the owner of the directory tree. I wouldn't have begun this journey to using www-data as the after-login user if it provided **S**FTP as a method. The check is absolutely retarded, but nonetheless I could not find a solution that was more simple than logging in as www-data via a SSH accessible user. In the end, I end up starting a migration to a CPanel-like system on my other VPS and moving the sites to that VPS.

---

### Post by bab1 on 2015-06-05
> **wolfgentleman said:**
> The users I created, before the www-data setup, for the web portion are setup like this:
```

useradd -b /var/www -g www-data -m -N -s /bin/bash $user
passwd $user
chmod -R ug=rwX,o=r /var/www/$user

```
$user being the username to be created. On the root account I added a cron job that ran a little script that ran chmod on all of the users setup like this based on the directories in /var/www. It worked beautifully. Then came Drupal. It wanted FTP access because it's calling user (www-data) was not the owner of the directory tree. I wouldn't have begun this journey to using www-data as the after-login user if it provided **S**FTP as a method. The check is absolutely retarded, but nonetheless I could not find a solution that was more simple than logging in as www-data via a SSH accessible user. In the end, I end up starting a migration to a CPanel-like system on my other VPS and moving the sites to that VPS.

Are you asking for help or are you just restating what you did?

---

### Post by wolfgentleman on 2015-06-05
> **bab1 said:**
> Are you asking for help Nope.
> **bab1 said:**
> are you just restating what you did?
I said what I did before, restated what I'm doing, and restated what I'm going to do.

---

### Post by SeijiSensei on 2015-06-05
The Drupal site I was working on had permissions granted to www-data, and the site was defaced as a result.  Worse, if www-data owns the sites/all/modules directory and has write permissions there, anyone who hacks your site can install any modules they want. 

We're pretty sure my client's site was defaced by an automated process that looks for vulnerable Drupal sites.  If you follow the procedures you suggest, you'll eventually end up on their list.

---

