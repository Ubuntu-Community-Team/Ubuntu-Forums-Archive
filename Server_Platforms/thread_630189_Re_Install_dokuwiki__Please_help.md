---
title: "Re: Install dokuwiki : Please help"
date: 2007-12-03
forum: Server Platforms
---

### Post by mogra on 2007-12-03
I badly need help for installing dokuwiki on my laptop for the personal use.

This going to my last attempt to install,

Laptop : PowerBook G4 15" , tiger 10.4

Things I tried so far :

Followed instructions from official dokuwiki forum :
[http://wiki.splitbrain.org/wiki:install](http://wiki.splitbrain.org/wiki:install)

But it didnt work , uninstalled three times and reinstalled.

Then friend of mine gave me following instructions :
DokuWiki requires a Web server running PHP. These are the steps I followed to get DokuWiki set up on my Mac:

1. Download DokuWiki from [http://www.splitbrain.org/projects/dokuwiki](http://www.splitbrain.org/projects/dokuwiki). I downloaded
latest version
2. I unpacked the DokuWiki archive and moved the contents to ~/Sites/dokuwiki.
3. I enabled the Apache Web server. From System Preferences > Sharing, I checked the Personal Web Sharing checkbox. My Mac is running Apache version 1.3, and its URL is [http://localhost/](http://localhost/) or [http://127.0.0.1/](http://127.0.0.1/). Append &#8220;~myid&#8221; to the URL to get to the document root for user myid (fill in your own user name).
4. I installed PHP 5.1.6 by following the instructions at [http://www.entropy.ch/software/macosx/php/#install](http://www.entropy.ch/software/macosx/php/#install).
5. I set the permissions for the dokuwiki directory (and all enclosed items) to read and write, for Owner, Group, and Others. This can be easily done in the Finder via File > Get Info on dokuwiki.
6. The URL of your Wiki is [http://127.0.0.1/~myid/dokuwiki](http://127.0.0.1/~myid/dokuwiki).


But hard luck it still doesnt work for me.

I get following error
Forbidden
You don't have permission to access /~myid/dokuwiki on this server.
Apache/1.3.33 Server at mogra.local Port 80


Can anybody please help me?

I am not much familiar with all the permissions issues. This forum is my last hope.

Thanks a lot
__________________

---

### Post by sciurus on 2007-12-03
> **mogra said:**
> 

I am not much familiar with all the permissions issues. This forum is my last hope.

Thanks a lot
__________________

Since this forum is for users of the Ubuntu Linux operating system, not Mac OS X, it's probably not a good *last hope*.

---

