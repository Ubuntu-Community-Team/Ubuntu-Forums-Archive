---
title: "lost password and encryption"
date: 2011-03-11
forum: Security
---

### Post by molvistan on 2011-03-11
I recently forgot my password. After searching i came across this page [https://help.ubuntu.com/community/LostPassword](https://help.ubuntu.com/community/LostPassword) , i reset my password following the instructions.

After rebooting i couldn't log in properly. My user and pass were accepted but no desktop, gnome, and home folder. the home folder had none of my files it had two files 'Access-Your-Private-Data.desktop' and 'README.txt'. Anyway i realised my files were encrypted. so i tried this [http://rayslinux.blogspot.com/2011/01/caught-out-by-being-overzealous-remove.html](http://rayslinux.blogspot.com/2011/01/caught-out-by-being-overzealous-remove.html)

i think i just made things worse. any suggestions??

thank you

---

### Post by kidders on 2011-03-12
Hi there,

Unfortunately, recovering an encrypted home directory is designed to be impossible unless you know the password.

> **molvistan said:**
> i tried this [http://rayslinux.blogspot.com/2011/01/caught-out-by-being-overzealous-remove.html](http://rayslinux.blogspot.com/2011/01/caught-out-by-being-overzealous-remove.html)

I'm afraid those instructions don't apply, since you don't know your password.

---

### Post by molvistan on 2011-03-17
I could maybe re-try guessing the password, as it's my only option. However, i have changed the password, so i can't guess the log-in password anymore as i use the new one to log-in and this does not decrypt the files. Is there another method to enter the old password to decrypt the files.

I hope you understand what i mean.

Thank you.

---

### Post by bodhi.zazen on 2011-03-17
You can mount (decrypt) if you know the old password.

[https://help.ubuntu.com/community/EncryptedPrivateDirectory#Live%20CD%20method%20of%20opening%20a%20encrypted%20home%20directory](https://help.ubuntu.com/community/EncryptedPrivateDirectory#Live%20CD%20method%20of%20opening%20a%20encrypted%20home%20directory)

---

