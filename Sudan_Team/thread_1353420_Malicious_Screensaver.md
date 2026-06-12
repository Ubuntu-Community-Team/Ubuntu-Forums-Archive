---
title: "Malicious Screensaver"
date: 2009-12-12
forum: Sudan Team
---

### Post by mhmdfoss on 2009-12-12
When installing an innocuous "waterfall" screensaver from Gnome-Look.org, an Ubuntu user noticed something strange: apart from the screensaver not being on GNOME's approved list, it also contained a script that performed some peculiar substitutions. 
 Among other things, it took a file named auto.bash from the server and installed it on /user/bin/, along with a file named gnome.sh that it put in the /etc/profile.d/ directory. The script then issued ping requests to send very large packages to a particular server. The script presumably helped serve in a denial-of-service (DoS) attack against other servers that provide exploits for huge multiplayer games such as World of Warcraft. 
  The user posted his discovery in the [Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1349678") and the screensaver has since disappeared from the Gnome-Look.org site. The guesswork as to what the script exactly did and how to remove was batted about in the forum. Apparently the Debian package installed under the name app5552. It was determined that removing the malware together with the malicious script required the command 
  *sudo rm -f /usr/bin/Auto.bash /usr/bin/run.bash /etc/profile.d/gnome.sh /usr/bin/index.php /usr/bin/run.bash && sudo dpkg -r app5552* 
  In general the lesson to be learned is if you want a secure system, don't download any software outside the official package sources without at least looking at the source code first.

---

### Post by zero-n on 2009-12-13
Thanks alot MR.FOSS

---

### Post by lisati on 2009-12-13
More information can be found here: [http://ubuntuforums.org/showthread.php?p=8465710](http://ubuntuforums.org/showthread.php?p=8465710)

---

