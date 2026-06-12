---
title: "cannot access shared folders on win ad server"
date: 2009-10-02
forum: Security
---

### Post by keevill on 2009-10-02
After installing Likewise Open on my Ubuntu 9.0.4 client machine, I am able to successfully login to my Win2003 Active Directory Server. This machine also acts as a file server.
Although, I can see the shared folders from the Ubuntu client, I am unable to access them.
I get the 'failed to mount windows share'.

Following advice on another thread I did the following.
sudo visudo
changed the last lines of the etc/sudoers to the lines below.


# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
%MYDOMAIN.local\\linux ALL=(ALL) ALL

Finally, I made a group called 'linux' on the Ad server and added users to it, including my own login name.
But the trouble still remains.
Can anyone help to troubleshoot this ?

---

