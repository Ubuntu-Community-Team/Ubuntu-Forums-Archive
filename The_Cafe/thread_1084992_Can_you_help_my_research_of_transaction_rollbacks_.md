---
title: "Can you help my research of transaction rollbacks in DAO/DTO?"
date: 2009-03-02
forum: The Cafe
---

### Post by Maheriano on 2009-03-02
I got to research this for work, we're implementing a new Data Abstraction Layer (DAL) with multiple Data Access Objects (DAO) and Data Transfer Objects (DTO). I need any information you have on how the transactions would get rolled back in this environment and what we would need to consider in implementing it. I don't expect to get spoonfed, any information which leads me to more defined searching would be great. :KS

EDIT - This is in a Windows environment.

---

### Post by Trail on 2009-03-03
Euhm. All I know on this matter is from using for a little bit the 'Hibernate' framework on Java, for a MySQL DB access.

Basically you would mark an SQL query as part of a transaction and you could either rollback manually, or it would happen automatically on an uncaught HibernateException. I guess it's only the DAO that has to worry about rollbacks, and not the DTO itself.

I don't know what exactly you are looking for, or how you're implementing it, but you could maybe get some ideas from how Hibernate does it.

---

### Post by Maheriano on 2009-03-03
Okay, cool. I see that and Spring use it quite effectively. Any ideas how it would handle the Business Logic Layer (BLL) creating 2 separate updates and rolling back the first one if the second one fails? Both transactions would be passed to the DAO or even 2 separate DAO and they both have to roll back if either one fails. That's the hard part.

---

### Post by cdekter on 2009-03-04
This probably belongs in the Programming Talk forum, or a Java/Hibernate forum for that matter.

---

### Post by Maheriano on 2009-03-04
> **cdekter said:**
> This probably belongs in the Programming Talk forum, or a Java/Hibernate forum for that matter.

It's being written in .NET, I'm just looking for ideas how other people have overcome it.

So far what I've decided is that there needs to be a common layer after the business logic and before the data access object. I'll call this the data management layer and it'll hoard all the SQL commands into one final step and only run the commit() if they were all successful. Otherwise it'll roll back. But I don't think this can be done without a common layer because each DTO that's created then has its own DAO so it needs to come back to a common meeting ground to be controlled.

---

### Post by Trail on 2009-03-05
I've done similar things on PL/SQL by using Savepoints, and rolling back on an update error. I didn't have to use Hibernate for anything advanced, so I wouldn't know, but a quick google search shows that it does not support savepoints. Then again, Oracle operates at a lower level than that, and I am not sure how you could emulate that (they maintain a log of actions per transaction, with savepoints being points in the log that you can go back to if necessary).

What you describe in your last post is pretty much that, in a higher level. And I can't think of a different implementation at the moment.

---

### Post by Maheriano on 2009-03-05
Guys, I'm not using Hibernate, I was just looking for different examples of how it was managed in different environments. We're actually discussing it right now though, taking a 5 minute break before discussing it some more. I got all the information I needed, thanks!

---

