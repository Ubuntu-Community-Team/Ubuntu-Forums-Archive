---
title: "How to set up Ubuntu Server for inexperienced people"
date: 2010-06-16
forum: Server Platforms
---

### Post by dan40 on 2010-06-16
Hi all,

Last year I created an article on how to set up a Ubuntu Linux server for newbies that hasn't seen much in the way of traffic or comments, so I thought I'd just advertise that site right now.

For those of you who are thinking of setting up a server but don't exactly know how to do so, the article I wrote might be handy as it contains screen captures of each of the setup steps and an explanation of what each setup option does.

Nearing the end of the article, I put on some basic commands, tell you how to set up your server, add phpmyadmin for databases and setting up your web server.

Until I wrote this as I set up my server, I didn't have a clue how to do it so what you see before you I wrote from my setup experience.

Check it out at [http://www.dansmith.ca/linuxsetup](http://www.dansmith.ca/linuxsetup) and feel free to leave me a comment. I'm always open to suggestions for improving the article.

Cheers,
Dan

---

### Post by mörgæs on 2010-06-17
Thanks, good work. You could also add a link to the article here:
[http://ubuntuforums.org/showthread.php?t=1487198](http://ubuntuforums.org/showthread.php?t=1487198)
 

Just one question:

"First, you must decide if you really want to get rid of your Windows OS and actually switch to Ubuntu, because once you do there&#8217;s no going back, and all information will be erased from your current Windows setup."

Is this true on serverside, that you can not have Ubuntu and Windows on the same machine?

---

### Post by TEVERTH on 2010-06-17
Hi! I am consulting with a school.
I am suggesting they move to a edubuntu LTS setup for their student systems. However they will also need to carry on using their windows PCs and windows server 2003 for teachers and admin work. 
Now the need arises for teachers or admin staff to also log into the edubuntu server to check students work etc.
Is there a solution for opening a linux thin client like session inside a web browser from a windows platform? 
In the ideal world the windows user would open a browser and type the URL of the edubuntu server in to get a new session inside a browser tab.
Any idea how this can be done.
Sorry if this is not the right place to ask this.
TE

---

### Post by mörgæs on 2010-06-17
I guess best is to ask in Absolute Beginner Talk. It is the most active of the fora.

---

### Post by ThesaurusRex on 2010-06-17
> **TEVERTH said:**
> Hi! I am consulting with a school.
I am suggesting they move to a edubuntu LTS setup for their student systems. However they will also need to carry on using their windows PCs and windows server 2003 for teachers and admin work. 
Now the need arises for teachers or admin staff to also log into the edubuntu server to check students work etc.
Is there a solution for opening a linux thin client like session inside a web browser from a windows platform? 
In the ideal world the windows user would open a browser and type the URL of the edubuntu server in to get a new session inside a browser tab.
Any idea how this can be done.
Sorry if this is not the right place to ask this.
TE

You could use Cygwin from inside Windows, and make the remote connection to the server to use Edubuntu. Is that what you're asking for?

---

### Post by dan40 on 2010-06-17
> **mörgæs said:**
> Is this true on serverside, that you can not have Ubuntu and Windows on the same machine?

Interesting concept.  I've never even thought about installing Ubuntu linux/server/ws on a machine that already has Windows on it.  If anyone knows of a way to do this, please post the instructions!

---

### Post by mörgæs on 2010-06-17
I can not tell you how to, since I dropped Windows years ago, but you will find heaps and loads of posts in this forum regarding the topic (on client side, that is).

---

### Post by drdos2006 on 2010-06-17
Hi dan40,
Nice HOWTO, and I have a question. 
Where you modify the Apache Web directory, you indicate changing the permissions for this folder by  <chmod -R 777 /var/www/
This would allow Users, Groups and Others full permission to modify the files in this directory. Is it not better to set the Permissions to 770 where Users and Groups can change the folder contents but not Others ? Please let me know if my thought is not correct, for I intend to follow your guide to experiment with.

regards

---

### Post by Zip247 on 2010-06-17
Your tutorial is good, I did find a problem though...

> therwise, always log on with your non-root user ID & password, and issue any commands using:

> sudo <command string>

Doing so will ask you for your root password.

using SUDO as a not root user will require you to put YOUR password in, not roots.  As long as the logged in user is permitted to SUDO.

---

### Post by dan40 on 2010-06-17
> **wdecker said:**
> Using SUDO as a not root user will require you to put YOUR password in, not roots.

Thank you wdecker, you are correct.  I have made the modification.

---

### Post by dan40 on 2010-06-17
> **drdos2006 said:**
> Where you modify the Apache Web directory, you indicate changing the permissions for this folder by  <chmod -R 777 /var/www/
This would allow Users, Groups and Others full permission to modify the files in this directory. Is it not better to set the Permissions to 770 where Users and Groups can change the folder contents but not Others ?

Hi drdos2006,
In some instructions I found on the web, I found that particular instruction and reiterated them in my post.  It seemed to work for me, and I didn't mention anything in the article about changing them back, did I?!

it is true, it would make sense to change the permissions back to 770, a setting that is more secure than 777.

Dan

---

### Post by The Real Dave on 2010-06-17
> **dan40 said:**
> Thank you wdecker, you are correct.  I have made the modification.

You should probably explain about adding the regular user to the sudoers list then.

> **mörgæs said:**
> Thanks, good work. You could also add a link to the article here:
[http://ubuntuforums.org/showthread.php?t=1487198](http://ubuntuforums.org/showthread.php?t=1487198)
 

Just one question:

"First, you must decide if you really want to get rid of your Windows OS and actually switch to Ubuntu, because once you do there&#8217;s no going back, and all information will be erased from your current Windows setup."

Is this true on serverside, that you can not have Ubuntu and Windows on the same machine?

No. You can keep both, and use GRUB to choose between each at startup, just as for any Ubuntu release.
[B]
@OP[/B] I'd suggest you alter that section, at explain how the user can select either version from the GRUB menu, ensuring that they configure their partition's correctly. Of course, if they are using Dynamic Disks on Windows, they will have to erase the disk, but I presume your guide is more suited to those attempting to create a home server type deal.
EDIT: I see now that you guide was dealing with letting the installer control all the partitioning itself, making the above correct. Still, it could be useful to explain the options. The thought of blanking a harddrive can often been intimidating to someone who is new to this kind of thing.

Also, as a general note, linking to a free and decent ISO burner will save some confused comments. [ImgBurn]("http://www.imgburn.com/") is a fantastic freeware ISO burner.

---

### Post by Zip247 on 2010-06-17
> You should probably explain about adding the regular user to the sudoers list then.

I believe by default any user in the admin group can sudo.  The original user set up during install is automatically in the admin group.

---

