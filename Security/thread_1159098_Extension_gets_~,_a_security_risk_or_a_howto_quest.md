---
title: "Extension gets ~, a security risk? or a howto question?"
date: 2009-05-14
forum: Security
---

### Post by Endlesskiss on 2009-05-14
Well, When I edit a PHP File on my apache, a file named file_name.extension~ is automatically generated and is readable by everyone, I found myself able to read my config.php file by adding ~ to the file extension [[http://mysite.com/config.php~]]("http://mysite.com/config.php%7E%5D").

how can I disable this auto generation? [or it's just built-in and impossible to be canceled?]

Thanks from advance!

---

### Post by cdenley on 2009-05-14
Are you using gedit to edit the files?
edit>preferences>editor tab
There is a checkbox under "File Saving" that says "Create a backup...".

Also, you could deny access to these files by creating this file:
/etc/apache2/conf.d/backups
```

<Files *~>
Deny from All
</Files>

```

---

### Post by Endlesskiss on 2009-05-14
Thank you :)

---

### Post by drubin on 2009-05-16
On the point of denying access to those files:
Why are you even uploading those files to a live environment?

---

### Post by Endlesskiss on 2009-05-19
I'm not uploading them!

Once I'm editing a file they're automatically generated [well, now I've disabled the backup option so they're no longer generated].

---

### Post by drubin on 2009-05-22
> **Endlesskiss said:**
> I'm not uploading them!

Once I'm editing a file they're automatically generated [well, now I've disabled the backup option so they're no longer generated].

Are you files on the server via gedit?

---

