---
title: "Mailman shell access"
date: 2012-03-19
forum: Server Platforms
---

### Post by Meanmachine187 on 2012-03-19
Hi all,

I'd like to create a little shell script that runs every night and that adds or deletes email addresses to a specific mailinglist.

Is there a possibility to add/delete members to a mailinglist via shell? I only did this using the web interface.

Thanks and best wishes,

Dirk

---

### Post by SeijiSensei on 2012-03-19
I haven't used mailman for a long time, so I don't know if this will work.  The older mailing list manager called majordomo just puts the subscribed addresses into a text file which is referenced via a email alias.  If mailman uses the same approach, then adding or deleting subscribers is as simple as adding or deleting them from the text file.

If it uses a database of some kind to store subscribers, then you might be able to automate requests via email.  Again, using majordomo as my example, you can subscribe or remove someone by sending a command like
```
approve PASSWORD [un]subscribe mailing-list someone@example.com
```
to the administrator's account.  I'd guess mailman enables that type of management as well as via the web interface.

---

### Post by Meanmachine187 on 2012-03-19
Hi SeijiSensi,

thanks for your Response. I'll try your answer and hopefully it works ;)

Thanks and best wishes,

Dirk

---

