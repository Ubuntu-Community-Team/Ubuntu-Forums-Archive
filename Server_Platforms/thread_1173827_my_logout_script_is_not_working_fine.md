---
title: "my logout script is not working fine"
date: 2009-05-30
forum: Server Platforms
---

### Post by Eswarjava on 2009-05-30
Hi All,

Could you please any one help me to solve my issues.

i need to logout server
if the time ==6 pm 

This is my script it is working fine when user is logged in as user 
but if the user is logged as root
it is not able to logout the entire terminal.


        NAMEONE=$USERS
        echo $NAMEONE
        if [ "$NAMEONE" = "root" ]
        then
        echo "your  in the root"
        sudo pkill -KILL -u root
        #skill -KILL -v /dev/pts/*

        else
         sudo pkill -KILL -u $NAMEONE

        fi



I want to logout the enter server if the time is 6:00 pm
but server has renaming running not shutdown.

Regards,
Eswar.G

---

