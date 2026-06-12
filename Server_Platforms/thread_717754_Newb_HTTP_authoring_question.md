---
title: "Newb HTTP authoring question"
date: 2008-03-07
forum: Server Platforms
---

### Post by uberlinux on 2008-03-07
I'm not even sure if this is the right place to post this, but...

I've got a static html website that I'd like to make a change to, but don't want to have to change all the pages individually.

I'd like to add more page links to the sidebar here:
[http://kfiresmith.homeunix.org/kfiresmith/index.htm]("http://kfiresmith.homeunix.org/kfiresmith/index.htm")
The problem for me is, the only way I know to add more links to the sidebar is to manually edit each page. 

Does anyone know how to edit all the pages at once?

Thanks!
 - Kodiak

---

### Post by Dr Small on 2008-03-07
Yes, but it would require knowing Php and variables.

---

### Post by uberlinux on 2008-03-07
Anyone else?  Not looking to use PHP...  More just looking for a way to insert a few lines of text into .html pages wholesale.
Thanks guys,
 - Kodiak

---

### Post by Dr Small on 2008-03-07
Copy and paste then... But nothing gets simpler than Php and global variables.

---

### Post by Oldsoldier2003 on 2008-03-07
> **uberlinux said:**
> I'm not even sure if this is the right place to post this, but...

I've got a static html website that I'd like to make a change to, but don't want to have to change all the pages individually.

I'd like to add more page links to the sidebar here:
[http://kfiresmith.homeunix.org/kfiresmith/index.htm]("http://kfiresmith.homeunix.org/kfiresmith/index.htm")
The problem for me is, the only way I know to add more links to the sidebar is to manually edit each page. 

Does anyone know how to edit all the pages at once?

Thanks!
 - Kodiak
use server side includes, then you can include a text file for the links in each page. changing the text file changes overypage as ech page is processed when it is requested. google SSI or server side includes, there are tons of tutorials on the web,

---

### Post by uberlinux on 2008-03-07
Thanks very much, dude!

---

