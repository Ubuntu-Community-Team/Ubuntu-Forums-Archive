---
title: "gallery2 user registration error"
date: 2007-04-24
forum: Server Platforms
---

### Post by tbuss on 2007-04-24
I'm trying to set up user registration in gallery2. I chose the option of having an email sent for confirmation. I decided to run the email test before configuring the user registration, below is the results of that test:
```
Error (ERROR_UNKNOWN) : Could not send mail to tbuss01@gmail.com

    * in modules/core/classes/helpers/MailHelper_simple.class at line 102 (gallerycoreapi::error)
    * in modules/core/classes/GalleryCoreApi.class at line 2846 (mailhelper_simple::sendtemplatedemail)
    * in modules/core/AdminCore.inc at line 246 (gallerycoreapi::sendtemplatedemail)
    * in main.php at line 199 (admincorecontroller::handlerequest)
    * in main.php at line 87
    * in main.php at line 80

file_exists(/usr/share/gallery2/g2data/smarty/templates_c/%%3723729847)
is_dir(/usr/share/gallery2/g2data/smarty/templates_c/%%3723729847)
file_exists(/usr/share/gallery2/g2data/smarty/templates_c/%%3723729847)
is_writeable(/usr/share/gallery2/g2data/smarty/templates_c/%%3723729847)
file_exists(/usr/share/gallery2/g2data/smarty/templates_c/%%3723729847/v_9)
file_exists(/usr/share/gallery2/modules/core/classes/helpers/../../../..//modules/core/templates/local/EmailTest.tpl)
file_exists(/usr/share/gallery2/modules/core/classes/helpers/../../../..//modules/core/templates/local/EmailTest.tpl)
file_exists(/usr/share/gallery2/modules/core/classes/helpers/../../../..//modules/core/templates/EmailTest.tpl)
stat(/usr/share/gallery2/modules/core/classes/helpers/../../../..//modules/core/templates/EmailTest.tpl)
getParameter smtp.from for core plugin
file_exists(/usr/share/gallery2/g2data/cache/module/core/0/0/0.inc)
file_exists(/usr/share/gallery2/g2data/cache/module/core/0/0)
is_dir(/usr/share/gallery2/g2data/cache/module/core/0/0)
rename(/usr/share/gallery2/g2data/cache/module/core/0/0/0.incmiiJ8F,
/usr/share/gallery2/g2data/cache/module/core/0/0/0.inc)
mail(tbuss01@gmail.com, Gallery Email Test, This is a test email from
Gallery2, Content-Type: text/plain; charset="utf-8"
)

``` 
I have to be honest, I have the slightest clue as to where to begin to fix this: I took a look at the files where the errors were posted, not sure what to change in them to resolve the error. If anyone has any advice I would greatly appreciate it.

---

### Post by stuart.crouch on 2008-05-29
Found this thread whilst I was searching for an answer.  Then I figured out the answer.  Figured it might save some head scratching if I told people the solution here :P

```
sudo apt-get install postfix
```

I selected internet server as the option on the install screen (dunno if that was the right choice but it let me get email working in gallery2)

Whatever you choose as the hostname is what goes on the email it sends, so I entered "noisebox" and the emails were sent as "wwwadmin@noisebox".  I assume noisebox.com should have been what I entered, but I dont need it for replies so never bothered correcting it.

Once the install is finished you don't even have to restart apache, just go in and use the gallery2 email test with blank options.  It should work.

---

