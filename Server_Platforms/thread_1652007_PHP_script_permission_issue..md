---
title: "PHP script permission issue."
date: 2010-12-24
forum: Server Platforms
---

### Post by Guruprasad on 2010-12-24
I have Apache2 server with PHP.

I want a php script to create new directories at a location which do not have access permission for www-data.

Will there be any security issue id I give access permission for www-data? Or can I run php script as some other user than the default www-data?

---

### Post by windependence on 2010-12-24
You can do this in PHP but I'm not sure you would want to for security reasons. Can you give us a bit more info as to what exactly you are trying to do and I may have some more suggestions.
 
-Tim

---

### Post by Guruprasad on 2010-12-24
I have a folder "/media/Disk1/Works" with "bcstaff" as owner and group with permision as 770.

I want the php script to create folder like "/media/Disk1/Works/SomeWork" but it is not able to create because "www-data" which is default user of Apache and PHP do not have write permision for "/media/Disk1/Works"

How can I do this without give write access of "/media/Disk1/Works" to "www-data"?

---

### Post by iponeverything on 2010-12-24
You can have the script call su and setup /etc/sudoers for only one specific command for that user. So for instance the specific command can be a script that only does one thing. You can have it so that sudo does not require a password for that user to run that command.

```
su - some-other-user <command>
```

---

