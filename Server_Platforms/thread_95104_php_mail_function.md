---
title: "php mail function"
date: 2005-11-25
forum: Server Platforms
---

### Post by MarkTheDaemon on 2005-11-25
Anybody got the php mail function working so it actually sends out email!

My setup is standard with the apache 2, php 4 and mysql

any help appreciated


Mark

---

### Post by hostile on 2005-11-25
It should work ootb if you installed everything correctly. 

I'm assuming you either used Synaptic or the CLI/apt-get to install, so it should work just fine.

In the root of your site, create a file called "testmail.php"

```

sudo touch testmail.php

```

Then use your favourite CLI editor to edit the file. For me, it would be:
```

sudo nano testmail.php

```

and enter:
```

<?php
// message
$message = "The mail server is working fine.";
// Use wordwrap()
$message = wordwrap($message, 70);
// Send
$rc = mail('**mymailaccount@myisp.ca**', 'Test Subject', $message);
if ($rc) {
print "Mail successfully sent!<br>";
}
else {
print "Failed to send mail!<br>";
}
?> 

```

*Note that you need to put in your own email addy where I bolded the text*

Then, open your browser to [http://yourwebhost.yourdomain/testmail.php](http://yourwebhost.yourdomain/testmail.php)

You should then receive an email from this.

If not, go into your logs and see where things are going wrong.

---

### Post by fakey1223 on 2006-04-26
To get the php mail() function working, I installed the sendmail package (doing so removed postfix).

---

### Post by LordHunter317 on 2006-04-26
I'll have to say this in every thread, but there is no need to do that.  Postfix is a drop-in replacement for sendmail.

---

