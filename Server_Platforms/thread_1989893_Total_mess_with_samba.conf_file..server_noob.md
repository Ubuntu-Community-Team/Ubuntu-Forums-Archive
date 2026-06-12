---
title: "Total mess with samba.conf file..server noob"
date: 2012-05-29
forum: Server Platforms
---

### Post by pandoracode on 2012-05-29
Ok so I installed ubuntu server on a old HP I managed to acquire. My issue is when I follow some guides online (or even here) I have trouble finding the .conf file(for samba file share) to have already pre-filled content (example going to the global security settings to add or remove lines , etc.) what I usually find is empty files. Even better is sometimes when I confirm that Samba is running and installed and issue the command to kill it to start "editing" the files the terminal returns that the command is not known.

P.S install XFCE UI so I could actually set up the server , FTP, web server and then remove it once done

any help?

---

### Post by pandoracode on 2012-06-05
bump

---

### Post by darkod on 2012-06-06
Are you using sudo for opening system files?
Are you using the command line or the UI?

Try in the command line for example:
sudo nano /etc/samba/smb.conf

Does that open a file with content, or empty?

You exit nano with Ctrl + X.

---

### Post by pandoracode on 2012-06-07
Yes I do use server and the terminal but couple days ago I was editing something else and happened to hit "CTRL + X" and text magically appears..I dont know why but if something happens again..ill be posting

---

