---
title: "Simple question [Permission]"
date: 2011-12-17
forum: Security
---

### Post by rickygk on 2011-12-17
I downloaded apache 2 and the whole 9 yards. In the www file I cannot set the settings to read only for group\other users. So i keep getting permission denied. I know theres a terminal code to fix this I just can't remember it. Setting it by the folder does not work and although do-able I'd rather not go through several hundred items setting their permissions. I had done it once already and got everything set up fine, then I went to delete a file on my other computer with the keyboard.. Used the wrong keyboard and deleted my whole sub directory. Fortunately i have a simi-out-tdated version on my server lol. Any help much appreciated guys :-)

---

### Post by lisati on 2011-12-17
There's the [sudo]("https://help.ubuntu.com/community/RootSudo") command.....

---

### Post by rickygk on 2011-12-17
Yeah I open the folder up in sudo ofc

---

### Post by emiller12345 on 2011-12-17
I'm not sure this is what your looking for but...
```
sudo chmod go-wx -R /var/www
```test it out on a non-important folder first to make sure

edit:
some people like to keep directories executable and files not for some reason, not sure why
```
find /var/www -type f -exec sudo chmod go-wx '{}' \;
find /var/www -type d -exec sudo chmod go-w '{}' \;
```

---

### Post by Lars Noodén on 2011-12-18
You need to set the directories to a group that you are a member of and then make the directories group-writable.  The sticky bit is also set to make sure this is carried on to other files and directories that may be created later on.

```

sudo addgroup webmasters

sudo gpasswd --add rickygk webmasters

sudo chgrp -R webmasters /var/www

sudo find /var/www -type d -exec chmod g=rwxs "{}" \;

sudo find /var/www -type f -exec chmod g=rws  "{}" \;

```

---

