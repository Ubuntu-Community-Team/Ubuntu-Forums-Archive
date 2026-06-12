---
title: "exporting from website"
date: 2011-04-03
forum: Ubuntu One (CLOSED)
---

### Post by Technomouse on 2011-04-03
Hello i need to get my contact in vcard format but can not get evolution to sync with Ubuntu one is there any way i can export ALL my contacts from Ubuntu one to vcard?

thank you in advance

---

### Post by duanedesign on 2011-04-06
Could you please try the steps listed under [killing and restarting desktopcouch]("http://www.freedesktop.org/wiki/Specifications/desktopcouch/Documentation/Troubleshooting")

After following those steps can you see the Couch interface in your browser(step 4)?

If you are still unable to access the Ubuntu One addressbook in Evolution please try the following:

Applications->Accessories->Terminal, and run: 

```
evolution --force-shutdown
```

Then, if on < Maverick:
```
/usr/lib/evolution/evolution-data-server-2.28 > ~/evolution_debug.log 
```

Or, if on Maverick
```
/usr/lib/evolution/e-addressbook-factory > ~/evolution_debug.log 
```

Now launch Evolution. Applications->Internet->Evolution Mail 

Then try to reproduce bug and attach ~/evolution_debug.log to a bug report. You can[ file the bug here.]("https://bugs.edge.launchpad.net/evolution-couchdb/+filebug")

---

