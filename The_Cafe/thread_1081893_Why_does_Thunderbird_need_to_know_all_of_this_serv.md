---
title: "Why does Thunderbird need to know all of this server stuff?"
date: 2009-02-27
forum: The Cafe
---

### Post by NintendoTogepi on 2009-02-27
I don't know the answer...shouldn't my email addresses be enough?

---

### Post by Ocxic on 2009-02-27
Every e-mail client/program needs to know that server stuff. 

Without it it's like mailing a letter without having a post office, or mailman.
You may have the mailing address but no mailbox to put it in.

---

### Post by swoll1980 on 2009-02-27
> **NintendoTogepi said:**
> I don't know the answer...shouldn't my email addresses be enough?

mail clients need to know the server settings to get the mail. Who's your provider?

---

### Post by cb951303 on 2009-02-27
actually op is right. mail servers and port configurations can be guessed from the mail address. outlook had such an option if I remember correctly.

EDIT: But it's not always possible. So that's why thunderbird and all other mail clients ask for it :popcorn:

---

### Post by Vince4Amy on 2009-02-27
Imagine how bloated it would be if it stored every detail for every Mail Provider.

---

### Post by 3rdalbum on 2009-02-27
Trust me, your ISP will be able to tell you what settings to use. It's probably on their Support page under "How to set up your e-mail account".

---

### Post by koenn on 2009-02-27
> **Vince4Amy said:**
> Imagine how bloated it would be if it stored every detail for every Mail Provider.

it could assume default service ports for smtp, pop3 or imap, and query DNS for smtp servers in the domain shown in the email address.

you'd still have to know the address of the pop/imap servers (assuming its different from the smtp server), and mailbox credentials, though.

---

### Post by geoken on 2009-02-27
> **Vince4Amy said:**
> Imagine how bloated it would be if it stored every detail for every Mail Provider.

I'm pretty sure the settings for the top 5 or 10 could fit into a <5kb text file.

With that said, it already has a wizard for some of the common ones in TB3. For example, gmail only requires your address and whether you want pop or imap.

---

