---
title: "/hello goes to /hello.php?"
date: 2007-12-26
forum: Server Platforms
---

### Post by flip79 on 2007-12-26
I'm using Apache2 on my Ubuntu laptop to work on a PHP site. I discovered that if I go to a non-existent directory (like [http://localhost/foo](http://localhost/foo)) the browser shows me the correspondent php script (if available, of course)... then [http://localhost/foo.php](http://localhost/foo.php) :confused:

mod_rewrite is not enabled.

What it could be?!?

Thank you in advance!

---

### Post by jtc on 2007-12-27
Identified whatever the magic happens on the server or on the client? What happens if you use a different browser?

---

### Post by flip79 on 2007-12-27
> **jtc said:**
> Identified whatever the magic happens on the server or on the client? What happens if you use a different browser?

Same using Firefox, Konqueror or Internet Explorer (IEs4Linux) from localhost. I still have to try from a different pc, but I think will be the same :confused:

**EDIT:** I found it!!!! It was the **MultiViews** option turned on in the configuration file of the site. Now this question is solved ^_^

---

