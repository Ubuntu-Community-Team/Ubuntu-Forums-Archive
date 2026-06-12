---
title: "SquirrelMail - folder_synch plugin problem"
date: 2007-12-08
forum: Server Platforms
---

### Post by satimis on 2007-12-08
Hi folks,


Ubuntu 7.04 server amd64
squirrelmail-1.4.12


I followed;

3.2 Installing SquirrelMail on Unix and Linux systems 
[http://www.squirrelmail.org/docs/admin/admin-3.html#ss3.2](http://www.squirrelmail.org/docs/admin/admin-3.html#ss3.2)

To install SquirrelMail from source.  It is now working w/o problem.


Later I installed folder_synch plugin on;

[http://www.squirrelmail.org/plugin_view.php?id=64](http://www.squirrelmail.org/plugin_view.php?id=64).


Installation went through w/o problem.  After finish it does not work.


On Display Preferences page

following options found missing;
Address Book Take
Bug Reports
Delete/Move/Next Buttons
Fortunes
Folder list update forces message list update
Message list update forcess folder list update


Googling did not help me.


Can any folk shed me some light how to fix the problem?  TIA


B.R.
satimis

---

### Post by MJN on 2007-12-08
Have you re-ran conf.pl in <SMroot>/config/ to enable the plugins?

Mathew

---

### Post by satimis on 2007-12-08
> **MJN said:**
> Have you re-ran conf.pl in <SMroot>/config/ to enable the plugins?
Hi Mathew,


No.


Googling brought me some information.  I tried 2 of them separately as follows;


1)
As root run;

cd /usr/local/squirrelmail/www/config/
./configure

This is quite funny to me.  After selecting the folder_synch on running ./configure the 1st time, it disappears on running ./configure the second time.


$ ls -l /usr/local/squirrelmail/www/ | grep plugin```

drwxr-xr-x 21 root root  4096 2007-12-07 18:11 plugins

```


2)
Copying following lines at the bottom of config.php```

/**
 * To install plugins, just add elements to this array that have
 * the plugin directory name relative to the /plugins/ directory.
 * For instance, for the 'sqclock' plugin, you'd put a line like
 * the following.
 *    $plugins[0] = 'sqclock';
 *    $plugins[1] = 'attachment_common';
 */
// Add list of enabled plugins here
$plugins[0] = 'administrator';

```


None of them solve my problem


satimis

---

### Post by MJN on 2007-12-09
Change into your Squirrelmail web directory, then cd config and run ./conf.pl

This is the configuration tool for SM and, amongst other things, lets you choose which plugins to enable.

Mathew

---

### Post by satimis on 2007-12-09
> **MJN said:**
> Change into your Squirrelmail web directory, then cd config and run ./conf.pl

This is the configuration tool for SM and, amongst other things, lets you choose which plugins to enable.

Mathew
# cd /usr/local/squirrelmail/www/config
# ./conf/pl

```

SquirrelMail Configuration : Read: config.php (1.4.0)
---------------------------------------------------------
Main Menu --
1.  Organization Preferences
2.  Server Settings
3.  Folder Defaults
4.  General Options
5.  Themes
6.  Address Books
7.  Message of the Day (MOTD)
8.  Plugins
9.  Database
10. Languages

D.  Set pre-defined settings for specific IMAP servers

C   Turn color on
S   Save data
Q   Quit

```

Command >> 8  [Enter]

```

SquirrelMail Configuration : Read: config.php (1.4.0)
---------------------------------------------------------
Plugins
  Installed Plugins
    1. administrator

  Available Plugins:
    2. abook_take
    3. bug_report
    4. calendar
    5. delete_move_next
    6. demo
    7. filters
    8. folder_synch
    9. fortune
    10. info
    11. listcommands
    12. mail_fetch
    13. message_details
    14. newmail
    15. sent_subfolders
    16. spamcop
    17. squirrelspell
    18. test
    19. translate

```

Command >> 8 [Enter]```


Plugins
  Installed Plugins
    1. administrator
    2. folder_synch

  Available Plugins:
    3. abook_take
    4. bug_report
    5. calendar
    6. delete_move_next
    7. demo
    8. filters
    9. fortune
    10. info
    11. listcommands
    12. mail_fetch
    13. message_details
    14. newmail
    15. sent_subfolders
    16. spamcop
    17. squirrelspell
    18. test
    19. translate

R   Return to Main Menu
C   Turn color on
S   Save data
Q   Quit

```

Command >> S [Enter]
```

Data saved in config.php
Press enter to continue...

```

Command >> Q
```

Exiting conf.pl.
You might want to test your configuration by browsing to
http://your-squirrelmail-location/src/configtest.php
Happy SquirrelMailing!

```


Start SquirrelMail and login

Options -> Display Preferences

following 2 options displayed in addition;

Folder list update forces message list update:	
Message list update forces folder list update:	


check both options -> Submit

Restart squirrelmail (this is necessary otherwise won't work) and login

Folder synch works whenever an email read the number next to INBOX is reduced.  The mails deleted on this folder are dump to Trash folder.


However "Purge" next to Trash is not displayed?  Scrap mails are in this folder waiting for dumping

Thanks


satimis

---

### Post by MJN on 2007-12-09
It might have been easier to simply confirm the plugin gets loaded using conf.pl - I know what the tool looks like! ;)

> Restart squirrelmail (this is necessary otherwise won't work) and loginSquirrelMail is a PHP web application hence there is no 'restart' - just log out of SM and back in again.

> However "Purge" next to Trash is not displayed?  Scrap mails are in this folder waiting for dumpingDunno - have you tried clicking the 'Check Mail' link to refresh the frame? Perhaps folder_synch doesn't cause a refresh for deleted message recounts (i.e. it only does it when the number of new messages decreases - that was the original intent of the plugin).

Mathew

---

### Post by satimis on 2007-12-09
[QUOTE=MJN]
Dunno - have you tried clicking the 'Check Mail' link to refresh the frame? Perhaps folder_synch doesn't cause a refresh for deleted message recounts (i.e. it only does it when the number of new messages decreases - that was the original intent of the plugin).
[/QUOTE]
Hi Mathew,


It looks a little bid funny to me.  "Purge" sometimes appears another time disappears beyond control.  SquirrelMail mailing list can't help.


Others noted and thanks.  

I'll start another thread "Change Password" direct on SquirrelMail login page later.


B.R.
satimis

---

