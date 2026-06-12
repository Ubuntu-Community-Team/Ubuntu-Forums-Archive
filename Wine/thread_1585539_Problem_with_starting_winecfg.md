---
title: "Problem with starting winecfg"
date: 2010-09-30
forum: Wine
---

### Post by mss1988 on 2010-09-30
milan@milan-laptop:~$ winecfg
wine: '/home/milan' is not owned by you, refusing to create a configuration directory there

the console explains everything. please help...

---

### Post by slooksterpsv on 2010-09-30
Type in:

sudo chown milan:milan /home/milan

Then run it again.

---

### Post by mss1988 on 2010-09-30
I tried, and got the same output :(

---

### Post by slooksterpsv on 2010-09-30
Whats the output of the following:

ls -l /home | grep milan
ls -la ~ | grep .wine

---

### Post by mss1988 on 2010-09-30
here is the result...
milan@milan-laptop:~$ ls -l /home | grep milan
drwxrwxrwx 1 root root 524288 2010-10-01 00:22 milan
milan@milan-laptop:~$ ls -la ~ | grep .wine
milan@milan-laptop:~$

---

### Post by dino99 on 2010-10-01
***** drwxrwxrwx 1 root root 524288 2010-10-01 00:22 milan ****

what's that mess ? Dont change the default ubuntu rights: dangerous for security and will break your install. Now you need a clean install.

---

### Post by Half-Left on 2010-10-01
You should chown your home directory to your permissions.

An example would be:
```
cd /home
```
```
sudo chown -R milan:milan milan
```

---

### Post by mss1988 on 2010-10-01
I've got a new problem:

milan@milan-laptop:~$ cd /home
milan@milan-laptop:/home$ sudo chown -R milan:milan milan
[sudo] password for milan: 
chown: cannot access `milan/.gvfs': Permission denied
milan@milan-laptop:/home$

---

### Post by Half-Left on 2010-10-01
Do the same for your hidden directories or just create a new user and start again.

---

### Post by mss1988 on 2010-10-01
Thanks :)

---

### Post by mss1988 on 2010-10-01
I found what is problem. I mounted my NTFS partition in my home dir... after mounting it in the other dir, things are ok again :)
Thanks for your help people :)

---

### Post by slooksterpsv on 2010-10-01
Awesome, glad you figured it out. If you don't mind, could you mark the thread as solved?

---

