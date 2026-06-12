---
title: "GypsyMail????"
date: 2008-10-08
forum: Server Platforms
---

### Post by chriswebb18 on 2008-10-08
ok, so i have downloaded and edited the config files for gypsymail.  made sure it was all uploaded using ascii.  i keep getting the error:
The requested URL /cgi-bin/gypsymail.py/defaultconfig.txt/sample2.txt was not found on this server.

i know python is installed, my real question is(since i couldnt really find this anywhere) when config/installing gypsy mail it just says to put all your config and sample .txt file in the same directory.  do i need to make a gypsymail.py dir with defaultconfig.txt subdir to put the sample file in.  the error makes me think i should, but i dont understand why.  as it is i have 
/cgi-bin/
containing the gypsymail.py script and templates/ subdir
do i need it to have gypsymail.py (script)
and gypsymail.py(dir)... is that possible?

sorry im just really lost.  let me know if you need any other information

i followed all steps here:
[http://www.thinkspot.net/sheila/gypsy/gypsydoc.html](http://www.thinkspot.net/sheila/gypsy/gypsydoc.html)

i am using gypsy mail btw, because i do not have sendmail installed and dont really know anything about setting up a mail server, and gypsy just sends everything to any smtp server(localhost or external) and i can use my gmail account.

---

### Post by cariboo on 2008-10-08
You better have a look at the docs again it says to put these files:

```
     gypsymail.py - requires editing before uploading
     gypsyutils.py
     gypsymail.err

```

in your /cgi-bin directory, by default installation the directory should be /usr/lib/cgi-bin

These files:

```
     defaultconfig.txt
     config5.txt
     config6.txt
     sample1.txt
     sample2.txt
     sample3.txt
     sample4.txt
     successtemplate5.html
     successtemplate6.html

```

Have to be in /cgi-bin/templates so the correct path would be /usr/lib/cgi-bin/templates.

These files:

```
     sample1.html
     sample2.html
     sample3.html - requires editing of the email addresses in the menu, if you want the mails sent to you
     sample4.html
     sample5.html
     sample6.html

```

have to be anywhere in your public htm, so the path would be /var/www.

So to review the files in the first code block should be in /usr/lib/cgi-bin, the files in the second code block have to be in /usr/lib/cgi-bin/templates, so you will have to create the templates directory:

```
sudo mkdir /usr/lib/cgi-bin/templates
```

The files in the third code block have to be in /var/www.

Putting the files ahywhere else will entail changing several apache configuration files.

Jim

---

### Post by chriswebb18 on 2008-10-09
ok, so just for me to be sure and to help me understand, when it says
The requested URL /cgi-bin/gypsymail.py/defaultconfig.txt/sample2.txt was not found on this server.
URL is /cgi-bin... referring to (root of serverdocs)/cgi-bin
or (system root)/cgi-bin?
and since the cgi-bin is located at /usr/lib/cgi-bin, how does it find that, since it is looking for /cgi-bin, at either the root of serverdocs or system root?   i will try moving these as you say, but i was just a bit confused and had set it up with the (serverdocs root)/cgi-bin/templates.

i will let you know how it goes, could you please let me know how all that works, or at least any info you have.

---

### Post by chriswebb18 on 2008-10-09
alright, so that *seems to be an improvement.  now it can at least find the python script and gets somewhere.  now i have to figure out what i did wrong in the config.  here is the error(500) i get
> Internal Server Error

The server encountered an internal error or misconfiguration and was unable to complete your request.

Please contact the server administrator, webmaster@localhost and inform them of the time the error occurred, and anything you might have done that may have caused the error.

More information about this error may be available in the server error log.
Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch Server at *domain*.com Port 80

first, i am confused because in the defaultconfig.txt gypsymail.py and sample2.txt(which is the only one im using) i have all emails set to show [email]chri@*domain*.com[/email]

my gypsymail.err file is empty, so i dont really have anything more specific than that.

first question, by default is python path /usr/bin/env python?
/usr/bin/env is not a directory, and when i do ls /usr/bin | less it does show env, but i dont knwo if its realted to python
python script starts with this:
#!/usr/bin/env python

... double checked all config.txt sample.txt files and all show webmaster email as [email]chris@*domain*.com[/email].  im really confused i attached the html page, configs, and gypsymail.py

---

