---
title: "Subversion Cannot Commit"
date: 2010-10-07
forum: Server Platforms
---

### Post by Zanthir on 2010-10-07
I just need a little help with setting up Subversion on my Ubuntu Server.
 
I set up subversion almost as described [here]("https://help.ubuntu.com/community/Subversion"), with the exceptions being 
 
1. I didn't uncomment the authorization line ```
# password-db = passwd
```I did at first but the command ```
$svn co svn://hostname/myproject myproject --username user_name
``` was returning "authorization failed."
 
2. I only set up the custom protocol (svn://). I did not set up the WebDAV, direct repository access or custom with SSL.
 
My problem is this: SVN works, and I can get the code from the repository, but I cannot commit changes. I set up two users, but subversion is not asking for their credentials. 
 
I'm guessing the command I used to try to check out my svn project was just wrong for authorization. Can anyone confirm this and possibly point me to the correct command access the subversion repository with authentication?

---

### Post by Zanthir on 2010-10-09
Problem solved. I just had to go in there an uncomment the lines that said something to the effect of "enable-read" and "enable-write", maybe something like "auth" too, and so I uncommented the authorization lines, and now everything seems to work just fine.

---

