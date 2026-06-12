---
title: "Trouble with Wordpress file permissions"
date: 2021-10-26
forum: Server Platforms
---

### Post by hipnerd2 on 2021-10-26
I'm a web developer and occasional Ubuntu desktop user.

I recently decide to set up an Ubuntu 20.10 LAMP server at my house using some old hardware as a development environment for Wordpress. The LAMP part went fine (I even substituted MariaDB for mySQL) but after installing Wordpress I was unable to update plugins. It wanted FTP/SSH information from me. Poking around it appears as if I did not have the permissions/ownership of the directories and files involved set up correctly. 

I attempted for follow at least three different online guides on how to set this up. None worked. I figured that I should stop making changes that alter the environment but don't fix anything and see if someone could here could give me solid guidance.

---

### Post by LHammonds on 2021-10-26
There are at least 2 methods for doing updates/plugin installs.

The secure method has the web server / database permissions set to just the minimum for running the site which means you cannot use the web-based updater to do online updates or installs.

When I setup wordpress installs, I created two database IDs, one for normal daily operation which had the minimal set of permissions needed (it could not create/delete database/table structures) and another that had full DBA permissions to just the wordpress database.  When it came time to do updates / installs, I would modify the wordpress config to use the DBA account so it could make any necessary changes to the database structure it wanted.

The flip side is the file system permissions and with Ubuntu / Apache, the user:group that runs Apache is www-data:www-data.  Most files/folders are set with the minimum permissions (usually read-only) so that it is more difficult for a hacker to compromise the application / database and then the OS.  The only folders that have write permission normally are the upload content folders that the web server can write to...which means an auto-upgrade will not work.  You would need to modify the websites permissions so the web service can do the auto-upgrade or since you are touch the server anyway, just do it manually with the root account and after the upgrade/install, correct all the files ownership and permissions.  I always used a Bash script to ensure it was always set correct after every time I touched the system....and it ran on a regular basis on its own.

It is generally a bad idea to let the web server run in such a way that it can update itself...because whatever the web server can do, so can a hacker that utilizes an exploit in the app.

It should also be pointed out that I NEVER installed wordpress based on "apt install" because it never worked the way I wanted it to.  It always bundled the database install with it and I always wanted my database server separate and dedicated for multiple application servers to use...which meant I always had to install / update manually and not via "apt update"

As for following online guides, there are many different ways to configure a web server and following one guide and switching to another may not work well due to different design choices implemented.  Guides can also fall behind in relevance depending on newer OS, newer web server, newer application, newer database.   For example, I wrote my own guide for installing and updating NextCloud but I fell behind several versions since I no longer maintained it.  When I needed to upgrade several versions, it turned out that my method for updating the password directly in the database using MD5 function no longer worked (needed to use the occ command) and my typical NextCloud password was invalid because it was 9 characters in length and the minimum changed to 10 in that application.  So that process was a bit different than what was published in nearly every guide due to recent changes in the application.

So, all that I said above is...don't setup your server so that the app can update itself or install add-ons itself.  Yes, it makes it super convenient for you but that also creates super-bad security habits that do not just stop at your development area...more often than not, dev work turns into production work super fast and if you were not building it as a production-worthy system, it will bite you when you least expect it.

LHammonds

---

### Post by hipnerd2 on 2021-10-26
> **LHammonds said:**
> There are at least 2 methods for doing updates/plugin installs.

It is generally a bad idea to let the web server run in such a way that it can update itself...because whatever the web server can do, so can a hacker that utilizes an exploit in the app. 

I understand the principle, but this is a test server on my home network. It is not, generally speaking, public facing. I am weighing the balance of security and ease of use. I maintain dozens of Wordpress sites for various clients. None of them are using the "FTP method" to upload files. I am comfortable with the level of risk that allowing the update feature to run as designed would entail.

> It should also be pointed out that I NEVER installed wordpress based on "apt install" because it never worked the way I wanted it to.  It always bundled the database install with it and I always wanted my database server separate and dedicated for multiple application servers to use...which meant I always had to install / update manually and not via "apt update"

I installed by downloading the tarball via "wget" and unpacking. I didn't even think of using apt to install Wordpress itself.


> So, all that I said above is...don't setup your server so that the app can update itself or install add-ons itself.  Yes, it makes it super convenient for you but that also creates super-bad security habits that do not just stop at your development area...more often than not, dev work turns into production work super fast and if you were not building it as a production-worthy system, it will bite you when you least expect it.

LHammonds

As mentioned above, I am comfortable with the tradeoff of some security for some ease of use if it means I can use the plugins repository to select and install plugins instead of having to manually download and install every single one of them. This is a test environment to quickly prototype websites to show to clients, and then the server will be reset for the next client. 

Having to locate, download and install every single plugin or update from the shell would create a lot of drag on my time that would better be served working on web design. I am comfortable with the same level of security that Bluehost or Host Gator provides in a production environment. The only time I've worked on something this locked down is when I worked on a Fortune 500 company's website -- and this isn't that.

So to clarify, I am looking for the correct permission settings to allow Wordpress on my home server to behave in the same way that it does when hosted on a commercial hosting service such as Bluehost.

---

### Post by MAFoElffen on 2021-10-27
If you want to replicate what you would have to conform to on Bluehost, then ask Bluehost what they set their permissions to for their own hosting specific environment... and set yours to those. 

As per what LHammonds told you, that is common sense and real-world. What he said and recommended is what you would have to comply to, in some kind of way or form of, if you were to go to a hosted environment, or much less, than if you were to host it yourself. (As it only applied to WordPress itself.) Of course, you could do what you want on your own test environment, if is isolated and detached from all but you, but the goal to learn the system, that is something that is meant to be accessible to the world, is to learn it like it really is in the "real world" isn't it? Instead of getting in the habits of doing something that will get you into troubles later, right?

@LHammonds

Thank you very much for this. That was very well thought out, and one of the very best approaches I have ever read regarding WordPress. Much more than what I could have answered.

---

### Post by SeijiSensei on 2021-10-28
I've implemented most of what LHammonds suggests on my WP installs.

First, I put all my sites under a separate username and add that user to the www-data group.  

Next, I wrote two simple scripts that I use to change permissions before and after updates.

Before an update I run this:
```

#!/bin/sh
chmod g+w wp-admin wp-includes wp-content -R
chmod g+w *
echo "Run update now"

```

That restores write permissions to members of the www-data group to which the website owner belongs.

After running an update I run the script
```

#!/bin/sh
chmod u+rwx,g+rx wp-admin wp-includes wp-content -R
chmod g-w *

```

Both these scripts must be run as root from the top of the WordPress directory tree.

---

