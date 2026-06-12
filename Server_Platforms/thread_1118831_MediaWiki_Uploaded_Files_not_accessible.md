---
title: "MediaWiki Uploaded Files not accessible?"
date: 2009-04-07
forum: Server Platforms
---

### Post by kooldino on 2009-04-07
I have mediawiki installed, and it's set up so that users can upload files.  However, when they successfully upload them, it places them in a path under the /images folder that doesn't exist.  While it appears to have uploaded, the file does not exist.  I have verified this via the shell.

Maybe my wgUploadDirectory and wgUploadPath mismatched?

Any ideas?

---

### Post by kooldino on 2009-04-07
Ok, so thus far I figured out that it doesn't actually upload the files to the disk, but mediawiki thinks it does.

---

### Post by kooldino on 2009-04-08
help?

---

### Post by Paul Weaver on 2009-04-09
You'll probably find that your directory your uploads are supposed to be saved in isn't world-writable (or writable by apache). If you check the apache error log you might see something saying this.

---

### Post by kooldino on 2009-04-10
> **Paul Weaver said:**
> You'll probably find that your directory your uploads are supposed to be saved in isn't world-writable (or writable by apache). 

They're 777.  I checked:

/var/www/wiki/images

as wel as:

/usr/share/mediawiki/images

*note: /var/www/wiki is a symbolic link to /usr/share/mediawiki

> 
If you check the apache error log you might see something saying this.

Just errors from people trying to access "uploaded" files that don't exist.

Also to note: The database that runs this wiki was exported from mediawiki 1.10 and imported into a fresh installation of the latest and greatest mediawiki.

---

### Post by kooldino on 2009-04-13
Monday morning bump.

---

### Post by kooldino on 2009-04-16
Thursday bump.

---

### Post by kooldino on 2009-04-20
Yet another monday bump.

---

### Post by Ateles on 2009-05-04
I'm having the same problem... the upload directory is writeable, other previously uploaded files exist in the directory.  Mediawiki acts like the file has been uploaded, but the file isn't actually being uploaded.  Also no errors in the Apache logs.

Any ideas would be appreciated.  Thanks!

---

