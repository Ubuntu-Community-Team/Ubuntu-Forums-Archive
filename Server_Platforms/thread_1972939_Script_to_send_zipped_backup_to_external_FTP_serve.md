---
title: "Script to send zipped backup to external FTP server"
date: 2012-05-04
forum: Server Platforms
---

### Post by wggmx on 2012-05-04
Hey there, I was wondering if there was a way to automatically send zipped backup files to a remote web server?

---

### Post by Lars Noodén on 2012-05-04
There is a way if you use SSH (scp or sftp), usually best if you use keys for authentication.  If you load the key into an agent, then you can let the script run unattended and it will still be able to log in. 

Here is a good place to start with keys:
[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

---

### Post by wggmx on 2012-05-04
Could you be a bit more specific as to how I would setup such a script.

---

### Post by Lars Noodén on 2012-05-04
To start with, I would use [rsync](https://help.ubuntu.com/community/rsync) for transferring large files.  That way, if the process is interrupted, it is easy to resume without having to start over from the beginning.  Nowadays, [rsync](http://manpages.ubuntu.com/manpages/precise/en/man1/rsync.1.html) uses SSH by default.

```

rsync /some/dir/backupfile.zip wggmx@remotehost.example.org:/someother/dir/

```

Once that is working, you can set up keys for SSH.  You'll find many tutorials and HowTos on the net.  The main steps are 1) generate a pair of keys, 2) put the public key into the file [font=Courier New]~/.ssh/authorized_keys[/font] on the remote server.  All methods will use [ssh-keygen](http://manpages.ubuntu.com/manpages/precise/en/man1/ssh-keygen.1.html) to create a key pair.

```

ssh-keygen -b 2048 -t rsa -f ~/.ssh/backup_rsa -C "Created on $(date +'%F') for wggmx"

```

That will create a private key ([font=Courier New]backup_rsa[/font]) and a corresponding public key ([font=Courier New]backup_rsa.pub[/font]) in the directory [font=Courier New]~/.ssh[/font].  It's the public key that you need to transfer to the remote machine.

You can use [ssh-copy-id](http://manpages.ubuntu.com/manpages/precise/en/man1/ssh-copy-id.1.html) to copy the keys.  Or you can cut-and-paste, if you are careful with the line breaks.

```

ssh-copy-id -i ~/.ssh/backup_rsa wggmx@remotehost.example.org

```

Make sure you can log in with the key.

```

ssh -i ~/.ssh/backup_rsa wggmx@remotehost.example.org

```

Then test the combination.

```

rsync -e "ssh -i ~/.ssh/backup_rsa wggmx@remotehost.example.org" /some/dir/backupfile.zip wggmx@remotehost.example.org:/someother/dir/

```

Once that's working, you can include it in your script.

---

### Post by elico on 2012-05-04
this is a nice script that will send the file you will add to the command such as
```
/scripts/sendftp.sh /backup/1.zip
```
just change the user password domain and ip
it will also create a log file.
```
#/bin/bash
# $1 is the file name
# usage: this_script  <filename>
IP_address="xx.xxx.xx.xx"
username="username"
domain=my.ftp.domain
password=password

echo "
 verbose
 open $IP_address
 USER $username $password
 put $1
 bye
" | ftp -n > ftp_$$.log
```

---

### Post by Lars Noodén on 2012-05-05
elico, that can be made safe by swapping out [FTP](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp) for [SFTP](http://olex.openlogic.com/wazi/2011/stop-using-ftp-how-to-transfer-files-securely/)

```

echo "put $1" | sftp -b - -i ~/.ssh/backup_rsa wggmx@remotehost.example.org > sftp_$$.log

```

---

### Post by codemaniac on 2012-05-05
> **elico said:**
> this is a nice script that will send the file you will add to the command such as
```
/scripts/sendftp.sh /backup/1.zip
```
just change the user password domain and ip
it will also create a log file.
```
#/bin/bash
# $1 is the file name
# usage: this_script  <filename>
IP_address="xx.xxx.xx.xx"
username="username"
domain=my.ftp.domain
password=password

echo "
 verbose
 open $IP_address
 USER $username $password
 put $1
 bye
" | ftp -n > ftp_$$.log
```

There is a security issue associated with the script , you would never want to show off your user credentials in a plain text file .
Rather key based aunthentication as mentioned above by Lars Noodén is the more secure option to be adopted .
Nice explanation Lars Noodén .+1

---

