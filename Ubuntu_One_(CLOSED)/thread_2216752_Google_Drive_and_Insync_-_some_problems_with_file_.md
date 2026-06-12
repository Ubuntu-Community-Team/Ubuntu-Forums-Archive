---
title: "Google Drive and Insync - some problems with file names"
date: 2014-04-13
forum: Ubuntu One (CLOSED)
---

### Post by mainmeister on 2014-04-13
With Ubuntu One closing and Google lowering the prices of the Google Drive storage (15G free) I decided to try this as a replacement for Ubuntu One. I ran into one problem with the synchronization stalling on file names with non UTF8 characters. Once these where corrected it seems to work very well.

Here is the script I used to fix the file names

```
find /path/to/files -type f -print0 | \
perl -n0e '$new = $_; if($new =~ s/[^[:ascii:]]/_/g) {
  print("Renaming $_ to $new\n"); rename($_, $new);
}'

```

---

### Post by eric-ericwarnke on 2014-04-16
Hey there, we're providing a free migration for this exact problem. Blatant plug, but our service, Mover, specializes in migrating and backing up cloud platforms and we just announced our support for Ubuntu One. Here's a link to our announcement. [https://blog.mover.io/2014/04/15/rescuing-ubuntu-one/](https://blog.mover.io/2014/04/15/rescuing-ubuntu-one/)

Apologies for the spam but I think we can save you some headache.

---

