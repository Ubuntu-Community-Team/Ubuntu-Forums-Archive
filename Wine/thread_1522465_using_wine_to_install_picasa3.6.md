---
title: "using wine to install picasa3.6"
date: 2010-07-02
forum: Wine
---

### Post by gregpo on 2010-07-02
i/ve tryed to install picasa3.6 using tweak5.4.1 from forum advice  does/nt happen will i try with wine allready have picasa 3 but it does/nt update please explain

---

### Post by kimikrishna on 2010-07-02
Follow the steps in this link : 

[http://www.webupd8.org/2010/04/how-to-install-picasa-36-in-ubuntu.html](http://www.webupd8.org/2010/04/how-to-install-picasa-36-in-ubuntu.html)

*After* installing picasa using the steps in this link, Do this :


Close  picasa  if it is opened.
Then run

```

gksudo nautilus /opt/google/picasa/3.0/wine/drive_c/Program\ Files/Google/Picasa3/runtime/geotag 
```

Rename the "geopanelscript.html" file to "geopanelscript.abc" 

The places button (in picasa) won't work.

And then start picasa 3.6 from App > Graphics 


Thanks to the webupd8.org  
and swiniak who posted a comment on the page to solve the "places" problem.

---

