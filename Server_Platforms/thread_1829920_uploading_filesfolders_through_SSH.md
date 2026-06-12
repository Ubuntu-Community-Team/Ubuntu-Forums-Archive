---
title: "uploading files/folders through SSH?"
date: 2011-08-21
forum: Server Platforms
---

### Post by Heeter on 2011-08-21
Hi all,

I am done setting up an ubuntu server on Amazon Cloud Service.

I connect to it via SSH.

I would like to upload my website into the /var/www folder through SSH. I would like to upload a complete folder's worth.

How would I go about doing that?

Thanks


Heeter

---

### Post by dinu90 on 2011-08-21
You can use WinSCP from your PC. Or if you are uploading from a Linux server and have command line access then you can do it like this:
```

scp -R -P PORT /path/to/files/* username@destinationIP:/path/to/destination/

```

[**java tutorials**]("http://www.java-forums.org/java-tutorial/")

---

### Post by Lampi on 2011-08-21
thanks dinu90,

will try scp myself, up til now I used rsync:

```
rsync -avPz -e ssh /path/to/files username@destinationIP:/path/to/destination/
```

but If the remote has not rsync daemon this won't work -> use scp

---

### Post by Lars Noodén on 2011-08-21
SFTP is easy to use, too.  I would recommend it over scp.

---

### Post by Heeter on 2011-08-21
Hey Guys, I am getting this error

```


root@domU-12-31-39-09-3E-A4:/var/www# scp -R -P PORT /home/user/website/* root@ec2-174-129-44-95.compute-1.amazonaws.com:/var/www/
scp: illegal option -- R
usage: scp [-12346BCpqrv] [-c cipher] [-F ssh_config] [-i identity_file]
           [-l limit] [-o ssh_option] [-P port] [-S program]
           [[user@]host1:]file1 ... [[user@]host2:]file2
root@domU-12-31-39-09-3E-A4:/var/www# 

```

Heeter

---

### Post by Hack.The.Pow. on 2011-08-21
> **Heeter said:**
> Hey Guys, I am getting this error

```


root@domU-12-31-39-09-3E-A4:/var/www# scp -R -P PORT /home/user/website/* root@ec2-174-129-44-95.compute-1.amazonaws.com:/var/www/
scp: illegal option -- R
usage: scp [-12346BCpqrv] [-c cipher] [-F ssh_config] [-i identity_file]
           [-l limit] [-o ssh_option] [-P port] [-S program]
           [[user@]host1:]file1 ... [[user@]host2:]file2
root@domU-12-31-39-09-3E-A4:/var/www# 

```

Heeter

Try this.

```
scp -r -P PORT /var/www root@ec2-174-129-44-95.compute-1.amazonaws.com:/var/www/
```

That is assuming your web folder is at /var/www on your local machine(not amazon server)

---

