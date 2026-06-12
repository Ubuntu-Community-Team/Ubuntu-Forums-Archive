---
title: "problem with php mail() function"
date: 2007-06-12
forum: Server Platforms
---

### Post by patrickk on 2007-06-12
hey there

im playing around with setting up a home server, and i installed the current ubuntu server edition with a lamp architecture...it runs great and is very convenient in getting the lamp stuff up and running without the hassle of installing and configuring it all.

my question is this:  has anyone had trouble running php scripts with the mail function?  I have a few simple scripts, one of which uses the mail function...and the mail was never showing up, so now im just trying to get it working using the example script from php.net:

[http://us.php.net/function.mail](http://us.php.net/function.mail)

```
<?php
// The message
$message = "Line 1\nLine 2\nLine 3";

// In case any of our lines are larger than 70 characters, we should use wordwrap()
$message = wordwrap($message, 70);

// Send
mail('emailaddress@example.com', 'My Subject', $message);
?> 
```

and it doesnt work...do you know of any ways to figure out whats wrong?  I have some experience with php, but never on a server I set up myself...so it must be something that you need to enable or something like that...can anyone offer any advice or help?

--patrick

---

### Post by patrickk on 2007-06-12
nevermind i think i figured it out

---

### Post by hockey97 on 2007-06-13
What was wrong with it??

---

