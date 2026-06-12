---
title: "Testing for App Indicator Library in C"
date: 2012-10-04
forum: Ubuntu Application Development
---

### Post by Conzar on 2012-10-04
How can I test in C for the existence of the app indicator library?

I found [code]("http://askubuntu.com/questions/13197/how-to-program-a-status-icon-that-will-display-in-ubuntu-as-well-as-in-other-dis") in python to do this:
```
have_appindicator = True
try:
    import appindicator
except:
    have_appindicator = False
```

---

