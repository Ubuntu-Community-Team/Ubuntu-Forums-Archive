---
title: "SFTP and UMASK"
date: 2010-03-12
forum: Server Platforms
---

### Post by blindenvy on 2010-03-12
_The problem: _
I have a user that has been uploading files via SFTP into a directory called:  /shared/files

The user is uploading the files via Filezilla and all the files have the following permissions: 
-rw-r--r--, I think this is because the files are created on a windows machine, so those would be the default permissions coming from a windows box.

To test this, I created a file on my osx machine and did a chmod 777 on it and then uploaded that file to the server via FileZilla, its maintained its permissions. I used the same users login information.

_What I desire:_
I would like the files uploaded from the windows machine to have -rwxrwx--- permissions. (full permission to the owner and the group). How can I go about doing this?

_What I have tried:_
At first I thought umask was the answer.
I tried creating a wrapper like the one suggested[on this site.]("http://jeff.robbins.ws/articles/setting-the-umask-for-sftp-transactions") It seemed to have no affect. I also tried editing /etc/profile, ~/.bashrc, ~/.bash_profile, ~/.profile to include umask. No success with any of those either.

---

