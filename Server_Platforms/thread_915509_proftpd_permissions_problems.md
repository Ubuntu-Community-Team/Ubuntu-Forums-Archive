---
title: "proftpd permissions problems"
date: 2008-09-09
forum: Server Platforms
---

### Post by not28 on 2008-09-09
Hello people.

I'm testing an Ubuntu server that will be hosting a web site. I currently use ssh/scp for everything, but I'd like to set up an FTP service to make things a bit easier.

I currently have proftpd installed. What I want to do is enable a user (I guess this is a Unix-user, one who has been created by me on the system) to log in with their credentials and access their home directory. So essentially, if I log into /home/nick, I should be able to edit/upload/download anything under that directory recursively.

I've only been able to fix this halfway. I can FTP into my home directory and I have read/write access to that directory, but no subdirectories under that. I keep getting a permission denied error. Can anybody help me out with this? I'd be willing to post my proftpd.conf file if necessary.

---

### Post by not28 on 2008-09-09
Nevermind, I fixed the FTP problem using chown. However, now when I try to upload something it seems to disconnect/reconnect me. Any idea why?

---

### Post by cariboo on 2008-09-09
You shouldn't have to do anything, just create the user on your server and then access it remotely using the user you just created. the only thing I could suggest is to change this in your /etc/proftpd/proftpd.conf:

```
# Use this to jail all users in their homes 
# DefaultRoot			~

```

Uncomment Defaultroot, that way they can't get to any other directories but their own.

Jim

---

