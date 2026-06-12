---
title: "phpMyAdmin Cannot start session without errors"
date: 2010-02-16
forum: Server Platforms
---

### Post by mjfroggy on 2010-02-16
Hello,

I get an error message that says 
phpMyAdmin - Error
Cannot start session without errors, please check errors given in your PHP and/or webserver log file and configure your PHP installation properly.


So I did some googling and found a post here
[http://www.electrictoolbox.com/phpmyadmin-cannot-start-session-without-errors/](http://www.electrictoolbox.com/phpmyadmin-cannot-start-session-without-errors/)

which speaks about resetting the ownership of the session directory. However I am wondering how I can find out what the owner if the directory is (if its root or admin or ...)

It's strange because it all worked fine just about two hours ago and I am not sure since I have the server automatically download security updates if there is something it automatically downloaded that caused this. Also how to make the server stop automatically downloading security updated?

thanks all

---

### Post by mjfroggy on 2010-02-16
dis regard above post I figured it out

---

### Post by squinter on 2010-07-27
I'm having the same problem now, what's your solution???

---

### Post by timgrin on 2010-09-06
I had this problem in lucid.

My problem was that in /etc/php5/apache2/php.ini the line with: ```
;session.save_path = "/tmp"
``` was commented out so PHP was defaulting somewhere else maybe.

I just uncommented it and restarted apache2 and it worked.

---

### Post by ug57amf on 2010-09-13
Thanks,

That worked for me :)

---

### Post by mojo706 on 2011-05-30
It worked on Natty Thanks Mate!

---

### Post by imquark on 2011-07-27
It worked on my ubuntu 10.10. Thanks man! I was fighting it for last two days :)

---

### Post by cwhisperer on 2011-08-16
> **timgrin said:**
> I had this problem in lucid.

My problem was that in /etc/php5/apache2/php.ini the line with: ```
;session.save_path = "/tmp"
``` was commented out so PHP was defaulting somewhere else maybe.

I just uncommented it and restarted apache2 and it worked.

worked for me ;)

---

### Post by AlexanderDGreat on 2012-05-19
Worked thanks!

---

### Post by lorranpego on 2012-12-12
Thank's!
Worked!

---

### Post by rgoya on 2013-07-14
uncommenting session.save_path = /tmp in php.ini works for me

I spent 2 days looking for the solution, Googling "can't log in to phpmyadmin" and "nothing happens"

The key was noticing the error message the first time I loaded phpmyadmin, when I reloaded it displayed the login screen but nothing happened when I logged in to phpmyadmin

I'm posting here so this solution is easier to find for someone (or me) the next time :D

---

### Post by Mariane on 2013-07-16
Thank you very much :)

---

