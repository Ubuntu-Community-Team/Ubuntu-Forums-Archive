---
title: "xchat-2.4.5"
date: 2005-09-20
forum: Requests
---

### Post by izaac on 2005-09-20
10-Sep-2005

    Released 2.4.5 for Linux/BSD/Unix. This version has been tested on FC4 and FreeBSD 4.11. It's recommended you upgrade to this version for security reasons. 

----------------------------------------------------------------------
 2.4.5
----------------------------------------------------------------------

 - Updated translations (cs, el, fr, gl, it, nl, sl, sr, vi, zh_TW).
 - Fixed incorrect information displayed in Plugins & scripts window
   under unix (xc244-fixpluginns.diff).
 - Added "/set irc_whois_front 1" option to show WHOIS in front tab.
 - Lots of speed ups under the hood, mainly in handling of URL
   highlighting during mouse motion. Also now allows underlining
   .name and .info domains [1230265].
 - Moved the "Insert color code" menu into the input box's right-
   click menu.
 - Fixed "Your Message" messing up when starting with a comma
   [1230269].
 - Added /id command to identify yourself to nickserv.
 - Added /gui MSGBOX <text> for scripters.
 - Added /menu command which lets plugins/scripts add their own
   menu items.
 - Added support for passive DCC chat via /DCC PCHAT <nick>.
 - Added support for DCC sending and receiving very large files
   (above 4 GB).
 - Improved layout of "Info" button in the DCC windows.
 - Improved layout of the nick-name right-click menu.
 - Improved /help command's display of plugins/script commands.
 - Fixed two bugs in detaching tabs (or CTRL-I) [1228926].
 - Added /uselect command for scripters to select nick names in the
   channel userlist (Daniel P. Stasinski).
 - Fixed possible crashes while using the SJIS (Japanese) charset.
 - Fixed various memory leaks in right-click menus.

---------------------------------------------------

Another reason?

---

