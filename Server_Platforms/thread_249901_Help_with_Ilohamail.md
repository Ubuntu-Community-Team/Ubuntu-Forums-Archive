---
title: "Help with Ilohamail"
date: 2006-09-03
forum: Server Platforms
---

### Post by foxmulder on 2006-09-03
Hi,

I want to install Ilohamail on Ubuntu.

You can simply intsall it with apt-get install ilohamail

However: how do I configure everything?

In other words: is there a post-install how-to????

The documentation for Ilohamail itself only tells you how to do everything if you installed using a tarball.

But by using apt-get everything is all over the place...

HELP!

I looked here in the forums and using Google, but there is NO how-to whatsoever!

I run my own LAMP server so I have all that is needed...

Just need help on how to get it to run, preferable with MySQL...

---

### Post by foxmulder on 2006-09-03
Anyone?

---

### Post by dcherryholmes on 2006-09-18
Yes, I would also like to have some documentation.  Just for kicks.  Mind-melding with those install docs that whoever rolled the package didn't feel like including is cool and all, but I figure the author probably wrote them for a reason.  

In particular with IlohaMail (which gets installed just like that.... why not "ilohamail" for consistency?), after you go and download the tarball just so you can have a peek at the documentation, the docs say to "copy your IlohaMail folder to your document root.  OK.... what IlohaMail folder?  /usr/share/IlohaMail?  Doesn't look like it.  /etc/IlohaMail?  That would be retarded, seems to me.  Locate ilohamail/IlohaMail doesn't turn up much, and a scan of files installed from the package just show the /usr/share and /etc stuff.

Feh.  uw-imap doesn't play nice with squirrelmail, roundcube (also crappily documented) wants you to build a mysql database without really telling you how ("build it" is great if you already know that stuff, but c'mon), and IlohaMail is a friggin' *enigma* for something that is actually in the repository tree.

Rants aside, any tips on IlohaMail would be greatly appreciated.

---

### Post by zitch on 2006-09-18
"Document root" refers to what your www server uses as the directory that's web-accessible.  At least on debian, that would be under /var/www.  Where this is should be specified in your /etc/apache2/apache.conf file as the "DocumentRoot" parameter, I think.  From what I've seen, most of these website packages require that you install them by extracting/copying them into a directory in the web document root (or alternatively, create a softlink in the document root to the website package directory).

The documentation is probably still assuming that you're downloading the .tgz file directly from the IlohaMail website and installing from that.  It's unfortunate, but the .deb was not modified to account for this. 

From what I remember from installing IlohaMail from apt-get, there should be a folder like /usr/lib/IlohaMail (or it might be /usr/share/IlohaMail, I don't fully remember at the moment).  In that, there should be a "source" folder, which is what you want to copy to/soft-link from the document root folder.  I remember doing something like "ln -s /usr/lib/IlohaMail/source /var/www/IlohaMail" to get the package web-accessible.

Again, double check the directories, as it's been some time since I messed with IlohaMail.  I'm a SquirrelMail user myself. :)

Also, in terms of "building a MySql database", that usually means setting up a MySql user (with password) and a blank database that user has full access to.  Most of these website packages I've seen have some means of setting up the tables for you in whatever configuration utility was made for them, usually after you specify the MySql user, password and database.

---

### Post by dcherryholmes on 2006-09-19
Thanks for taking the time to reply.  I understand document roots and all that (I moved mine out of /var because it seems like a bad idea to me).  What I couldn't find was that source directory you were talking about.  I've since removed + purged ilohamail and dropped back to squirrelmail myself.  I was looking at alternatives to squirrelmail because I wasn't getting uw-imap to play nicely with it (plain text logins).  But I finally figured out what I needed was to run squirrelmail-config, switch authentication to TLS and manually change the imap port from 143 to 993.  After that it worked like a charm.

---

### Post by mendieta on 2008-04-12
same thing here. I know this thread has been dormant for a long time. I just installed latest ilohamail, and  I have no idea how to make it available in the webserver (apached2)

Documentation in is hard to find (I still couldn't find anything)

Is this project alive ? Would anyone recommend any similar package ? All i need is an easy to use interface to my email in pop/imap servers, just be able to view it, like with mailbee (maybe i should try that, but there are no packages in the ubuntu repos ...

Any tips, anybody?
Thanks!

---

### Post by mendieta on 2008-04-12
Well, some of the info above helped! But I am still stuck. I did 

```

sudo -i
cd /var/www/
ln -sf /usr/share/IlohaMail/source/ ./webmail

```

Now I can see the webmail folder in the mail server, but I can't open it. It asks me (in all webbrowsers I tried) to specify I should use to open a php html file. I guess the php module is not loaded in apache ? How would I do that ?

Thanks in advance!

---

