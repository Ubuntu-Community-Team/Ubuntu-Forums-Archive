---
title: "Permissions and security"
date: 2006-07-11
forum: Server Platforms
---

### Post by az on 2006-07-11
In regards to a web application that needs read-write permissions to a folder, is it better to have that folder owned by root and make it world-read and writeable or would it be better to just chown it to www-data:www-data?

---

### Post by venzen on 2006-07-11
I'd go with chown www-data:www-data.
as you might suspect anyway giving world readable/writeable permissions to files and folders owned by root is... well, you might blink in the dark when you should be sleeping ;)

---

### Post by az on 2006-07-11
Yes, but all of the web applications (of which I am aware) that are installed from the ubuntu repositories, write to /var/www/whatever where /whatever and it's contents are owned by root.

---

### Post by az on 2006-07-11
Oops.  I just noticed I made a mistake in my original post.  I don't think I was clear.

What I meant was, is it better for a LAMP application's directory to be root-owned and only world-readable with a few files and folders writeable, rather than www-data-owned and therefore the whole thing writeable by www-data?

In the former case, www-data cannot write to the whole directory and in the latter case, it can.

Would it be best to have the folder owned by root and only the files or directories that need write access two be owned by www-data?

---

