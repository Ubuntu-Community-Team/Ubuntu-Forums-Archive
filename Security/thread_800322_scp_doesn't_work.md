---
title: "scp doesn't work"
date: 2008-05-19
forum: Security
---

### Post by myle on 2008-05-19
After the apply of the the patches for the new vulnerability which has been detected, the scp stopped working even though ssh works flawlessly (or at least, it looks like this).
scp requests for a password, connects to the servers and instead of uploading the specified file, prints the first line of the cal which is the month and the year (cal runs every time I log in the system).
How can I fix it?

---

### Post by bikeboy on 2008-05-19
Is your new public key in the authorised_keys file of the remote user you're trying to copy to? You could also try temporarily setting *PasswordAuthentication yes* in the /etc/ssh/sshd_config file of the ssh server to see if it's a key problem or not. You'll need to restart the sshd service after changing settings.

I realise these are basic things you've probably checked (since you say ssh works), but they're worth asking.

---

### Post by kevdog on 2008-05-20
For the life of me I can't get scp to work with filenames or directories with spaces in their names!!! SSH works but not scp. Ive tried /, double quotes, single quotes, combinations, %20, nothing seems to work.

---

### Post by Dr Small on 2008-05-20
> **kevdog said:**
> For the life of me I can't get scp to work with filenames or directories with spaces in their names!!! SSH works but not scp. Ive tried /, double quotes, single quotes, combinations, %20, nothing seems to work.
I had this problem before. I think I ended up by trying:
```
scp -r "/path/to/broken\ directory/" host:
```

---

### Post by myle on 2008-05-20
Still doesn't work. I have tried "PasswordAuthentication yes" with no obvious result after "/etc/init.d/sshd restart". scp still doesn't work.

> **kevdog said:**
> For the life of me I can't get scp to work with filenames or directories with spaces in their names!!! SSH works but not scp. Ive tried /, double quotes, single quotes, combinations, %20, nothing seems to work.

Use tab when you are typing the path of your file

---

