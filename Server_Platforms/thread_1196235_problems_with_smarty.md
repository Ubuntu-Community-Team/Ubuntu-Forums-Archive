---
title: "problems with smarty"
date: 2009-06-24
forum: Server Platforms
---

### Post by kustomjs on 2009-06-24
Hey Guys
currently I am having problems with smarty and I am getting this error message:

```
Fatal error: require_once() [function.require]: Failed opening required 'Smarty/Smarty.class.php' (include_path='.:/usr/share/php:/usr/share/pear') in /var/www/messagecenter/smarty.php on line 81
```

---

### Post by v3xtra on 2009-06-24
Well it is obviously looking for the file Smarty.Class.php in the Smarty Folder.  Is it in there?

---

### Post by Bachstelze on 2009-06-24
Also, the Smarty folder should be somewhere in the PHP include path.

---

### Post by kustomjs on 2009-06-24
I got the problem fix.  I had to include the /usr/share/php/smarty into the smarty.php page.

---

