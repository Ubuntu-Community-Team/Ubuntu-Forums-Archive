---
title: "Set permissions to full &quot;webpage&quot; directory"
date: 2007-04-09
forum: Server Platforms
---

### Post by gargo2000 on 2007-04-09
I've spent most of the night trying to get a web server up and running.  I'm using apache and now have the web page up and running (in transition to moving to ubuntu).  Webpage seems to be working, but difficult to get all the permissions correct.  I believe it's correct, but trying to set ever file and directory is a pain.  Is there a faster way to say, give viewing access to all?  On the flip side.  Yes you can see most of my pages, some still say "forbidden" and all my pictures do not work at all.

Let me know of any ideas that could help.  I could not find anything on searches for permissions on directories/subdirectories/files for faster permission setting.

Thanks!

Gargo

---

### Post by rsermilik on 2007-04-09
man chown is your friend...

If you as root do
chown -R www:www /srv
then everything under and including /srv will be owned by user www and group www.

regards

---

### Post by gargo2000 on 2007-04-09
Fantastic!  Pictures now work.  I'm assuming the rest of it is too.  Thank you very much!!!

Gargo

---

