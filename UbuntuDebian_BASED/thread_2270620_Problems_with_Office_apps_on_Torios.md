---
title: "Problems with Office apps on Torios"
date: 2015-03-24
forum: Ubuntu/Debian BASED
---

### Post by andfree on 2015-03-24
When I installed on my laptop and updated Torios, there was a Document Viewer on Apps => Office menu and I could use it to open PDFs. But there was not an app for opening DOCs.

Then I installed LibreOffice, but when I tried to start Libre Office Writer I got a message box:

```
LibreOffice 3.5 - Fatal Error 
```

It’ s a problem with permissions which was fixed by using the command:&#65279;

```
sudo chown -R $USER ~/.config
```

Now LibreOffice is installed and works, but there’s not anymore the Document Viewer on Apps => Office, so I can’t open PDFs.

---

### Post by andfree on 2015-03-25
I installed Evince and got the job done.

---

