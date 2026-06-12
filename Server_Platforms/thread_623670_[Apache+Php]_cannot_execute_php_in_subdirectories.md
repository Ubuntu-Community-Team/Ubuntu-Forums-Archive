---
title: "[Apache+Php] cannot execute php in subdirectories"
date: 2007-11-26
forum: Server Platforms
---

### Post by cataenry on 2007-11-26
Hi all,
i have installed apache and mod_php, and it seems to work under the root directory of my vhost, it correctly runs my scripts.. but inside subdirectories it doesn't work.. any hint? 

Thanks for the attention

---

### Post by colo on 2007-11-26
What does your error-log or PHP's error reporting output say?

---

### Post by cataenry on 2007-11-26
It says permission denied, but i don't think that's the problem, since file inside subdirectories and those in root directory are the same. And directory has execution right on for the owner (suphp is enabled).
(13)Permission denied: access to /debug/_user.php denied

---

### Post by cataenry on 2007-11-26
solved, that was really stupid rights issue..
i think this 3d can be erased :D

Bye bye

---

