---
title: "[SOLVED] Can't modify files in &amp;quot;default-site&amp;quot; (LAMP)"
date: 2008-10-05
forum: Server Platforms
---

### Post by dESAI on 2008-10-05
Greetings good people :)

I've just installed LAMP on my Ubuntu Desktop, but I can't modify files in the default directory. Can anyone help?

BTW I'm still a noob. and I'm not experienced with the terminal.

Thanks! :D

---

### Post by condonm on 2008-10-05
Did you check the permissions on the var/www/ folder? I find it hard to believe that lamp would have set the permissions to be read only... Just to make sure I'd try running

```
chmod 777 *
```

in the www directory.

---

### Post by dESAI on 2008-10-05
> **condonm said:**
> Did you check the permissions on the var/www/ folder? I find it hard to believe that lamp would have set the permissions to be read only... Just to make sure I'd try running

```
chmod 777 *
```

in the www directory.

Sorry I'm still not very good with the command lines. The directory I need to have rights to is:

"/use/share/apache2/default-site/*"

Thanks :)

---

### Post by Iowan on 2008-10-05
The files directory for the default, out-of-the-box "site" (on my LAMP server, at least) is **/var/www**, although the configuration file is  in "/etc/apache2/sites-available/default*"  Even if you changed the default location, you should be able to edit them with "sudo nano filename" or, for a graphic editor "gksudo gedit filename".  There are more options if "sudo-ing" the files is unacceptable.

---

### Post by dESAI on 2008-10-05
> **Iowan said:**
> The files directory for the default, out-of-the-box "site" (on my LAMP server, at least) is **/var/www**, although the configuration file is  in "/etc/apache2/sites-available/default*"  Even if you changed the default location, you should be able to edit them with "sudo nano filename" or, for a graphic editor "gksudo gedit filename".  There are more options if "sudo-ing" the files is unacceptable.

Hi :D

I don't think I changed the default location. It was my first LAMP install, so I just said yes, yes, yes...

But it worked! :D I was able to modify the file :) 1,000 thanks!

Next I need to copy a script into there. How can I change the settings so that I can paste files into there at will, using the GUI? 

I actually want to do a FTP (gFTP) download into there, so I need the directory to be writable.


Thanks.

D

---

### Post by Iowan on 2008-10-05
You're rapidly outpacing my (rather limited) expertise.  Changing write permissions to 777 seems a bit insecure, but keep it as an option.  My suggestion would be to change the ownership of that directory to your username using **sudo chown username directoryname**  (from a terminal).  More details about **chown** available by **man chown**. You could change the group, too.  I've never done FTP, so can't help there.

---

### Post by dESAI on 2008-10-05
> **Iowan said:**
> You're rapidly outpacing my (rather limited) expertise.  Changing write permissions to 777 seems a bit insecure, but keep it as an option.  My suggestion would be to change the ownership of that directory to your username using **sudo chown username directoryname**  (from a terminal).  More details about **chown** available by **man chown**. You could change the group, too.  I've never done FTP, so can't help there.

Thanks for you help again. I really appreciate it :D

Do I need to know th name of the "owner" to use that command, because I have no idea what it is :P

Anyway, I think all I need to know is exactly how to change the access rights to two directories. Or, change to the user who can access the directories.

FTP is basically just like pasting files into there from another location :)

Thanks :D

D

---

### Post by dESAI on 2008-10-05
Or, can I change it so it accesses files from any directory I want?

:confused:

---

### Post by Iowan on 2008-10-05
The "owner" would be you (actually, your username).  And yes, you could change where the files come from.  You'd edit DocumentRoot and Directory in the **/etc/apache2/sites-available/default** file.  It'd be better to build a new virtual host and activate it - leave **default** as a sample.  Much better information is available [here.]("https://help.ubuntu.com/community/ApacheMySQLPHP") 
I'm still learning this stuff myself.  My testbed server at work has a user-based website enabled. This home-server still has the default setup.

---

### Post by dESAI on 2008-10-05
> **Iowan said:**
> The "owner" would be you (actually, your username).  And yes, you could change where the files come from.  You'd edit DocumentRoot and Directory in the **/etc/apache2/sites-available/default** file.  It'd be better to build a new virtual host and activate it - leave **default** as a sample.  Much better information is available [here.]("https://help.ubuntu.com/community/ApacheMySQLPHP") 
I'm still learning this stuff myself.  My testbed server at work has a user-based website enabled. This home-server still has the default setup.

I'm not the owner for some reason... When I right-clicked and went to the permissions, it told me so :P

