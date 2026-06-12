---
title: "creating new lists with mailman"
date: 2007-03-14
forum: Server Platforms
---

### Post by murrellr on 2007-03-14
I've installed ubuntu server 6.10 on my machine and most things have gone rather smootly, especially considering I'm a Linux novice and the server doesn't have the nice GUI.  I installed mailman, and began following the instructions in the Server Guide.  I got to the point to where I needed to create the default mailing list.  I executed:

sudo /usr/sbin/newlist mailman

Bu it said the list already exists.  So I browsed to 'http://www.myhost.org/cgi-bin/mailman/admin', and the admin page is displayed.  I go to .../admin/mailman, log in with with my administrator password, and I can change the default list.  So I go back up to .../admin and try to create a new mail list.  But after I fill in the form and give the administrator password, I get the following error:

'Error: You are not authorized to create new mailing lists'

I didn't find this problem on these forums, and a Google search of the error message gets me 200 hits.  It semed each one had a different solution and the Linuxese might as well have been Klingon.  I tried removing and reinstalling mailman, but that didn't help.

Is there a simple solution to this problem?

---

### Post by Mr. C. on 2007-03-16
Google is your friend, as are the mailman mailing lists:

[http://tinyurl.com/27st7f](http://tinyurl.com/27st7f)

If this doesn't solve the issue, search the other posts in the mailman archives.

MrC

---

### Post by murrellr on 2007-03-16
Its funny you referenced that URL.  I read it and concluded that I MUST have two instances of mailman installed, even though I only use apt-get to install it.  So I unsintalled it with apt-get.  And since I didn't know how another instance could have been installed, I did what any Windows user would do.  I found every directory and file named 'mailman' and deleted it.  And then I reinstalled mailman.  Gee, guess what.  Some of those files were not installed by the mailman package.  Files like '/etc/init.d/mailman' and the default mail list are gone.  I tried updating all the installed packages hoping someone would restore these files, but to no avail.

Like most Linux programs, the GNU mailman site assumes you are already an expert in every aspect of the program, including Python.  I tried following some of the instructions there but apparently the Ubuntu installation renames files and paths, so they were useless.  So I'm likely going to remove the mailman installation and hope to find a 'friendlier' package whose documentation matches the program.

P.S. 'sudo' can be a dangerous tool to the inexperienced.

---

### Post by murrellr on 2007-03-26
I was able to recover most of the missing files by running 'dpkg -x' against the mailman install package.  I don't understand why 'apt-get install' couldn't do that.  I recreated the default mailing list using the instructions in the server guide.  But I still have a problem.  When I navigate to the default mail list administration page at:

[http://myhost.com/cgi-bin/mailman/admin/mailman](http://myhost.com/cgi-bin/mailman/admin/mailman)

I get an error announcing a bug in mailman.  When I look in the mailman error log, it says that it couldn't find 'admlogin.html'.  I found this file under the mailman English (en) directory (sorry, I can't login to my server from work, so I can't give the exact location), as well as several other languages.  I ran 'dpkg-reconfigure' against mailman.  It asked me the language but this action didn't fix the problem.

So I have two questions.

1) Where should this file reside or what 'parameter' needs to be set so mailman can find it.

2) Can a Debian install package be disassembled to figure out what steps should have been done to properly install this on Ubuntu server?

---

### Post by Mr. C. on 2007-03-26
Many web packages are translated into various languages.  A language can be specified by the user, which is passed during content negotiation to the web server.  It designates which language should be used.  There are standard language codes, and pages are placed in language-specific locations, or with language specific suffixes.

Mailman places the admlogin.html in :

.... mailman/templates/**en**/admlogin.html

where "en" is the language code for English.  There are others.

To enable this, the MultiViews option must be set for the location or directory.

```
                Options MultiViews
```

Take a look at your mailman virtual site config file in /etc/apache2/...

and ensure that MultiViews is enabled.  See  [http://httpd.apache.org/docs/2.2/content-negotiation.html](http://httpd.apache.org/docs/2.2/content-negotiation.html) for more info.

MrC

---

### Post by murrellr on 2007-03-26
The web server seems to be set up OK.  But I realized that when I reinstalled it with dpkg, I did it 'root' instead of 'list'.  I tried to chown and chgrp files that check_perm complained about, but some of the links wouldn't change.  So I'm going to try to rip it out again, and install it according to the GNU mailman website directions.  apt-get seems to be a one-shot install.  If it goes wrong, it can't be repaired easily.   'apt-get remove' seems to leave a lot of turds and doesn't remove everything.  Without knowing the exact steps that the debian package is performing to install mailman, there is no way to fix it.  Pity.

---

### Post by Mr. C. on 2007-03-27
This is one of my biggest beefs in general with the *nux community and various distros trying to force a one-button install model into an environment that *requires* solid understanding of the fundamental infrastructure and security model of the OS.  People installing sophisticated software today have no idea what to do when the packages break, don't install, or create havoc on their systems.  It changes computer science and into computer voodoo, and this is bad for the industry as a whole.

Mailman only affects a handful of directories.  If you were to ask me, I'd say leave the installation as you have it, but do go read, as you've suggested, the mailman installation process, and learn how it needs to be configured and how it interacts with the system.

We're here to help (I've been running a mailman mailing list for years, btw).
MrC

