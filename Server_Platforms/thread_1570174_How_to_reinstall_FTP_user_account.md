---
title: "How to reinstall FTP user account?"
date: 2010-09-07
forum: Server Platforms
---

### Post by rcayea on 2010-09-07
Hey everyone,

I recently setup an FTP server for my wife, Kelly, and I. I made an error or two when I tried to set various permissions. 

I decided ok, fine, I will just start fresh. I rm our two accounts. However, I go to re-add Kelly's account with useradd Kelly and I am told that the account still exist. I thought I deleted it?

So, how do I go about wiping the slate clean, so-to-speak to start over, without having to go through the whole software reinstall?

Thanks,
Randy

---

### Post by rcayea on 2010-09-08
Bump. Anyone help please?

---

### Post by gobbledigook on 2010-09-08
```
rmuser kelly
```

will remove the user kelly :) 


documentation on setting up [ftp server]("https://help.ubuntu.com/10.04/serverguide/C/ftp-server.html")

---

### Post by rcayea on 2010-09-08
Great. Thanks for the help. 

Randy

---

