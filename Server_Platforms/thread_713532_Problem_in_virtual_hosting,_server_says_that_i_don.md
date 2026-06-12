---
title: "Problem in virtual hosting, server says that i dont have permission to that site.."
date: 2008-03-02
forum: Server Platforms
---

### Post by deepblue_tiano on 2008-03-02
Hello everyone i having trouble with my virtual host..My virtual host is okay coz the server is restarting fine without errors and the site name that i declare in virtual host is accessible in the browser, the only problem  is i get an permission denied, you dont have permission to this site..please help..

---

### Post by twistedtwig on 2008-03-03
have you checked the file permissions of that folder?

---

### Post by deepblue_tiano on 2008-03-03
Yes, I already try this sudo chown -R "the user" "location of my folder" but nothing happens

---

### Post by deepblue_tiano on 2008-03-03
And also when i try to extract my project in /var/www/ i cant see my folder in localhost.. and when i try localhost/myprojectname again i dont have permission to view the page..

---

### Post by rickyjones on 2008-03-03
> **deepblue_tiano said:**
> And also when i try to extract my project in /var/www/ i cant see my folder in localhost.. and when i try localhost/myprojectname again i dont have permission to view the page..

Try the following command replacing the path/folder with your path/folder:
```

sudo chmod -R www-data:www-data /var/www/website

```

-Richard

---

### Post by deepblue_tiano on 2008-03-03
> **rickyjones said:**
> Try the following command replacing the path/folder with your path/folder:
```

sudo chmod -R www-data:www-data /var/www/website

```

-Richard

What is the function of this code? sorry i am new to ubuntu..

---

### Post by rickyjones on 2008-03-04
> **deepblue_tiano said:**
> What is the function of this code? sorry i am new to ubuntu..

My apologies. The code is actually supposed to be:
```

chown -R www-data:www-data /var/www/folder

```

What this code does is change the ownership information on that folder to the apache user.

-Richard

---

### Post by deepblue_tiano on 2008-03-04
> **rickyjones said:**
> My apologies. The code is actually supposed to be:
```

chown -R www-data:www-data /var/www/folder

```

What this code does is change the ownership information on that folder to the apache user.

-Richard


Okay I will try this when i get home.. Is it also okay if i did it even my site folder is not in /va/www/ directory? because i did it in virtual host my location of my folder is in another drive...

---

### Post by rickyjones on 2008-03-04
> **deepblue_tiano said:**
> Okay I will try this when i get home.. Is it also okay if i did it even my site folder is not in /va/www/ directory? because i did it in virtual host my location of my folder is in another drive...

Just change the command to point to your correct folder. The path that I used is just an example.

-Richard

---

