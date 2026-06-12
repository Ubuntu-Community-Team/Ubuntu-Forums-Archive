---
title: "horde setup flushed mysql"
date: 2008-02-14
forum: Server Platforms
---

### Post by foresttb on 2008-02-14
hello...
I have tried to install horde webmail to my webserver..
I followsd the instructions carefully , and i inserted the 
create.mysql.sql in my sql server..
This script has deleted all my databases , and created a root with no rights..Can anyone help me how to roll these changes back?

```

USE mysql;

REPLACE INTO user (host, user, password)
    VALUES (
        'localhost',
        'root',
-- IMPORTANT: Change this password!
        PASSWORD('mypassword')
);

REPLACE INTO db (host, db, user, select_priv, insert_priv, update_priv,
                 delete_priv, create_priv, drop_priv, index_priv)
    VALUES (
        'localhost',
        'root',
        'mypassword',
        'Y', 'Y', 'Y', 'Y',
        'Y', 'Y', 'Y'
);
```

---

