---
title: "Local network and Ubuntu One Sync"
date: 2010-06-02
forum: Ubuntu One (CLOSED)
---

### Post by seanlano on 2010-06-02
I have a simple question: Presume I have two (or more) computers set up with Ubuntu One. I copy the exact same file manually into my Ubuntu One folder on two computers, will the U1 service realise this and not download it again? 

For example, I want to copy to the cloud a large file so that I can share it with others. It will upload to the server from the computer I first copy it to. Then on the second computer I copy it to the Ubuntu One folder as well, because I don't want to download it since I already have it. Will the U1 service on the second computer see the local file and skip the download?

I suppose I could just try it and see, but I would like to know what is supposed to happen.

---

### Post by duanedesign on 2010-06-02
Have never tried it but one thing to help improve your chances of suceess. Make sure you have Ubuntu One completely shut down on your computers until you get the file in all three locations. Close the Ubuntu One Preferences window and run the following to quit all the U1 processes.

```
u1sdtool -q; killall ubuntuone-login
```

You can make sure all ubuntu one processes are quit with:

```
ps aux | grep ubu
```

good luck. Let us know what happens.

---

### Post by seanlano on 2010-06-03
I'll give that a go. Thanks!

---

### Post by skippycostin on 2011-05-17
also, if you go to the u1 settings on your computer, you can tell it NOT to sync to your local machine. unselect the directory you don't want to sync on your second machine and it shouldn't download it.

---

