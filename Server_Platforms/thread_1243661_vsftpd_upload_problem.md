---
title: "vsftpd upload problem"
date: 2009-08-18
forum: Server Platforms
---

### Post by brunoskrebs on 2009-08-18
Hi people,

Im having this trouble with vsftpd that I can't get the uploaded file with the right read and write permissions.

I have tried all kind of combinations of 

```

#
# Default umask for local users is 077. You may wish to change this to 022,
# if your users expect that (022 is used by most other ftpd's)
file_open_mode=0664
local_umask=077

```

like local_umask=002 local_umask=022 local_umask=077
file_open_mode=0777 and etc...

but I can't the correct configuration.

What I want is to upload the file with the 0777 permissions.

I have a lot of users sharing a folder, and all that users should be able to read write delete the files and folders inside this folder.

What should I do????

Oh by the way the public folder that they are sharing is mounted using --bind option in their homes...

Thanks in advance.
Bruno Krebs

---

### Post by hessiess on 2009-08-18
> **brunoskrebs said:**
> Hi people,

Im having this trouble with vsftpd that I can't get the uploaded file with the right read and write permissions.

I have tried all kind of combinations of 

```

#
# Default umask for local users is 077. You may wish to change this to 022,
# if your users expect that (022 is used by most other ftpd's)
file_open_mode=0664
local_umask=077

```

like local_umask=002 local_umask=022 local_umask=077
file_open_mode=0777 and etc...

but I can't the correct configuration.

What I want is to upload the file with the 0777 permissions.

I have a lot of users sharing a folder, and all that users should be able to read write delete the files and folders inside this folder.

What should I do????

Oh by the way the public folder that they are sharing is mounted using --bind option in their homes...

Thanks in advance.
Bruno Krebs

I dont know how to fix the problem, but what you describe would be a major security risk and a single point of failure. Each user should have there own user space which cannot be read/written by any other user. If your users are working on a collaborative project, use a VCS like Subversion so they cannot delete/damage each outers files.

---

### Post by Bachstelze on 2009-08-18
```
local_umask=000
```

No need for file_open_mode.

---

### Post by brunoskrebs on 2009-08-18
Ok this is weird.

I do remember to make this attempt before, but now it worked.

Anyway thank you very much HymnToLife.

Oh and only for the record, every single user does have a private directory. But I needed a public folder so everybody could use it with all the permissions. That's why I have created this shared folder. And I'm using ftp only because I wanted to be able to open/save documents directly on it from microsoft word and excel..

Thanks again for the quick response.

---

