---
title: "Errors executing exe"
date: 2008-12-30
forum: Wine
---

### Post by tech9 on 2008-12-30
I am getting the following error when trying to double click /single click any exe


```
End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
```

I realize that ubuntu is trying to open the exe as a zipped file or archive file, and if I execute this through wine or command line the exe will work.

Is there a way to fix this by executing the file by double or in my case single clicking the file?

---

### Post by Rohan Kapoor on 2008-12-30
Right click on it and select open with wine windows program loader!

---

### Post by tech9 on 2008-12-30
> **darth-vader said:**
> Right click on it and select open with wine windows program loader!

I am aware of this as I stated earlier. I am looking for the fix so that I can execute exes with a single click.

Thanks for the response anyway.

---

### Post by Rohan Kapoor on 2008-12-30
Ah I'm sorry, Try this (works for me) right click on the .exe and go to properties, go to the open with tab and click on the wine windows program loader. The close out. It should work:

---

### Post by tech9 on 2009-01-14
> **darth-vader said:**
> Ah I'm sorry, Try this (works for me) right click on the .exe and go to properties, go to the open with tab and click on the wine windows program loader. The close out. It should work:

Hi darth-vader,

      That's exactly what I was looking for. Thanks a lot :)

T9

---

### Post by Rohan Kapoor on 2009-01-14
> **tech9 said:**
> Hi darth-vader,

      That's exactly what I was looking for. Thanks a lot :)

T9

Glad to help!

---

