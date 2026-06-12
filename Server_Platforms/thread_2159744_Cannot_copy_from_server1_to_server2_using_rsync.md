---
title: "Cannot copy from server1 to server2 using rsync"
date: 2013-07-04
forum: Server Platforms
---

### Post by alfirdaous on 2013-07-04
Hello everybody,

I tried to copy items from server1 et server2, but it failed:

```

rsync -avrR --log-file=/var/log/rsync.log Videos USER2@IP_SERVER2:home/USER2/www/
ssh: connect to host IP_SERVEUR2 port 22: Connection timed out
rsync: connection unexpectedly closed (0 bytes received so far) [sender]
rsync error: unexplained error (code 255) at io.c(605) [sender=3.0.9]

```

both ssh are working:

```

ssh user1@ip_serveur1 -p port
ssh user2@ip_serveur2

```

using different port on server1

thx in advance

---

### Post by SlugSlug on 2013-07-04
should it not be


rsync -avrR --log-file=/var/log/rsync.log Videos USER2@IP_SERVER2:/home/USER2/www/
or
rsync -avrR --log-file=/var/log/rsync.log Videos USER2@IP_SERVER2:www/

---

### Post by alfirdaous on 2013-07-04
I tried this:

```

rsync -avrR --log-file=/var/log/rsync.log Videos USER2@IP_SERVER2:www/

```

still the same error message

---

### Post by nerdtron on 2013-07-04
Does rsync use the same port as ssh?
Specify the ssh port for rsync.

```


rsync -avrR -e 'ssh -p 5000' /home/source user@IPadd:/path/destination 
```

Don't forget the -e option

---

### Post by alfirdaous on 2013-07-04
I tried to another server, it works, SSH is using port 22, I think it is a ssh key problem

can I delete this key from local, generate a new key and re-send to my 3 servers??

---

### Post by nerdtron on 2013-07-05
Ah keys...It's safe to delete them to go ahead.

---

### Post by alfirdaous on 2013-07-05
should I delete all files in .ssh in both local and remote servers

---

### Post by nerdtron on 2013-07-05
How to you copy using rsync?
If you're login into you're local machine then copy to the remote destination, delete the key on local.

BTW don't deleted the keys, just rename them so that at least you have a backup of the keys.

---

### Post by alfirdaous on 2013-07-05
I am transfering from a remote server to another remote server :)

---

### Post by SlugSlug on 2013-07-05
edit nvm didn't read above posts

---

### Post by SlugSlug on 2013-07-05
Are you sure the paths are correct?

command should be 
rsync -avrR --log-file=/var/log/rsync.log Videos USER2@IP_SERVER2:www/

---

### Post by alfirdaous on 2013-07-05
> **SlugSlug said:**
> Are you sure the paths are correct?

command should be 
rsync -avrR --log-file=/var/log/rsync.log Videos USER2@IP_SERVER2:www/

Yes correct, I've done it with another server, it works
> **genialrasel said:**
> I am new here.......... welcome

[rasel]("http://rasels.webs.com")

Welcome

---

