---
title: "Perl scripts and apache"
date: 2006-09-12
forum: Server Platforms
---

### Post by mmcclure79 on 2006-09-12
I can't seem to get the formmail script to do anything but give me a 404 remotely and when I try it on the server it asks me what I want to open it with. Any suggestions on where to start?

---

### Post by WagnerVaz on 2006-09-12
You need put the executables scripts on cgi-bin and configure it proper.
otherwise it will ask to save.

You can even use the mod_perl with apache.

---

### Post by mmcclure79 on 2006-09-12
I checked and the script is in the cgi-bin folder and set to be executable. How can I check if I have mod_perl installed for apache? I'm not quite sure I installed it. If I can't get this  to work I do have a forum that sends emails with no problems, is there a way I can use php's mail function to send form data?

---

### Post by WagnerVaz on 2006-09-12
Your luck today, I'm PHP programmer, 
you can send mail with the mail() function.

To configure PHP with Mail:
[http://www.php.net/manual/en/ref.mail.php](http://www.php.net/manual/en/ref.mail.php)

To use the php mail() function:
[http://www.php.net/manual/en/function.mail.php](http://www.php.net/manual/en/function.mail.php)

You can check the user owner of file and the user of httpd daemon for make perl scripts work.

---

### Post by mmcclure79 on 2006-09-13
The mail() function is already set up. Is it possible to call it from a html page to send form fields? I'me delving into new waters and appreciate all the help I can get.

---

### Post by Tomosaur on 2006-09-13
I too had trouble with this. Turns out the cgi-bin is not /var/www/cgi-bin/, but is in fact /usr/lib/cgi-bin/. I just plonked my perl scripts in there and it worked fine.

---

### Post by mmcclure79 on 2006-09-13
Aha! and the script runs!, well atleast it finds it and gives me a script centric error.  Now to figure out what thus means: Premature end of script headers: email.pl

---

