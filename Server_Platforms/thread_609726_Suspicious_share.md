---
title: "Suspicious share"
date: 2007-11-11
forum: Server Platforms
---

### Post by dgrafix on 2007-11-11
How come i have a share name that is not in the smb.conf file that appears to be sharing /tmp. Is there anything else that could be telling this folder to share? interestingly enough it is not visible simply by browsing smb://server but i can access my tmp folder by using smb://server/sharename. I only noticed it when using my xbox to connect. It lists it.  am a bit concerned about this as i understand that /tmp can be linux's achillies heel.

---

### Post by MJN on 2007-11-11
You can see what you're sharing with **smbclient -L localhost -N** - post the output of this and we can see how it compares to default.

Mathew

---

### Post by dgrafix on 2007-11-11
Here is the line causing the concern:

```
PDF             Printer   PDF
```

Here is the share thats sharing my /tmp it appears to be some kind of cups: pdf printer, but i can actually view /tmp files when i share to smb://servername/PDF !!! 

I need to know where to disable this, as it isnt in smb.conf. Its a bit worrying seeing as i never knowingly allowed this to be shared.

---

### Post by MJN on 2007-11-11
I guess the PDF printer dumps the output in /tmp.

Check your printer settings - you must have a PDF printer listed somewhere.

Mathew

---

### Post by dgrafix on 2007-11-11
i did a ctrl-f search for both "PDF" and "/tmp" in smb.conf and it isnt there, i also checked nfs /etc/exports (impossible, but just to make sure) its really weird. Mabe cups manager has done something but i cannot remember the port for the interface [http://localhost: ????](http://localhost: ????)

edit - i also noticed shared is unchecked in gnome administration > printers > PDF printer

I do have the generic PDF printer installed but i never shared it. But it seems to be allowing my /tmp folder to be accessable across the smb network by accessing \\servername\PDF - even though it is not listed under \\servername\ :(

---