---

### Post by murrellr on 2007-04-15
I don't know how I did it, but I got Mailman mostly working.  There is one oddity I'd like to fix.  To see the list of lists, I have to go to:

[http://mail.michiganantiqueradio.org/cgi-bin/mailman/listinfo](http://mail.michiganantiqueradio.org/cgi-bin/mailman/listinfo)

However, I'd like that to be:

[http://www.michiganantiqueradio.org/cgi-bin/mailman/listinfo](http://www.michiganantiqueradio.org/cgi-bin/mailman/listinfo)

since the 'www' is the prefix everyone knows.  Note that when you go to the 'mail...' address, you see the list.  But if you go to 'www...' it says there is no lists.  Any idea how to fix this?

---

### Post by Mr. C. on 2007-04-16
You need to configure your DNS A or CNAME record to provide the www hostname.  If this is already done, then you need to configure www as a virtual or real host in your web server setup.

MrC

---

### Post by murrellr on 2007-04-16
Are these Mailman settings?  This is the only page that is effected.  All the other pages, including the mailing list itself, works correctly with the www prefix.

---

### Post by Mr. C. on 2007-04-16
No, these are DNS and/or Apache settings.

From the internet, you need a name translation so that when one enteres "www.mydomain.com" they get to your site.  You need apache (web server) configured correctly to respond to "www.mydomain.com".

How did you get "mail.example.com" working ?

MrC

---

### Post by murrellr on 2007-04-17
The 'mail.example.com' was part of my DNS settings as an MX record as opposed to a CNAME record.  But it doesn't appear to be a DNS or Apache problem.  If you try the 'www' link I gave, the Mailman listinfo page is displayed correctly.  It just says there arn't any lists.  When you go to the 'mail' link, it shows the lists.  The problem is with the Mailman Python-generated content.  When I installed Mailman, I was only asked the language.  I don't know how it derived the 'mail' prefix.

I'm going to try another brute-force method I learned from Windows.  I'm going to search all the files on the disk to see which ones have the 'mail' address try to change it.

---

### Post by murrellr on 2007-04-17
Ha! Got it!  I found an entry in /etc/mailman/mm_cfg.py.  I changed:

DEFAULT_URL_HOST   = 'mail.michiganantiqueradio.org'
 to
DEFAULT_URL_HOST   = 'www.michiganantiqueradio.org'

My thanks to Mr. C for responding to my posts.

I must say that I have NEVER had this much trouble with any Microsoft program, going back to MS-DOS 1.0!  I hope this stings you Linuxers out there to your hearts, so that you will not only write good programs, you will also write good installers, uninstallers, and DOCUMENTATION.

"There was a little girl, who had a little curl
right in the middle of her forehead.
And when she was good, she was very, very good,
But when she was bad, she was horrid."
--The little girl's name was Linux.

---

### Post by Mr. C. on 2007-04-17
Glad you got it working.

You've clearly never setup Microsoft Exchange, or a Windows Active Domain server!  Mailman is very powerful, as are many server programs in general, regardless of platform.  Complexity is the nature of these beasts unfortunately.

Best of luck,
MrC

---

### Post by mbradlcu on 2007-05-11
> **murrellr said:**
> I've installed ubuntu server 6.10 on my machine and most things have gone rather smootly, especially considering I'm a Linux novice and the server doesn't have the nice GUI.  I installed mailman, and began following the instructions in the Server Guide.  I got to the point to where I needed to create the default mailing list.  I executed:

sudo /usr/sbin/newlist mailman

Bu it said the list already exists.  So I browsed to 'http://www.myhost.org/cgi-bin/mailman/admin', and the admin page is displayed.  I go to .../admin/mailman, log in with with my administrator password, and I can change the default list.  So I go back up to .../admin and try to create a new mail list.  But after I fill in the form and give the administrator password, I get the following error:

'Error: You are not authorized to create new mailing lists'

I didn't find this problem on these forums, and a Google search of the error message gets me 200 hits.  It semed each one had a different solution and the Linuxese might as well have been Klingon.  I tried removing and reinstalling mailman, but that didn't help.

Is there a simple solution to this problem?

for me the fix was running 'mmsitepass -c some_new_password'.

in this case google was not my friend ; )

---

