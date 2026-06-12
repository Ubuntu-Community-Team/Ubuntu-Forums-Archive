---
title: "sudo cat /etc/shadow - Concerend about password change"
date: 2014-05-10
forum: Security
---

### Post by florence2 on 2014-05-10
I have NEVER set up a root password, however I have just run the sudo cat /etc/shadow command and it shows:

[noparse]root:!:16066:0:99999:7:::
daemon:*:15994:0:99999:7:::
bin:*:15994:0:99999:7:::
sys:*:15994:0:99999:7:::
sync:*:15994:0:99999:7:::
games:*:15994:0:99999:7:::
[/noparse]
and so on

I have read that the 1st number is the number of days after Jan 1 1970 that the password was changed. Most of the others show 15994 which equates to 16/10/13 however root shows 16066 which would equate to 27/12/2013. Does this mean that there was a root password set/changed on this date, as I never set a root password? I am therefore concerned about the security of my system.

Any guidance would be very much appreciated. I realise the ! signifies there is no password at present.

---

### Post by bapoumba on 2014-05-10
[http://linux.die.net/man/5/shadow](http://linux.die.net/man/5/shadow)

The ! in the password field means the password is locked. Same reading here on my own file.

Now the dates : have you upgraded keeping your /home and user on this machine ?

---

