---
title: "Backup to Google"
date: 2010-11-29
forum: Security
---

### Post by toolmania1 on 2010-11-29
Could I use rSync to backup to Google?  I wanted to use my Google account to store my back ups from my pc.  I really only have one or two main folders.  Right now, I just email myself with the files attached.  It would be nice to have them transferred to Google.  I am not sure if that can be done with something like rSync or some other backup utility?

---

### Post by toolmania1 on 2010-11-29
I know Google allows a user to upload files now using the Google docs on their server.  So, if I encrypted the files / folders first, then I could just upload them like that to the Google server.  I was thinking that I could do an automatic backup with rSync right into Google, but I need to learn more about rSync first.

---

### Post by sanderd17 on 2010-11-29
well, google changes his api sometimes, so that would give problems. Can't you use things like dropbox or ubuntu one? Those are made to backup files in the cloud. They both give 2 GB for free.

---

### Post by toolmania1 on 2010-11-29
I did not know about Ubuntu One.  I will look into it.  Thanks.

---

### Post by toolmania1 on 2010-11-29
[http://www.backuphowto.info/how-backup-ubuntu-one-and-get-2-gb-storage-free](http://www.backuphowto.info/how-backup-ubuntu-one-and-get-2-gb-storage-free)

---

### Post by sanderd17 on 2010-11-29
that's it. it almost saved my life once, when I lost an important work but I had synced it to the ubuntu one server.

---

### Post by toolmania1 on 2010-11-29
Is it pretty safe?   

Or should I encrypt my files first, then upload them to Ubuntu One?

---

### Post by sanderd17 on 2010-11-29
I'm not an expert in that area. It's safe in the way of "you won't lose data" but I don't know if it's safe it the way "nobody will see your data". There are share options, but if you use the web client everything happens via https. I don't know what type of connection the destop client uses.

I believe it's pretty safe since they also use the framework for there ubuntu one music store (in rhythmbox) I don't think they would handle money via an unsafe connection. But don't assume I'm right, as said, I'm not an expert.

---

### Post by 311005901 on 2010-11-29
[Here's a great guide for comparing backup services side-by-side]("http://en.wikipedia.org/wiki/Comparison_of_online_backup_services"). I use Dropbox, but if you're concerned about security, look into SpiderOak. UbuntuOne desktop sync is not encrypted, however, Dropbox and SpiderOak are.

---

### Post by sanderd17 on 2010-11-29
hmmm the comparision isn't so good. the table says dropbox has encryption and ubuntu one not (with a link to a bug report to add encription). But if you look to the bug, it's about encrypted files on the server, not about the encryption of the connection. And dropbox also doesn't encrypt his files on the server.

So dropbox and ubuntu one are equally safe. SpiderOak is probably safer, but I never tried it.

---

### Post by toolmania1 on 2010-11-29
If I encrypt and then send the files it should not matter, right?

---

### Post by sanderd17 on 2010-11-29
off coarse, the only problem is: where do you keep your key? If you keep it locally, when you lose your files, there is a big chance that the key is lost too. If you upload it, well, it can be seen if your files can be seen.

---

### Post by toolmania1 on 2010-11-29
You're right, phooey!

---

