---
title: "shell account on Web server: best way to sync a folder?"
date: 2011-07-09
forum: The Cafe
---

### Post by keithpeter on 2011-07-09
Hello All

Its summer so I can play for a bit as teaching has finished.

I've decided to explore using a Web hosting package with shell access to a linux server. 

I want to syncronise the web docs directory on the server with a directory on this PC (actually in my dropbox folder so the site files are backed up and available on my laptop as well).

I tried mounting the remote server using ssfs, no deal. gvfs works under Gigolo, but then I don't get synch, in the sense that I have to remember which files I changed. I tried rsynch but had permission issues that meant I had to log into ssh and chmod the docs directory on the server.

Finally, I've hit on using lftp over sftp. The script I'm using is shown below...

```
#!/bin/sh

HOST=some.shell.account.server.co.uk
USER=myshelluser
PASS=myshellpassword

echo "Starting to sftp..."

lftp -u ${USER},${PASS} sftp://${HOST} <<EOF
cd /path/to/html/docs/directory
mirror -e -R /home/mylocaluser/mywebsitefiles
chmod -R 777 /path/to/html/docs/directory
bye
EOF

echo "done"
```

Is this sensible? Anyone got a better idea? I found it at [http://www.unix.com/302110934-post24.html](http://www.unix.com/302110934-post24.html)

---

### Post by CharlesA on 2011-07-09
rsync ftw.

You can set it up to use keys so you don't have to enter your password.

---

### Post by undecim on 2011-07-09
> **CharlesA said:**
> rsync ftw.

You can set it up to use keys so you don't have to enter your password.

This.

EDIT: P.S: If you're looking for a web host, I can recommend a great one.

---

### Post by keithpeter on 2011-07-10
Hello CharlesA and Undecim

Yes, I tried rsync, but I also had problems with the 777 permissions not being preserved, so I was logging in with ssh and chmoding directories each time I synchronised. 

I'll read the howtos again and have another go.

PS: I have located a uk based hosting provider, thanks

---

### Post by wizard10000 on 2011-07-10
> **keithpeter said:**
> Hello CharlesA and Undecim

Yes, I tried rsync, but I also had problems with the 777 permissions not being preserved, so I was logging in with ssh and chmoding directories each time I synchronised. 

I'll read the howtos again and have another go.

PS: I have located a uk based hosting provider, thanks

As others have said, rsync.  Nothing stopping you from doing a recursive chown or chmod in your script once the files are on your end, but rsync has switches to preserve permissions.  rsync -a should get you most of what you want.

---

### Post by CharlesA on 2011-07-10
Hmm, nothing should be stopping it from preserving the permissions unless you aren't using -a.

Are you rsyncing the files to the same user account?

---

### Post by keithpeter on 2011-07-10
> **CharlesA said:**
> Hmm, nothing should be stopping it from preserving the permissions unless you aren't using -a.

Are you rsyncing the files to the same user account?

Nope, and even if I used the same user *name* on the local pc, the user id would likely be different as the server is redhat 6 and the local machine is Debian Squeeze, but I will investigate that.

I'd like to keep the site files in a dropbox folder so that I can update the site from my laptop as well :twisted:

[http://www.cyberciti.biz/tips/linux-use-rsync-transfer-mirror-files-directories.html](http://www.cyberciti.biz/tips/linux-use-rsync-transfer-mirror-files-directories.html)

is the guide I followed.

---

### Post by CharlesA on 2011-07-10
Valid point.

It should still not give you any problems, even if it changed the owner - you could just chown it back when it's back on the server.

---

