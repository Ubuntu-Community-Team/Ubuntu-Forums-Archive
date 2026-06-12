---
title: "Did a bone-headed thing need help with a chown problem"
date: 2016-11-16
forum: Server Platforms
---

### Post by nhdls1-matthew-8d0zeq on 2016-11-16
I was setting up a server (acutally a migration) and was logged in a root.   Well as we all know if you are root you are supposed to be on your top game.  I wasn't.

While sitting in /var/vmail I input a chown of:  chown -R vmail:vmail .* and it did just that.  It changed everything in vmail and /var to vmail ownership. 

Do I have to go in and manually chown everything back or is there a command I can use to undummy myself?  Like unchown would be nice.  

Please let me know if I am moosed.  Thanks.

---

### Post by QIII on 2016-11-16
Hello!

Does the server you migrated from still exist?

(Moved to Server Platforms)

---

### Post by SeijiSensei on 2016-11-17
```

$ sudo su
# cd /var/mail
# for x in *
# do
# chown $x $x
# done
# exit

```
This extracts each filename from the directory listing and changes the ownership of that file to the identical username.

---

