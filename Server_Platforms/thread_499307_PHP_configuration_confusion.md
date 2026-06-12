---
title: "PHP configuration confusion"
date: 2007-07-12
forum: Server Platforms
---

### Post by kitman420 on 2007-07-12
I am running apache2 and php 5. I have a script called test.php that prints the  the phpinfo(). If I point the web browser to [http://localhost/test.php](http://localhost/test.php) the php info is printed out.

Now, when I point the web browser to [http://localhost/test/](http://localhost/test/) the php info is printed out again! Why is this happening? I don't have another directory called test. What is curious is that the variable PHP_SELF == test.php whereas the _SERVER["REQUEST_URI"] == /test/ and _SERVER["SCRIPT_NAME"] == test.php.  So somehow either apache or php knows that I'm looking for test.php even though I asked for /test/.

So why is apache (or is it PHP) appending .php to the end of the script?  Is this the default behavior?

Thanks
db

---

### Post by jtc on 2007-07-12
Could it perhaps have something to do with the Rewriterule you mention in [this thread]("http://ubuntuforums.org/showthread.php?t=498697")?

---

### Post by kitman420 on 2007-07-12
It turns out that my rewrite rules weren't working because of this problem. And, the solution turns out that I have to disable Multiviews in apache.

db

---

