---
title: "gaim session startup"
date: 2005-04-22
forum: Ubuntu Backports
---

### Post by ubuntu_demon on 2005-04-22
I just encountered a problem with gaim. I think I have solved it.

My desktop would lock up / wouldn't respond normally right after I logged in.

If anyone experiences weird behavior right after logging in they should try to remove gaim from the session startup (or try to give it a number above 50 ... I haven't tried this one yet)

maybe this line in my .xsession-errors is related :

```

** (gnome-panel:16091): WARNING **: Unkown action type 'home' from /apps/panel/objects/object_2/action_type

```

edit :

It seems to be a problem with the samba client.I thought this were independent small problems. Samba problem started when I wanted to imported huge quantities of mp3's into my playlist.

---

