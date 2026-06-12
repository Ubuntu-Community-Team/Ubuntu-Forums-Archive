---
title: "[HELP] phpBB3 on Ubuntu server 10.04"
date: 2011-01-10
forum: Server Platforms
---

### Post by MurdR93 on 2011-01-10
Okay, iv been searching google and all instruction guides but i keep having problems installing phpbb, i had all the necessary components installed to be able to run phpbb, and now im simply re-installing phpbb on my server system, i have already transfered all the files to my server and when i browse to the directory of the phpbb , it redirects me to the /install/ directory automaticly, then it shows "Internal server error (500)" im not sure what i did wrong, please help me, also sorry about my grammer or misspelling, im in a hurry

---

### Post by CharlesA on 2011-01-11
If phpbb3 is already set up, you need to remove the install directory IIRC.

---

### Post by James78 on 2011-01-11
If doing what CharlesA said doesn't work (it should work though by the sounds of it); see if there are any errors and problems in /var/log/apache2/error.log, or if your VirtualHost has a custom ErrorLog directive, use that log file instead.

---

### Post by MurdR93 on 2011-01-11
I have already removed the directory from /www, all that remains is nothing.
I have tryed to retransfer the files yesterday, all fresh redownloaded and extracted, and when i browsed to the directory, the message remains

---

### Post by Thirtysixway on 2011-01-11
[http://packages.ubuntu.com/lucid/phpbb3](http://packages.ubuntu.com/lucid/phpbb3)
[https://help.ubuntu.com/community/PhpBB3](https://help.ubuntu.com/community/PhpBB3)
if you want to install via apt-get

---

### Post by CharlesA on 2011-01-11
Do you have PHP5 installed?

---

### Post by MurdR93 on 2011-01-11
Thank you so much, that really helped =D

---

### Post by MurdR93 on 2011-01-11
Yeah, I had all the required components installed.

---

### Post by CharlesA on 2011-01-11
Hrm. Did installing it from the repos get it working?

---

### Post by Thirtysixway on 2011-01-11
Only thing is if you run it from the repos, it's in Universe so it's not guaranteed to be updated right away with new security updates.

---

### Post by MurdR93 on 2011-01-11
Yea, I got it set up just right from the repos, PhpBB usually has the option to update itself through the Admin panel.

---

### Post by MurdR93 on 2011-01-11
Now, I noticed that when I install it through aptitude, it installs it to the /usr/share/ dir as usual, but when you use ln -s /usr/shar/blah /var/www/blah is it insecure having something linked to the usr/share from www?

---

### Post by Thirtysixway on 2011-01-11
> **MurdR93 said:**
> Now, I noticed that when I install it through aptitude, it installs it to the /usr/share/ dir as usual, but when you use ln -s /usr/shar/blah /var/www/blah is it insecure having something linked to the usr/share from www?

You should be fine, it's not insecure.

---

