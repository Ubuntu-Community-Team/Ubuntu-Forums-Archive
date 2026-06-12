---
title: "Is there an Omenserver Autoget equivalent for XChat??"
date: 2007-05-09
forum: The Cafe
---

### Post by kevdog on 2007-05-09
I really miss the omenserver autoget script that provided a GUI I could use with mIRC.  It seems there really isnt a Unix equivalent -- or at least one that Ive found yet.  Does anyone have any knowledge of anything even close to this???

---

### Post by bonzodog on 2007-05-09
[http://sourceforge.net/projects/zeus-autoget/](http://sourceforge.net/projects/zeus-autoget/)

This is a script written for XChat that does the Omenserve/Autoget thing.

---

### Post by kevdog on 2007-05-09
I see this package requires the perl Tk libraries.  I tried installing thiis package through cpan, however it seemed the installation failed.  Any other suggestion on how to install the Tk package???

---

### Post by kevdog on 2007-05-09
Ok seems like Ive got the problem above worked out -- basically dont use CPAN rather use the ubuntu repositories to download the perl dependencies.

Anyway when I start the gu this is what I get (sample):

DBD::SQLite::db selectall_arrayref failed: no such table: dl_queue(1) at dbdimp.c line 271 at gui.pl line 242.
Couldn't perform select for load_queue: DBD::SQLite::db selectall_arrayref failed: no such table: dl_queue(1) at dbdimp.c line 271 at gui.pl line 242.
DBD::SQLite::db selectall_arrayref failed: no such table: message_swap(1) at dbdimp.c line 271 at Zeus_DB.pm line 29.
XS_Tk__Callback_Call error:DBD::SQLite::db selectall_arrayref failed: no such table: message_swap(1) at dbdimp.c line 271 at Zeus_DB.pm line 29.

Tk::Error: DBD::SQLite::db selectall_arrayref failed: no such table: message_swap(1) at dbdimp.c line 271 at Zeus_DB.pm line 29.
 Tk::After::repeat at /usr/lib/perl5/Tk/After.pm line 79
 [repeat,[{},after#8,2000,repeat,[\&main::gui_timer]]]
 ("after" script)
DBD::SQLite::db selectall_arrayref failed: no such table: message_swap(1) at dbdimp.c line 271 at Zeus_DB.pm line 29.
XS_Tk__Callback_Call error:DBD::SQLite::db selectall_arrayref failed: no such table: message_swap(1) at dbdimp.c line 271 at Zeus_DB.pm line 29.

Tk::Error: DBD::SQLite::db selectall_arrayref failed: no such table: message_swap(1) at dbdimp.c line 271 at Zeus_DB.pm line 29.
 Tk::After::repeat at /usr/lib/perl5/Tk/After.pm line 79
 [repeat,[{},after#9,2000,repeat,[\&main::gui_timer]]]
 ("after" script)
DBD::SQLite::db selectall_arrayref failed: no such table: message_swap(1) at dbdimp.c line 271 at Zeus_DB.pm line 29.
XS_Tk__Callback_Call error:DBD::SQLite::db selectall_arrayref failed: no such table: message_swap(1) at dbdimp.c line 271 at Zeus_DB.pm line 29.



Can someone help me --- looks like the DB isnt properly configured.

---

### Post by bonzodog on 2007-05-09
Do you have SQLite installed and set-up?

I don't know this package myself, but from reading those errors, it seems that it is failing to find something in SQLite's DB.

---

### Post by kevdog on 2007-05-09
I know I have it installed but I did nothing to set it up.  The problem is that with Zeus, all the files that came in the download package had no instructions how to set it up.  Unless I can find instructions, I guess Im really stuck!

---