This is frustrating me now :(

OK, let me think...

---

### Post by lykwydchykyn on 2008-10-05
By default root is the owner of both the config files and the actual web directory.  You can change this directory to whatever you want, or (if you're lazy like me):

 - make a directory in your home directory called "www" or "htdocs" or "charlie" or whatever you like calling directories full of html files.
```

mkdir ~/www

```
 - Using sudo, remove /var/www
```

sudo rm -Rf /var/www

```
 - Using sudo, symlink /var/www to your web file directory
```

ln -s ~/www /var/www

```

Then you don't need to change anything in the configs (well, at least not yet), and you can read/write the website files.  Just make sure your files are world-readable (they should be by default).

---

### Post by dESAI on 2008-10-05
> **lykwydchykyn said:**
> By default root is the owner of both the config files and the actual web directory.  You can change this directory to whatever you want, or (if you're lazy like me):

 - make a directory in your home directory called "www" or "htdocs" or "charlie" or whatever you like calling directories full of html files.
```

mkdir ~/www

```
 - Using sudo, remove /var/www
```

sudo rm -Rf /var/www

```
 - Using sudo, symlink /var/www to your web file directory
```

ln -s ~/www /var/www

```

Then you don't need to change anything in the configs (well, at least not yet), and you can read/write the website files.  Just make sure your files are world-readable (they should be by default).

Thanks for trying to help :D

Once I to:
```

ln -s ~/www /var/www

```

It says "creating symbolic link ** : Permission denied :(

---

### Post by lykwydchykyn on 2008-10-05
Forgot to put a sudo on that. 
```

sudo ln -s ~/www /var/www

```

---

### Post by dESAI on 2008-10-05
> **dESAI said:**
> Thanks for trying to help :D

Once I to:
```

ln -s ~/www /var/www

```

It says "creating symbolic link ** : Permission denied :(

I love you! :D

1,000,000 thanks!

---

### Post by itsols on 2008-12-08
Many thanks for this great yet simple tip, IOWAN. I suppose changing ownership of the www folder would be the most appropriate. Actually I guessed that changing the folder to 777 wouldn't be advisable although it is possible.

But I have this doubt - I'm new to Ubuntu as a development platform, so maybe I'm wrong. Here's the issue. If we change ownership of the folder, wouldn't it affect other users logging in to the same computer. I'm refering to an Ubuntu desktop installation with LAMP?

Once again, your idea of changing ownerhsip IS what I think I should do, but this new issue worries me.

Any thoughts?

---

### Post by unutbu on 2008-12-08
Instead of changing the ownership and/or permissions on /var/www, 
I think it would be safer to simply use sudo to move the files into place:

To move a file into /var/www:```

sudo mv /path/to/file /var/www
```

or use a GUI with root privileges:
```
gksu nautilus
```

---

### Post by itsols on 2008-12-08
Thanks for this tip UNUTBU... In terms of allowing different developers to access the same www folder I think your method with nautilus is pretty cool. However, wouldn't this mean that we end up with multiple copies of the same code in different folders that will have to be moved to www? And also the issue is how we could test it? I mean, if we have the development folders elsewhere, everytime a modification needs to be tested, we'd have to move the files to www and I think this is a little too much of work in terms of delays and extra work.

Then again I don't suppose we'd face this problem if the development was in something like Dev-PHP where the the code can be tested within the IDE itself and finally moved to www.

Thanks again!

---

### Post by unutbu on 2008-12-08
itsols, I don't think I have a good answer to your questions.
If you have multiple developers working on the same code, then I think the proper way to handle this is to use version control software like cvs, subversion, or bzr.

You might also get some more advice by creating a new thread in the Programming Talk section: [http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39), where there are a number of people with web development and version control / project management experience.

---

### Post by itsols on 2008-12-08
Hi everyone, I think I pushed a little too much on this already SOLVED thread. Let me recap and afterwards maybe we'll move other issues to a new thread if the need arises - pretty smiles...

The issue: Can't modify files in the default www folder.

Background: I've switched from Windows. Back there, I would open my www folder and modify the files in them (WAMP server then), using DreamWeaver (DW). Thus via DW, I'd make the changes to whatever (eg: php, javascript, xhtml, etc), and minimise DW, then open up FireFox (FF) and test the changes on localhost/site...

But now on Ubuntu, I can't do that as the www folder is owned by root and I'd have to log in as root which I've learnt is not the ideal thing.

Solutions/suggestions I picked up on this thread:

1. Change ownership of root's www. 
Issue: What is then the plight of OTHER users logging in to the same computer to test/develop? They don't own it, right?

2. Remove root's www and make your own.
Issue: I think it's the same as the above, achieved differently...

3. Change the permissions to 777.
Issue: Yest it is the easiest but certainly not the best is it?

4. FTP the files to the www folder.
Issue: Nice but would be absurd on the same machine.

5. Use a different folder and move it to www.
Issue: Same as above. Furthermore, we'd not be able to actually test the code until we move it into www.

Conclusion: I think in fairness to all who are trying to contribute, we should consider this thread solved and keep it at that. Thus based on the initial problem, Solution #1 above is what I think is the most appropriate.

Anyway, it's wonderful to know that we have 4 other ways (based on the posts above) of getting around the issue.

Enjoy!

---

