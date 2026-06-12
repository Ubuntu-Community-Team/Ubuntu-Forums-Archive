---
title: "Help with Firefox Gran Paradiso using dark GTK theme"
date: 2007-11-30
forum: The Cafe
---

### Post by herbster on 2007-11-30
I'm trying FF Gran Paradiso now and since I use a dark GTK theme, the forms in web pages are dark. Previously with FF 2 I've been using the fix that came with the Neutronium theme which is as follows:

```
1. Backup the original file:
sudo mv /usr/lib/firefox/res/forms.css /usr/lib/firefox/res/forms_backup.css

2. Replace it with the provided forms.css
sudo mv /<downloaded location>/Neutronium-GTK2/forms.css /usr/lib/firefox/res/forms.css

3. Then you need to edit html.css:
sudo gedit /usr/lib/firefox/res/html.css

Around line 60, change:

body {
  display: block;
  margin: 8px;
}

To:

body {
  background-color: white;
  color: black;
  display: block;
  margin: 8px;
}

Save the file, then restart Firefox, and you should have standard colours
```

I am wondering where these files will be with Gran Paradiso so I can change them. I couldn't find them in /usr/lib/firefox-3.0/

This is definitely faster than FF 2.0, so I'd really like to stick with it.

---

### Post by jmn2k1 on 2008-01-04
I'm just start using a dark theme and FF3 and have the same problem... I tried those fixes (the files are in the same place FIREFOX_3_INSTALL_DIR/res/ at least using a version downloaded from Mozilla) but dont seem to work now (or Im doing something wrong...)

---

