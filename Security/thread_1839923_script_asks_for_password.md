---
title: "script asks for password"
date: 2011-09-06
forum: Security
---

### Post by q.dinar on 2011-09-06
hello. i wanted to install driver for hp laserjet 1020 for ubuntu 11.04 today, though, seems i needed just to download all updates, i have searched for solution in web and tried several other methods, among them: "ubuntu 11 04 hp laserjet 1020" in google -> [http://ubuntuforums.org/showthread.php?t=1839650](http://ubuntuforums.org/showthread.php?t=1839650) -> [http://hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_1020.html](http://hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_1020.html) -> ... -> download [http://prdownloads.sourceforge.net/hplip/hplip-3.11.7.run](http://prdownloads.sourceforge.net/hplip/hplip-3.11.7.run) -> searching for instruction [http://hplipopensource.com/hplip-web/install_wizard/index.html](http://hplipopensource.com/hplip-web/install_wizard/index.html) -> ... -> [http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html) .

look at [http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html) .
the script asks for superuser password. why? i have tried to run it with sudo sh hplip-3.11.7.run and it says that better not run as root, and if i run as user it asks for password. i have feared that it wanted to send password to its server, and have closed it.

do you know hplipopensource.com ? i hope it is trustable.

i have runned this file with sudo, so i am afraid it could install some spies as root. now i am going to download it again, because i am at other computer now, just to see its content with text editor, maybe, before asking root password it do not do any bad things.

can you explain, why it do not want to run as root, but asks for password?

---

### Post by Toz on 2011-09-06
I just installed this earlier today for my daughter. The reason that it asks for your password is so that it can install the necessary software on your computer. As you can see from the instructions in the link: [http://hplipopensource.com/hplip-web/install/install/index.html]("http://hplipopensource.com/hplip-web/install/install/index.html") - Step #8, the program will "Download and install and missing dependencies". To install software on your computer, you need to provide your password to enable installation through sudo.

As to why you should not run any script as root, that is a good security practice. When root privileges are required, then sudo is used. Some information about sudo: [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by q.dinar on 2011-09-07
"now i am going to download it again, because i am at other computer now, just to see its content with text editor, maybe, before asking root password it do not do any bad things."

i have not found string "passw" in the file.

Toz, your answer is unhelpful.

---

### Post by q.dinar on 2011-09-07
"When root privileges are required, then sudo is used." - when sudo is used , the program do not run as root?

---

