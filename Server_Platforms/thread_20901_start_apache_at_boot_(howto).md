---
title: "start apache at boot (howto)"
date: 2005-03-19
forum: Server Platforms
---

### Post by q(*v*)p on 2005-03-19
Hi,

i'm new to linux/ubuntu, and installed apache,
but can't seem to find how to make apache start at bootup.

any help much appreciated ;-)
cheers,
j

---

### Post by d0nk on 2005-03-19
[QUOTE=q(*v*)p]Hi,

i'm new to linux/ubuntu, and installed apache,
but can't seem to find how to make apache start at bootup.

any help much appreciated ;-)
cheers,
j[/QUOTE]
 try doing:
 # chmod +x /etc/init.d/apache

(you may need sudo to do that command, or become root [i set my box up so i can log in as root])

---

### Post by q(*v*)p on 2005-03-19
Thanks,
I get this error:
chmod: failed to get attributes of `/etc/init.d/apache': No such file or directory

there is no apache in the init.d directory...
do i need to copy something there?

---

### Post by fjleal on 2005-03-20
[QUOTE=q(*v*)p]there is no apache in the init.d directory...
do i need to copy something there?[/QUOTE]
Is there an httpd? :)

---

### Post by q(*v*)p on 2005-03-20
yes, there is, in /www/bin
I can start apache with apachectl, but want to start it automatically.

cheers

---

### Post by cisthebestuk on 2005-03-20
[QUOTE=q(*v*)p]Thanks,
I get this error:
chmod: failed to get attributes of `/etc/init.d/apache': No such file or directory

there is no apache in the init.d directory...
do i need to copy something there?[/QUOTE]
 Hi,

Try this instead:

# sudo chmod +x /etc/init.d/apache2

Dave

---

### Post by geek.de.nz on 2006-04-17
See my post at [http://ubuntuforums.org/showthread.php?p=929849#post929849](http://ubuntuforums.org/showthread.php?p=929849#post929849) for a detailed question on almost the same problem, please.

---

### Post by geek.de.nz on 2006-05-10
See [http://ubuntuforums.org/showthread.php?p=1001226#post1001226](http://ubuntuforums.org/showthread.php?p=1001226#post1001226) if you still have this problem. This might help.

---

