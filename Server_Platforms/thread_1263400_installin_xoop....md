---
title: "installin xoop..."
date: 2009-09-10
forum: Server Platforms
---

### Post by zander1013 on 2009-09-10
hi,


i would like to install xoops [http://xoops.org](http://xoops.org) onto a server i have setup an ibm t60 thinkpad using the ubuntu 9.04 installer for service as a lamp. i have also installed a desktop onto my server and all appears to be "good to go".

i am new to the server world but have allot of experience using linux desktop and command line. i would like to install xoops locally so that i can experiment and get a feel for it before i deploy it on my actual site. i have used the basic command line cd, mkdir, rm, chmod, ln, cp, ect... and vi for years. but i am really stumped by the instructions. especially the ones like "setup the www server, php and database properly"(sic)...:P

these are the instructions for install...

First time installation
Preface:

XOOPS is an open-source Object-Oriented Web publishing system written in PHP. It is an ideal tool for developing small to large dynamic community websites, intra company portals, corporate portals, weblogs and much more.

XOOPS is released under the terms of the GNU General Public License (GPL) and is free to use and modify. It is free to redistribute as long as you abide by the distribution terms of the GPL.
Requirements

    * WWW Server (Apache, IIS, Roxen, etc)
    * PHP 4.3.0 or higher (5.2 or higher recommended)
    * MySQL 3.23 or higher (4.1 or higher recommended)

:confused: are the basic requirements met by the default ubuntu 9.04 lamp install?

Before you install

   1. Setup WWW server, PHP and database server properly.
   2. Prepare a database for your XOOPS site.
   3. Prepare user account and grant the user the access to the database.
   4. Make the directory /uploads/ and the file mainfile.php writable
   5. If you need to install protector module: replace the file mainfile.dist.php in your XOOPS root directory with /extras/mainfile.dist.php.protector.

   6. For security considerations, you are strongly advised to move the two directories /xoops_lib/ (for XOOPS libraries) and /xoops_data/ (for XOOPS data) out of document root and change the folder names.

   7. Make the directory /xoops_data/ writable; Create (if not already present) and make the directories /xoops_data/configs/, /xoops_data/caches/, /xoops_data/caches/xoops_cache/, /xoops_data/caches/smarty_cache/ and /xoops_data/caches/smarty_compile/ writable.

   8. Turn cookie and JavaScript of your browser on.

Installing locally

If you are running a local environment for development or testing, make sure that you have the previous requirements met. Once this is done, copy the contents of the htdocs directory (from the XOOPS distribution file or SVN) to the root document path of your web environment. Once the files are copied there, you can start the install by typing "http://yoursite.com". This will start the install process.

can someone please guide me through this process? i am pretty much lost up to the point where i am to "copy the contents of the htdocs directory (from the XOOPS distribution file or SVN) to the root document path of your web environment. Once the files are copied there, you can start the install by typing "http://yoursite.com"." i know how to copy those files and type "http://yoursite.com" into a web browser.

thank you for your patience and consideration in this matter.:KS

-zander:)

---

