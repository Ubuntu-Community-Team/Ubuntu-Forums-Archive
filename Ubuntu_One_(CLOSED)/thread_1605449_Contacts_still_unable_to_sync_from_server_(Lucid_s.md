---
title: "Contacts still unable to sync from server (Lucid stable ppa)"
date: 2010-10-25
forum: Ubuntu One (CLOSED)
---

### Post by NHclimber on 2010-10-25
After enabling the ubuntu one stable ppa and updating, I am still unable to sync *most* contacts.

The replication log reads (excerpted and redacted):
```
2010-10-25 09:34:16,779 DEBUG    want to replipull 'contacts' from  static host '5e46f0a3-6ae5-401e-9d7a-f732150c2a6f' @  couchdb.one.ubuntu.com
2010-10-25 09:34:16,779 INFO     Connecting to http://localhost:50098/.
2010-10-25 09:34:16,785 DEBUG    db exists, and we're ready to replicate
2010-10-25 09:34:16,785 DEBUG    asking 'http://localhost:50098/' to  replicate {'url':  'https://couchdb.one.ubuntu.com/u%2Fxxx%2Fxxx%2Fxxxxxx%2Fcontacts',  'auth': {'oauth': {dbus.String(u'consumer_secret'):  'HiddenHiddenHiddenHiddenHidden', dbus.String(u'token'):  dbus.String(u'xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx'),  dbus.String(u'consumer_key'): dbus.String(u'xxxxxxx'),  dbus.String(u'name'): dbus.String(u'Ubuntu One @ thor'),  dbus.String(u'token_secret'):  'HiddenHiddenHiddenHiddenHiddenHiddenHiddenHiddenHi'}}} to contacts
2010-10-25 09:34:17,852 ERROR    can't replicate  'u/xxx/xxx/xxxxxx/contacts'  'http://localhost:50098/' <== {'source':  {'url':  'https://couchdb.one.ubuntu.com/u%2Fxxx%2Fxxx%2Fxxxxxx%2Fcontacts',  'auth': {'oauth': {dbus.String(u'consumer_secret'):  'HiddenHiddenHiddenHiddenHidden', dbus.String(u'token'):  dbus.String(u'xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx'),  dbus.String(u'consumer_key'): dbus.String(u'xxxxxxx'),  dbus.String(u'name'): dbus.String(u'Ubuntu One @ thor'),  dbus.String(u'token_secret'):  'HiddenHiddenHiddenHiddenHiddenHiddenHiddenHiddenHi'}}}, 'target':  'contacts'}
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/desktopcouch/pair/couchdb_pairing/couchdb_io.py", line 288, in replicate
    content=record)
  File "/usr/lib/pymodules/python2.6/couchdb/client.py", line 985, in post
    **params)
  File "/usr/lib/pymodules/python2.6/couchdb/client.py", line 1035, in _request
    raise ServerError((status_code, error))
ServerError: (500, ('json_encode', '{bad_term,<0.361.0>}'))

```Of 239 contacts, only 27 records were pulled, 3 of which  aren't contacts ('_design/u1_record','_design/u1_contact' &  '_design/u1_funex').  I can't remember how I got the contacts up there  in the first place - could have been from Blackberry or Funambol on  Outlook.

The only way I got this far was to purge desktopcouch,  evolution-couch, ubuntuone-client*, python-ubuntuone-storage*, delete  all the data files I know of (~/.cache/desktop-couch,  ~/.local/share/desktop-couch, ~/.config/desktop-couch), follow the  launchpad answer for reinstalling ubuntu one, delete the desktop couch  keys, reboot, and reinstall.

Troubleshooting has become more  difficult now that I can't run the evolution-data-server from the prompt  (exits with return code 1?).

Any ideas?

~Peter

[UPDATE:  After shutting down evolution with --force-shutdown, and restarting it, which apparently prompted a new replication (or the amount of time elapsing composing the above message), *ALL* the contacts are now sync'ed!  However, there are the 3 extra records I noted above in the desktopcouch database - which show up as blank contacts. It still would be nice to know how to run the evolution-data-server from a prompt.... ]

---

