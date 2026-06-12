---
title: "Listen announce script for xchat"
date: 2006-04-08
forum: The Cafe
---

### Post by oxEz on 2006-04-08
I made a small script which allow Listen users to display the current song in xchat. This is not really evolved for a script, but I'll eventually add more features  
when I have the time.

What you must have installed: xchat, dbus, python and python-dbus (they should be installed by default I think)

I posted two files in attachements. (both are in .gz, type gunzip 'file' to remove the .gz extension.)

listen.py: it's the script itself, put it in ~/.xchat2

dbus_manager.py: since it contained an error, I modified it a bit, and added more features to get more information about the song. (Listen authors will probably modify it in the next version, and fix the bug I found in it.)

You have to copy my dbus_manager.py in /usr/lib/listen/ (please backup the old one in case things go wild!)

To use it, type /listen np in xchat!

Suggestions, critics are welcome.

  - oxEz

---

### Post by LightsOut on 2006-04-09
im bout to try it now. Hopefully it works

---

### Post by LightsOut on 2006-04-09
couldn't get it to work:

```
[09:58] XChat module for Listen loaded
[09:58] Introspect error: The name org.freedesktop.listen was not provided by any .service files
[09:58] <brucki> nah man
[09:58] Traceback (most recent call last):
[09:58]   File "/home/duane/.xchat2/listen.py", line 34, in listen_command_handler
[09:58]     return np(word[1:], word_eol[1:], userdata)
[09:58]   File "/home/duane/.xchat2/listen.py", line 23, in np
[09:58]     current_song = listen.current_song()
[09:58]   File "/usr/lib/python2.4/site-packages/dbus/proxies.py", line 102, in __call__
[09:58]     reply_message = self._connection.send_with_reply_and_block(message, timeout)
[09:58]   File "dbus_bindings.pyx", line 458, in dbus_bindings.Connection.send_with_reply_and_block
[09:58] dbus_bindings.DBusException: The name org.freedesktop.listen was not provided by any .service files
```

error that i got trying to load and do a /listen np

---

### Post by LightsOut on 2006-04-09
know of any other xchat mp3 announce scripts?

---

### Post by oxEz on 2006-04-10
Well currently the script doesn't check if you're running Listen or not.. The script is made for current version (0.4.2)

---

