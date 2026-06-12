---
title: "Version 9.x LTS and home encryption?"
date: 2009-06-25
forum: Server Platforms
---

### Post by mevans336 on 2009-06-25
Hello Everyone,

I have two questions that I hope are simple!

First, I am contemplating a migration of all our servers from CentOS 5.3 to Ubuntu Server 9.04, but I would like to know when the next LTS version of Ubuntu Server is planned for release? I'd rather wait for that if it will be reasonably soon.

Second, the home directory encryption feature and the /etc versioning is what has me drooling, but I have a question about how the /home directory encryption works.

We accept plain text files for clients who have local PAM accounts and home directories in /home, just like a standard user. If I utilize full home directory encryption feature of 9.04, are those files accessible to that user account via FTP? What about to the root account? We process these files automatically each night with an account tied to the same home directory (different UIDs, but members of the same unique group) so is there a way to allow that user account access to the encrypted folder for file processing?

Thanks!

---

### Post by Cheesemill on 2009-06-25
LTS releases are every 2 years so the next one should be 10.04

---

### Post by bigbearomaha on 2009-06-26
I am just curious as to why you are compelled to abandon a CentOS 5.3 server just like that?

you are able to use encryption on directories such as home in Cent as you can in buntu server.

I am not trying to dissuade you from switching, I am merely curious as to what what cause such a change?

Big Bear

---

