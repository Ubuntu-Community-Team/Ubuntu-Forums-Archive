---
title: "Apache2 - Browse directories in /var/www from Firefox"
date: 2011-08-16
forum: Server Platforms
---

### Post by consequent on 2011-08-16
I recently installed Apache on Lucid Lynx (Macbook 1.1) using the following tutorial:

[http://tuxtweaks.com/2010/04/installing-lamp-on-ubuntu-10-04-lucid-lynx/](http://tuxtweaks.com/2010/04/installing-lamp-on-ubuntu-10-04-lucid-lynx/)

Everything appears to work correct except that when I browse [http://localhost/](http://localhost/) in Firefox, I cannot see any of the directories.  Although, files such as html documents are visible.  When I view the /var/www directory using the default graphical file browser, all of its child directories have Xs over their icons.  When I attempt to open the directory "js", the following error message displays:
[INDENT]The folder contents could not be displayed.
You do not have the permissions necessary to view the contents of "js".

[/INDENT]I figured this was preventing Firefox from viewing the directories.  So I launched it with the "gksu" command to see if it would help.  I still couldn't see directories when browsing [http://localhost/](http://localhost/)

Any help will be greatly appreciated.  I'm basically trying to achieve functionality identical to the MAMP local server for Mac OS X.  I'm about to start a LAMP project for a new client so having this up and running is important!

---

### Post by Bachstelze on 2011-08-16
For starters, *never* run Firefox with gksu!

The problem has nothing to do with Firefox, it's on the server. Check the permissions of the subfolders of /var/www. They should at least be browsable and readable by the user Apache runs as (www-data by default).

---

### Post by Wim Sturkenboom on 2011-08-17
Why would you want to make the contents of the js (javascript?) directory visible in a browser? Only reason I can think of is if you want to make it easy for visitors to download the scripts in there. Not being able to list them does not necessarily mean that apache can't serve them.

But OK, that is your problem although I'm very curious. If Bachstelze's reply does not sort it, you have to look at the directory directives in the apache configuration if you really want to list them. I've recently installed Apache on a Ubuntu 10.04 system.

The below is the default configuration (/etc/apache2/sites-available/default) and it does allow to display the directory listing.
```

        <Directory /var/www/>
                Options **[COLOR="Red"]Indexes[/COLOR]** FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

```
The word in red makes that apache will display a directory listing (if it can't find something like index.html).

The below is an example that prevents the directory listing of files in the subdirectory *testje* (and will throw a 403 error at you)
```

        <Directory /var/www/testje>
                Options FollowSymLinks MultiViews
        </Directory>

```

So check what the settings are.

You can edit the files with the editor of your choice. Not sure if manually editing files is the way of doing things on Ubuntu server. They might well have some non-standard command for it.

---

### Post by consequent on 2011-08-17
First off, thanks to both of you for promptly responding.

--

**In regards to Bachstelze's post**, I made myself a member of the group "www-data", then browsed [http://localhost/;](http://localhost/;) still no directories.  It seems like there should be a simpler solution than changing file permissions on all child directories.  I'm an ubuntu/linux "newb", so please elaborate as to why I shouldn't use gksu to run Firefox.  Btw, I also ran firefox via sudo and su.  I figured this could involve some stability/security risks, however, I really don't care about breaking my OS since everything is backed up and there's no sensitive information on the hard drive.

**In regards to Sturkenboom's post**, yes "js" is a directory containing a ****-ton of javascript "programs" (w/ corresponding html docs).  This is a local server I intend to use for web design/development work.  When I meet with a potential client, I simply browse through my local server via Firefox and demonstrate various technologies, layouts, navigations, et cetera.  Once I find what I want, I just copy and paste code into new documents.  Wahla!  A new website is born.

On MAMP, all directories (and children) in the "htdocs" folder are visible.  Whenever I browse to a directory with an index.html or index.php file, it is automatically parsed and the output is rendered by the browser.  WHEN I RUN NAUTILUS AS ROOT WITH SUDO, APACHE DOES SERVE MY PHP FILES WITHOUT ANY OBVIOUS ISSUES.  MySQL databases also appear to work without errors.  MY DEFAULT CONFIGURATION FILE IS IDENTICAL TO FIRST ONE YOU LISTED.

--

Thanks again for trying to help.  Hopefully I can pay it forward some day.

---

### Post by Wim Sturkenboom on 2011-08-17
It's not about you having the permissions. It's about apache having the permissions to read.
So making yourself a member of the www-data group does not help when viewing stuff in the browser.

I suggest that you check /var/log/apache2/error.log to get an idea of what is wrong.

And yes, there is a simpler way than changing permissions. I develop and host the sites in my home directory. With default settings setup, apache is / should be able to read from there (not write).

You can easily edit the earlier mentioned file and replace all references to /var/www to /home/youruser/yourdemoweb. Just make sure that the directory yourdemoweb exists before restarting apache.

---

### Post by consequent on 2011-08-17
I copy and pasted the text from the error log into Google and found this thread:

[http://ubuntuforums.org/showthread.php?t=1476965](http://ubuntuforums.org/showthread.php?t=1476965)

I'll give it a try later today and let you know how it goes.  The last post by James78 is definitely worth reading.

---

### Post by AlexNagy on 2011-10-16
> **Wim Sturkenboom said:**
> It's not about you having the permissions. It's about apache having the permissions to read.
So making yourself a member of the www-data group does not help when viewing stuff in the browser.

I suggest that you check /var/log/apache2/error.log to get an idea of what is wrong.

And yes, there is a simpler way than changing permissions. I develop and host the sites in my home directory. With default settings setup, apache is / should be able to read from there (not write).

You can easily edit the earlier mentioned file and replace all references to /var/www to /home/youruser/yourdemoweb. Just make sure that the directory yourdemoweb exists before restarting apache.

I'm having a similar problem with apache.

I've tried symlinking the website directories from my home folder to /var/www (after moving the default to www-bak).

I've done everything short of moving my files (in a folder served by Dropbox for offsite backup) to /var/www (doable, but trying not to have to do that). This is for local testing only and is not meant for the world.

---

