---
title: "Where is my authorized_keys file? Ubuntu Server 12.04.1 LTS"
date: 2012-10-12
forum: Security
---

### Post by wh33t on 2012-10-12
Hey Forums,

I'm trying to get some automatic rsync backups happening from my webserver. I have my public key set up on my webserver correctly now I just want to install my private key on my back up machine which is running Ubu Server 12.04.1 LTS and I can't seem to find my authorized_keys file. All of the guides on the net tell me that it should be in my home directory at ~/.ssh/authorized_keys but it doesn't appear that I have that directory or file in existence. 

Does that mean I should just make the .ssh dir and the authorized_keys file or does that mean that SSH in my system is configured differently?

Edit: I followed this guide ([http://www.debian-administration.org/articles/152](http://www.debian-administration.org/articles/152)) and it seems to be working

---

### Post by Cheesemill on 2012-10-12
.ssh is a hidden folder, you can use either 'ls -a' in a terminal or hit CTRL+H in nautilus to show hidden files.

The easiest way to copy your key to a remote host is to use the ssh-copy-id command:
```
ssh-copy-id user@host
```

---

### Post by wh33t on 2012-10-12
> **Cheesemill said:**
> .ssh is a hidden folder, you can use either 'ls -a' in a terminal or hit CTRL+H in nautilus to show hidden files.

The easiest way to copy your key to a remote host is to use the ssh-copy-id command:
```
ssh-copy-id user@host
```

That's exactly what I ended up doing :D Thank you.

---

