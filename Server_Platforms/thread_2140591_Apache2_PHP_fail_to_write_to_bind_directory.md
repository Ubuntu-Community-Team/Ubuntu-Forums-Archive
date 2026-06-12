---
title: "Apache2 PHP fail to write to bind directory"
date: 2013-04-30
forum: Server Platforms
---

### Post by Valpskott on 2013-04-30
I think I have some trouble with permissions.

sdb1 is mounted as EXT4 to a subfolder in /media/, and it works fine.
There are 3 directories in the root of sdb1, which are all "bind":ed via /etc/fstab, all 3 work to read/write and execute from within bash.
The 3:rd directory I created for use of uploaded files on a website I'm working on (don't want the files filling my 60gb SDD which the OS boots from).

I've set ownership 1000:1001 recursevly to the following directories:
/media/sdb2 (both before and after mount)
/home/website/

/media/sdb2/files is bind to /home/website/bind-directory/ and also has ownership 1000:1001 (which I set both before and after the mount)

All directories have permissions 775.

I've also added the user www-data to become a member of both group 1000 and 1001.

How ever, I have a PHP script on my webpage that can't output/write to that directory (binded as a subdirectory of the webpage folder). The script can how ever write to the parent directory (which is on the SSD).

```

<?php
exec('> bind-directory/test.txt');
?>

```

does not work, but...

```

<?php
exec('> test.txt');
?>

```

...works just fine.

Any thoughts, tips or guidance is much apprechiated.

---

### Post by Valpskott on 2013-04-30
Update: I just "unbinded" the subdirectory and typed an "ls" in the directory and the file that was supposed to go to the binded directory was there. Sooo, somehow Apache or PHP doesn't follow the bind. How to fix this?

---

### Post by Valpskott on 2013-04-30
I solved it myself. I had bounded the "/home/website/" directory to "/var/www", and somehow, the "/home/website/subdirectory" that was bound, was not mirrored in the "/var/www" directory.

---

