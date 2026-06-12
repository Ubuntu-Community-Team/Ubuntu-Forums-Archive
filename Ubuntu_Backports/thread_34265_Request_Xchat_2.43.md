---
title: "Request: Xchat 2.43"
date: 2005-05-14
forum: Ubuntu Backports
---

### Post by Dax0r on 2005-05-14
Can Xchat 2.43 be added on backports?
The current version in Hoary is 2.4.1

[http://xchat.org/download/](http://xchat.org/download/)

> ----------------------------------------------------------------------
[SIZE=1] 2.4.3
----------------------------------------------------------------------

 - Updated translations (de, sq, zh_CN).
 - Fixed crash of server list connect button when no network is
   selected while using GTK's auto-find feature [1166669].
 - Fixed handling of WhoIs Special event on some networks where it
   could chop off the first character [1164315].
 - Plugin API changes: Added "nickserv" field to xchat_get_info.
 - Python: Fixed get_list() incorrectly failing when the list
   contained a time field [1171525].
 - Perl: Make scripts using calls with fully qualified subs work again
   [1170139] (Lian Wan Situ).
 - Fixed input-box input-method (GTK I.M.) problem [1168239].
 - Fixed: Ignore and Notify windows incorrectly used the stock CLOSE
   button instead of DELETE [1170655].
 - Placed Close/Connect buttons in correct position in server list
   [1165474].


----------------------------------------------------------------------
 2.4.2
----------------------------------------------------------------------

 - Updated translations (ca, de, lt, nl, ru, sk, sr, vi).
 - Added command line args -u and -p.
 - Fixed handling of "MODE -o+o nick nick" (#1094026).
 - Plugin API changes:
   * Added "Key Press" print event.
   * Added "state_cursor" for xchat_get_prefs.
   * Added xchat_strip and xchat_free functions.
   * Added "lasttalk" field to "users" list.
   * Added "charset" field to xchat_get_info.
 - Perl plugin changes (Lian Wan Situ):
   * Move each script into their own unique package/namespace. Scripts
     containing multiple packages will not be loaded.
   * When warning messages are emitted you will now be told which
     script it came from.
   * Xchat::set_context will now accept Xchat::set_context( $channel )
     and Xchat::set_context( $channel, $server ) in addition to
     Xchat::set_context( $context ).
   * Fix display of loaded scripts in the Plugins and Scripts window.
 - TCL: Fixed crash with invalidated TCL timer (#1110306) (Daniel P.
   Stasinski).
 - /TIMER now supports timeouts to one decimal place.
 - Fixed possible crash of open-file dialog on 64-bit machines.
 - Pressing CTRL-O in the DCC Receive window will now open your
   downloads folder.
 - Win32: Default download folder changed to "My Documents\Downloads".
 - Added -quiet arg to the /charset command.
 - The /country command now supports a wildcard search.
 - The user is now warned when real/user name is left blank in the
   server list window.
 - Added the /URL command.
 - Added a text event for all unknown WHOIS reply lines.
 - Added /ALLCHANL which sends to the current server only.
 - Actions (/ME) are now treated like PRIV/CHAN for purposes of the
   ignore list[/SIZE].

---

### Post by Burgundavia on 2005-05-14
Breezy doesn't even have 2.4.3 yet, but it is in unstable, so I suspect it will come in a few days.

Corey

---

### Post by Technoviking on 2005-05-14
Done (in staging), and have added xchat-systray (in staging/universe).

Mike

---

### Post by whatever on 2005-05-14
[QUOTE=Mike Basinger]Done (in staging), and have added xchat-systray (in staging/universe).

Mike[/QUOTE]
 why does it depend on python2.3 instead of python2.4 ?

---

### Post by Technoviking on 2005-05-14
[QUOTE=whatever]why does it depend on python2.3 instead of python2.4 ?[/QUOTE]
This version is from Sid and not Ubuntu, I did not notice that requirement since I have to use Python 2.3 for work.:-\"

I will rebuild it once it makes it into Breezy. Don't worry, Python 2.3 and 2.4 can live side by side.

Mike

---

### Post by Dax0r on 2005-05-16
Thank you

---

### Post by Burgundavia on 2005-05-16
2.4.3 just hit Breezy.

Corey

---

### Post by Technoviking on 2005-05-16
[QUOTE=Burgundavia]2.4.3 just hit Breezy.

Corey[/QUOTE]
I will rebuild it ASAP.

Mike

---

### Post by Technoviking on 2005-05-16
The new package is uploaded, and no longer requires python 2.3.

Enjoy,
Mike

---

### Post by whatever on 2005-05-17
[QUOTE=Mike Basinger]The new package is uploaded, and no longer requires python 2.3.[/QUOTE]

thx :)

---

### Post by Homer on 2005-05-20
I don't have Python script support anymore with this package :(.  I will be forced to downgrade to the official package :(

---

### Post by Technoviking on 2005-05-20
[QUOTE=Homer]I don't have Python script support anymore with this package :(.  I will be forced to downgrade to the official package :([/QUOTE]
Looks like the Breezy xchat package maintainer has it compiling againist python 2.4 but part of the configuration is still look for Python 2.3. I have submitted a bug report  for this and will, try to fix it also.

Mike

---

### Post by RastaMahata on 2005-05-22
[QUOTE=Homer]I don't have Python script support anymore with this package :(.  I will be forced to downgrade to the official package :([/QUOTE]
 any tips on downgrading xchat?? :(

---

### Post by Homer on 2005-05-22
1. Remove Ubuntu backports in your /etc/apt/sources.list

2. sudo apt-get update

3. sudo apt-get remove xchat
(will also remove ubuntu-desktop, but it's ok)

4. sudo apt-get clean
(don't know if it's necessary, but I did it)

5. sudo apt-get install xchat ubuntu-desktop

Should work ;)

---

### Post by Dax0r on 2005-05-22
[QUOTE=Homer]I don't have Python script support anymore with this package :(.  I will be forced to downgrade to the official package :([/QUOTE]


What scripts do you use?

---

### Post by Homer on 2005-05-22
[QUOTE=Dax0r]What scripts do you use?[/QUOTE]

My own scripts

---

### Post by RastaMahata on 2005-05-23
[QUOTE=Dax0r]What scripts do you use?[/QUOTE]
 rhythmbox script.. [www.rhythmbox.org](www.rhythmbox.org)

---

### Post by Technoviking on 2005-06-02
The new source from Breezy fixes the problem, uploading to staging.

Mike

---

