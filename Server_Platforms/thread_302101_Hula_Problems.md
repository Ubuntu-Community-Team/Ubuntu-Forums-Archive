---
title: "Hula Problems"
date: 2006-11-18
forum: Server Platforms
---

### Post by Khaine on 2006-11-18
I followed the guide here [http://www.hula-project.org/Getting_Started](http://www.hula-project.org/Getting_Started) to install hula.  My problem is that when I try and log in as admin it complains that it "Could not load contacts or calendars (check Logs)"

the log says:

DEBUG: got current user: undefined
DEBUG: GET l10n/en.js finished: (0.08 seconds)
DEBUG: trying to log in as admin
DEBUG: GET /user/admin/preferences/dragonfly.json started...
DEBUG: GET /user/admin/preferences/dragonfly.json finished: (1.432 seconds)
DEBUG: Empty preferences, loading defaults.
DEBUG: GET /user/admin/calendar/all/calendars.json started...
DEBUG: GET /user/admin/addressbook/personal/contacts.json started...
ERROR: Exception GET /user/admin/calendar/all/calendars.json: MochiKit.Async.XMLHttpRequestError: Request failed: HTTP Error: 401/
ERROR: Exception GET /user/admin/addressbook/personal/contacts.json: MochiKit.Async.XMLHttpRequestError: Request failed: HTTP Error: 401/
ERROR: error loading contacts/calendars: MochiKit.Async.XMLHttpRequestError: Request failed: HTTP Error: 401/
DEBUG: Checking if zone for $("content")<DIV> canDisposeZone
DEBUG: Checking if zone for $("notebook1")<DIV class="notebook tabs-visible"> canDisposeZone
DEBUG: Checking if zone for $("???")<DIV> canDisposeZone
DEBUG: Checking if zone for $("???")<DIV> canDisposeZone
DEBUG: Checking if zone for $("content-iframe")<DIV> canDisposeZone

I have no idea how to fix it, does anyone have any ideas ?

---

### Post by fnjordy on 2006-11-18
Hula isn't released yet, its a very unstable product I would recommend leaving it until v1.0 unless you plan to aid development.

---

