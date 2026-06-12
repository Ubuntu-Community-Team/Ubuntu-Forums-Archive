---
title: "drupal username/password"
date: 2013-08-01
forum: Server Platforms
---

### Post by salmendar on 2013-08-01
hi,
 i am like new to so this may seem a very unprofessional act but i some how installed drupal on my ubuntu server and now i have forgotten my username and password(admin). i have phpmyadmin installed on the same server. this is under implementation and i need to put this up for office soon. its a small buisness and drupal is just clients request. now can someone please tell me how can i reset my admin password?????

i'll be really thankful
xxxxxxxxxxxxxxx

---

### Post by Habitual on 2013-08-01
depending on the Drupal version...
[https://drupal.org/node/44164](https://drupal.org/node/44164)
[URL="http://www.werockyourweb.com/how-reset-drupal-admin-password"]http://www.werockyourweb.com/how-reset-drupal-admin-password


[/URL]phpMyAdmin;
2. Select the database which Drupal use from the drop-down menu on the left.
4. Click on the SQL tab.
5. In the text field on the page type the following text:
```

update users set pass=md5('NEWPASS') where uid = 1;
```

where "NEWPASS" is your new administrative password. Then click on the GO button and if no errors present, the Drupal password should have been changed.

Stolen from [here...]("http://www.opensourceuniverse.com/drupal/how-can-i-reset-the-password-of-drupal-admin-158.html")

FYI: Offering access where none should be given is **not** necessary,  *you* can do it, easily. :)

Please let us know...

---

### Post by salmendar on 2013-08-01
Yes,
 admin is now accessible. 
thank you for the help.

---

### Post by Habitual on 2013-08-02
You are welcome.
Glad it worked out.

---

