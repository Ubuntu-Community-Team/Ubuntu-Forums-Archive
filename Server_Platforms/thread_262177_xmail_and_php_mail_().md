---
title: "xmail and php mail ()"
date: 2006-09-21
forum: Server Platforms
---

### Post by samuelkarush on 2006-09-21
Does anyone have any experience using xmail and the php mail () function? Xmail is working great, the mail () function is not. It worked well using postfix. I've done a bunch of reading, and tried a few things, but no luck. A point in the right direction would be great.
thanks,
sam karush

---

### Post by spp on 2006-09-22
The PHP Mail command is expecting sendmail or a sendmail wrapper in order to send things. Xmail has such a wrapper and a good discussion on how to set it up is [here]("http://xmailforum.homelinux.net/index.php?showtopic=3087")

SP

---

### Post by samuelkarush on 2006-09-22
Yes, i've been all through that forum, and am working with a fellow there to sort this out.

The post you linked to is very relevant. However, I believe that the original sendmail binary has already been replaced with a link to xmail's .sh script, which calls xmails sendmail binary.(or should, anyway. Something obviously isn't working right)

It's difficult to be certain, because the names and paths on ubuntu seem to be a bit different than in that post. Also, I'm not sure where this one peice of code originates from:

lrwxr-xr-x  1 root  wheel     17 Oct 13 10:06 sendmail -> sendmail.xmail.sh
-rwsr-sr-x  1 root  wheel  15428 Oct 13 10:04 sendmail.xmail
-rwsr-sr-x  1 root  wheel    141 Oct 14 07:35 sendmail.xmail.sh

So thats where I am at.
sam

---

### Post by spp on 2006-09-22
Well, the point of the wrapper is to allow you to use another MTA without having sendmail within 10 miles of the system. 

Have you tried calling the wrapper script from the command like like you would sendmail? If it works there, it should work from PHP as the PHP process will fork a call and call that program with the appropriate parameters passed.

SP

---

### Post by spp on 2006-09-22
As for where the code originates from, the first is the symbolic link that says "Hey, Sendmail is actually this script over here". This is used for programs that are hardcoded to call "sendmail <options>"

Third line is the replacement script for sendmail. It sets up the environment for the sendmail->xmail translation. It calls the second line which translates the sendmail options into xmail options and acutally sends the mail through xmail.

SP

---

### Post by samuelkarush on 2006-09-22
> **spp said:**
>  

Have you tried calling the wrapper script from the command like like you would sendmail? 

SP

I'm not quite sure how to do that.(beginner) It sure sounds like it would help pinpoint the problem

I understand now what that peice of code means. I'm  not sure what file it is found under, and if it needs to be edited on my machine.

---

### Post by spp on 2006-09-22
Alrighty :)

Do this:

Locate the sendmail.xmail.sh script

```
locate sendmail.xmail.sh
```


If you can't find it, run updatedb and try again. If you STILL cannot find it, create it by using the code on the site. Put it in the directory with sendmail.xmail. Link sendmail to that script. Make the script executable (chmod a+x)

Then...

```
./sendmail.xmail.sh
```

and see what happens.

---

### Post by samuelkarush on 2006-09-22
I had mentioned earlier, the file names are a bit different than the examples on the xmail forum.

xsendmail = sendmail.xmail.sh

Here is what I got

```
sam@sam-ibm:~$ locate xsendmail
/var/lib/xmail/sendmail/xsendmail
sam@sam-ibm:~$ cd /var/lib/xmail/sendmail
sam@sam-ibm:/var/lib/xmail/sendmail$ ./xsendmail
empty recipient list
sam@sam-ibm:/var/lib/xmail/sendmail$

```

appears that the xsendmail script is working (?)

here are the permissions for xsendmail
-r-xr-xr-x

it looks to be readable and executable by everyone

---

### Post by spp on 2006-09-22
Ok, the permissions on the file look good. Do you have a symbolic link pointing sendmail to that file? If not create one and set the sendmail_path variable in the mail() command to look at that file.

SP

---

### Post by samuelkarush on 2006-09-22
There is a file 'sendmail' under /usr/sbin which links to /var/lib/xmail/sendmail/xsendmail


Here is the portion of my php.ini file which I believe sets the sendmail_path for the mail() command 

```
[mail function]
; For Win32 only.
SMTP = localhost
smtp_port = 25

; For Win32 only.
;sendmail_from = postmaster@mydomain.com

; For Unix only.  You may supply arguments as well (default: "sendmail -t -i").
sendmail_path = /usr/sbin/sendmail -t -i
```

---

### Post by spp on 2006-09-22
Try this... (stab in the dark at this point...)


From [here...]("http://www.devarticles.com/c/a/PHP/Getting-Intimate-With-PHPs-Mail-Function/2/")
```

<?php
$fd = popen("/usr/sbin/sendmail -t","w");
fputs($fd, "To: myaddress@domain.tld\n");
fputs($fd, "From: Me \n");
fputs($fd, "Subject: Test message from my web site\n");
fputs($fd, "X-Mailer: PHP3\n");
fputs($fd, "Testing.\n");
pclose($fd);
?> 

```

That essentially replicates what the mail() function does. It may give you better insight on what is happening.

SP

---

### Post by samuelkarush on 2006-09-22
Nothing happens. It's just not making it to the xmail server.
That's a good article you linked to, though.


wonder what I'm missing?

I'll keep working on it....


I should mention that all scripts with mail() function work with postfix installed and xmail removed.

****************************
updated after sleeping on it
****************************



I got it to work. Even though  there was a sendmail in /usr/sbin that linked to the xmail sendmail script in mailroot (/var/lib/xmail), and the script called xmail's sendmail executable, it wouldn't work. Surprising, because this is the default installation using synaptic.

I had to change file names to match the instructions found on the xmail forum, and had to run it all right from /usr/sbin    

So i ended up with a script called sendmail in usr/sbin which called  sendmail.xmail , still in /usr/sbin.

here's the script:
```
#! /bin/sh
#modified for debian xmail package

export DEFAULT_DOMAIN=`cat /etc/xmail/default_domain`

if [ -z $MAIL_ROOT ]; then
	export MAIL_ROOT=/var/lib/xmail
fi

 /usr/sbin/sendmail.xmail $*
```

I sure hope this saves someone some time.
sk

---

