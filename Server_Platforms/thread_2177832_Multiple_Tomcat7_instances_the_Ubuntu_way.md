---
title: "Multiple Tomcat7 instances the Ubuntu way?"
date: 2013-09-30
forum: Server Platforms
---

### Post by 1clue on 2013-09-30
Hi.
I've been doing a bunch of Tomcat servers as services on the same box for quite awhile now.  But I've always done it from scratch, by downloading the zip from [http://tomcat.apache.org](http://tomcat.apache.org) and installing Java separately and all that.  Basically, circumventing the Ubuntu packages in favor of rolling my own.

I've decided to stop that.  I've got one Tomcat now using the standard method outlined here: [https://help.ubuntu.com/13.04/serverguide/tomcat.html](https://help.ubuntu.com/13.04/serverguide/tomcat.html)

I've also looked at and used that tomcat7-user script, but it's based on a private tomcat.

Now what I'd like is to make it so I can have a stack of instances like this:
/var/lib/tomcats/tomcat7_8080
/var/lib/tomcats/tomcat7_8081
/var/lib/tomcats/tomcat7_8082

and so on.  I also want to use the same /etc/init.d script for all of them, and have an /etc/defaults/tomcat7_8080 and so on for settings.

So I guess here are my questions:

[LIST=1]
[*]How many people are doing this?
[*]I looked at the /etc/init.d/tomcat7 script and it appears that it will need to be modified in order to work correctly in this circumstance.  Does anyone have a modified script that works?
[*]Is there something already in the Ubuntu setup that handles this sort of thing more elegantly than what I see in the documentation?
[/LIST]

Thanks.

---

### Post by hawkmage on 2013-09-30
I have implemented a shared Tomcat environment for the company I work for that hosts 70+ applications.  I am not going to go into all of the details but I will give you an overview of how I did this.


[LIST]
[*]I do not rely on any Linux distros default installs/scripts.
[*]I have a directory that has the differing versions Java, Tomcat and Apache that the applications share.
[*]Each application runs as a different UID.
[*]Each Application UID has directories for its Tomcat and Apache instances. (Eg. for application UID myapp /app/tomcat/mypp and /app/apache/myapp)
[*]The application UID .profile runs a common script that loads its environment info for version of Apache, Java, Tomcat and other things for the application.
[LIST]
[*]This script checks for an application specific script that it will run if it exists, this is so each app can have custom things in their setup like DB server name/UID /passwords.
[/LIST]

[*]In the Applications tomcat directory there are sym links to the shared version of java and tomcat for the application.
[*]In the Applications Apache directory there is a symlink for the module directory to the appropriate shared Apache directory and the
[*]In the Application Apache directory other than the modules directory are all the standard default directories & files except that the envvars file in the bin directory defines the APACHE_HOME as where the shared apache directory is.
[*]I have a single init.d script that loops through all of the Application UIDs to start/stop them at boot/shutdown.
[/LIST]

With this setup I can have any combination of Apache, Tomcat and Java I want for each application according to their needs.

---

### Post by 1clue on 2013-09-30
Sort of like what I've been doing.  I'm getting tired of whittling it out of a stick though, and since Ubuntu is supposed to have thought all this out I figured I'd try it on my own.

Theoretically, I should be able to do this:

```

cd /etc/init.d
sudo ln -s tomcat7 tomcat7-8081

```

and then handle it in the appropriate runlevels and then the init script would suck in settings from /etc/default/tomcat7-8081 and should also be able to go to something like /var/lib/tomcat7-8081 for the CATALINA_BASE and so on.

I haven't tried it yet, but I think only maybe 4 changes in /etc/init.d/tomcat7 would do it.

---

### Post by hawkmage on 2013-09-30
If you look at the /etc/init.d/tomcat7 script you will see the following lines:
```
NAME=tomcat7
DESC="Tomcat servlet engine"
DEFAULT=/etc/default/$NAME
```

Then later in it:
```
if [ -f "$DEFAULT" ]; then
        . "$DEFAULT"
fi
```

By making a symbolic link /etc/init.d/tomcat_8081 to the /etc/init.d/tomcat7 it will not load a different default since it based on the NAME variable in the /etc/init.d/tomcat7 script.  You would need to make a copy of the /etc/init.d/tomcat7 as /etc/init.d/tomcat_8081 and change the NAME variable to "tomcat_8081" so it will load /etc/default/tomcat_8081.

---

### Post by 1clue on 2013-09-30
If I change it to:

```

NAME="$0"

```

then it will work with the symbolic links.  There are a few other places where I would use something other than a hardcoded "tomcat" in there too, but I figure $NAME would be a decent replacement.

Since /etc/init.d/tomcat7 is a repository-controlled file, I might have to change some locations to prevent it from being overwritten.  I might also need to change the directory name in /etc as well, maybe to /etc/tomcat7s/<name>

It shouldn't be too complicated, still trying to decide if I want to mess with it.

I keep thinking that just about every Tomcat box I set up has more than one instance on it.  Usually around 10 or so, sometimes more.  So why should we have to hack in our own tomcat when Ubuntu is already supposedly set up for multiple instances out-of-the-box?

If I can figure this out, I'll raise a bug in Jira with some recommended changes.  Maybe we can have a genuinely useful out-of-the-box Tomcat7.  It's already part way there because of tomcat7-user, I think I can leverage some of that.

It might be interesting to have an apache2 script as well, to set up hostname lookups.

---

### Post by hawkmage on 2013-10-01
I believe that would set the NAME to /etc/init.d/tomcat7 or/etc/init.d/tomcat_8081.  Since the init process doesn't cd into the /etc/init.d directory the $0 variable will most likely have the full path to the script.  You could use something like:
```
NAME=`echo $0 | awk -F\/ '{print $NF}'`
```

If the init.d script used bash instead of sh you could use:
```
NAME=${TEST##*/}
```

---

### Post by 1clue on 2013-10-01
I don't know.  I copied that from some other init scripts.  **grep '$0' /etc/init.d/*** and you get all sorts of stuff that uses $0.

Or maybe:
INITSCRIPT="(basename "$0")"

I need to copy a VM to try it out on, so it'll be a bit longer before I can start.

---

