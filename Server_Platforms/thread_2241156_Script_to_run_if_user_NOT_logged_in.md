---
title: "Script to run if user NOT logged in"
date: 2014-08-24
forum: Server Platforms
---

### Post by johnathan3 on 2014-08-24
I am setting up Server 14.04 and want to run a script from cron every 30 minutes based on if a specific user is NOT logged into the system.
This should also work if the user was switched to from another user logged in.


any help is appreciated.

---

### Post by volkswagner on 2014-08-24
The who command should help you here.

I logged in as user1, then switched to root, then to user2. All instances
the who command returned user1 login time and ip address.

---

### Post by johnathan3 on 2014-08-24
Thanks, this lead got me to the code that works; 
Basically if "who | grep Username " return a result (greater that /dev/null) then do nothing, else execute

#!/bin/bash
if who | grep 'UserName' > /dev/null;
        then
                echo "UserName Found"
        else
                echo "UserName Not Found Executing command"
fi

---

