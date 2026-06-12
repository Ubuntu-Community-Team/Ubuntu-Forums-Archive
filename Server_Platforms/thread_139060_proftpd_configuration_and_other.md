---
title: "proftpd configuration and other"
date: 2006-03-03
forum: Server Platforms
---

### Post by wizzkid on 2006-03-03
hi! I just setup proftpd. its running and my user was able to login. but the problem was when the user transfers a files to ftp server the rror msg appears it says:  "Could not change local directory to /home/xxx/filename.doc: Not a directory. "

Here's my /etc/proftpd.conf
[http://www.i-bsc.com/noel/proftpdconf.txt](http://www.i-bsc.com/noel/proftpdconf.txt)

Also, when I add new user thru terminal, adduser, it has been added, but, when I check  on SYSTEM > Administration > Users and Group. the user is there, but it also added the username i used for the user as group. how can I add user then specify which group he is belong? i want to add users voa terminal. 

Also what is the use of shell? /bin/bash or /bin/sh.. how would i know which to use and when to use?

How can I add user that had ftp, mail, smb as a group? :) 

Thanks.

---

### Post by wizzkid on 2006-03-03
i have solve the problem of the error.. but still i need some input from my other questions.

when I add new user thru terminal, adduser, it has been added, but, when I check on SYSTEM > Administration > Users and Group. the user is there, but it also added the username i used for the user as group. how can I add user then specify which group he is belong? i want to add users voa terminal.

Also what is the use of shell? /bin/bash or /bin/sh.. how would i know which to use and when to use?

also, my main user id, the ones i used to login was able to login on my ftp. can I disable my username from accessing the ftp, coz it access the whole system and i think its very risky.

How can I add user that had ftp, mail, smb as a group?

---

