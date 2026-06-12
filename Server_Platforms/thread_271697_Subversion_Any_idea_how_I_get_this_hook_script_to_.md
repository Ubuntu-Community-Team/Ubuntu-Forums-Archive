---
title: "Subversion: Any idea how I get this hook script to work?"
date: 2006-10-05
forum: Server Platforms
---

### Post by lingnoi on 2006-10-05
Hi all,

I have been using subversion for a while on my open source project and recently installed Ubuntu on our work server with subversion working.

What I am aiming for is that whenever a user makes a commit to our subversion repository that the post-commit script then svn exports the working repository into a directory in the apache2 www folder so that we have a working copy on the machines web server.

I have got this working on the command line by using:

```
sudo svn export file:///home/svn/projects /var/www/projects --force
```

I have no idea how to do this in a hook script because I am quite new to linux and subversion. 

I have tried adding this line to the default "post-commit.tmpl" file.

```
svn export file:///home/svn/projects /var/www/projects --force
```

Changing the file permissions of the "projects" folder in the www directory to be writeable by www-data but so far no luck.

Is there something I am doing wrong? Is there a better way to do this?

Thanks ](*,)

**Update:** Anyone who reads this. This is not the best solution to the problem. Take a look at the hot-backup.py script on how to get the latest version of your SVN repository.

---

### Post by lingnoi on 2006-10-05
Ok I am stupid. 

I did not take off the ".tmpl". When you want your hook scripts to be executed it looks for the file "post-commit" not "post-commit.tmpl"

Anyway, hope this helps someone else. :D

---

### Post by Maxtorm on 2007-03-13
First of all, thank you for posting this.  It helped immensely.  However, for some reason, my post commit is not working.  As in your example, the explicit export works fine, but the line in my post-commit file does not appear to execute.  I commented out everything in the tmpl file and added the following:
```
/usr/bin/svn export file:///var/lib/svn /var/www --force
```
It doesn't seem to want to work.  I've changed the owner on /var/www to www-data:www-data and did the same to /var/lib/svn, but the post-commit doesn't appear to fire.

Is there a log anywhere that you can see what error the script encountered?  Argh!  I feel like I am *this* close to finally getting this working.

**Update:**
A ha!  Dum dum me.  I forgot to change the executable flag on the post commit file.

---

### Post by MikeBenza on 2007-05-10
> **lingnoi said:**
> 

**Update:** Anyone who reads this. This is not the best solution to the problem. Take a look at the hot-backup.py script on how to get the latest version of your SVN repository.

Why isn't that the best solution?  I looked at hot-backup.py.  I don't  want a working copy of the SVN tree, I want an exported copy.  I don't want to publish any of the SVN meta data (anything in .svn.  I'm fairly sure the encrypted password is stored in there).


I've a working hook.  The hook script executes as me (my user).  It doesn't seem to execute the command
```

/usr/bin/svn export https://localhost/programs/Gallery/trunk/src/ /home/www-data/non-pro/Gallery --force

```

The hook runs fine when I run it from the shell (using an empty environment: *env - ./post-commit /var/lib/svn-repos 1234*), however, only the above command doesn't run in the hook.  Every other command in the hook runs fine every time.

---

### Post by Maxtorm on 2007-05-11
> **MikeBenza said:**
> The hook runs fine when I run it from the shell (using an empty environment: *env - ./post-commit /var/lib/svn-repos 1234*), however, only the above command doesn't run in the hook.  Every other command in the hook runs fine every time.

If it runs fine as you and does not execute correctly when the hook is called, I think it would indicate a permissions problem on the file, no?  The web server ends up executing the hook, so you would need to either set the execute flag for "others" or change the owner to www-data (assuming that is the context for the web server).  Is that the problem?

---

