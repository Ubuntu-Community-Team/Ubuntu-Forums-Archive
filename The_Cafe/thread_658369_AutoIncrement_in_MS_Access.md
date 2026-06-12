---
title: "AutoIncrement in MS Access"
date: 2008-01-04
forum: The Cafe
---

### Post by Black Mage on 2008-01-04
Does anyone know the SQL statement for auto-incremeting a field in Microsft Access?

The columns are ID, name, address  I'm trying to have ID auto-incremted while inserting data into the name and address columns.

---

### Post by Tundro Walker on 2008-01-04
You don't really have to do a sql statement for it ... MS Access is a GUI.  Just go into the table design view and change the field type setting of ID to AutoNumber, which defaults it to a Long Integer that auto-increments.

On the other hand, if you absolutely want to do it using a SQL statement (I guess maybe having some code use a SQL statement to create and populate a table), [this article]("http://www.thescripts.com/forum/thread467786.html") might help you.

I copied the SQL statement from the link's OP, where he had AutoNumber, and modified it for AUTOINCREMENT.  I also took out his [PK_mytab] reference ... I don't think you need to reference the table itself in the statement.  I mean, you're creating the table, and doing the fields in the parenthesis, so I'm pretty sure sql will figure out that you're setting the PK for the table you're making without having to explicitly reference it.
```

CREATE TABLE mytab 
   ([ID] AUTOINCREMENT, 
     [NAME] TEXT(255), 
     [ADDY] TEXT(255), 
    CONSTRAINT PRIMARY KEY ([ID]))
```

Hope this helps.

---

### Post by Luggy on 2008-01-04
A general SQL statement could also be
```

CREATE TABLE table(
   id INTEGER PRIMARY_KEY AUTOINCRIMENT
);

```

---

### Post by Tundro Walker on 2008-01-05
I find it funny that the OP's asking a question about SQL and MS Access in a Linux forum, in the Community Cafe / Pub section, no less.

And he STILL got the answer he was looking for!

Damn, we're good!

---

