---
title: "Need help loading phpBB3"
date: 2011-01-05
forum: Server Platforms
---

### Post by Nova 107 on 2011-01-05
I'm trying to put phpBB3 on my server to add forums to my website, but in set up I need the information for my database. I have mySQL installed but I have no idea how to create a database (or if I already have one), and all the tutorials I've seen are not straight to the point and beat around the bush ignoring the actual question. Help is greatly appriciated.

---

### Post by aceofspades686 on 2011-01-05
When you install MySQL, it asks you input a root user password.  If you didn't then you may have a root account without a password (VERY BAD).

Try this:
```

mysql -u root

```

If it allows you to login, then you have a unprotected root account and should add a password to it.  If you do have a password on the account, you can log in to it with:
```

mysql -u root -p

```
and it will prompt you for the password.  Once at the "mysql>" prompt, you'll be able to enter in SQL commands, creating users, databases, etc.  My personal suggestion for a first step is to create an "administrator" account so that you're not using the root account to run commands, but this would require learning about database permissions and how to set them up which is far too lengthy for a forum post to cover.

---

### Post by Nova 107 on 2011-01-05
that worked, thanks! now for the rest of it...

---

