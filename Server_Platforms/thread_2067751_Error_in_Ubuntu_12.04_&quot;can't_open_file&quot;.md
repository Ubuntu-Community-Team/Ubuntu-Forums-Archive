---
title: "Error in Ubuntu 12.04 &quot;can't open file&quot;"
date: 2012-10-07
forum: Server Platforms
---

### Post by chiefguerra on 2012-10-07
Hello,

I'm trying to save a file in wordpress but get blank page with "can't open file".

I looked in my apache2 error log and found this, but I can't seem to correct it. I tried to chown -R the directory, ensured CHMOD permissions were correct, added an .htaccess file and still get that error.

Any ideas guys? please help!!

[Sat Oct 06 16:42:25 2012] [error] [client 66.69.??.???] File does not  exist:  /home/themotor...../public_html/wp-content/themes/localstarta/images/none,  referer: [http://www......./wp-admin/admin.php?page=themestarta.php]("http://www.themotorpool.org/wp-admin/admin.php?page=themestarta.php")
[Sat Oct 06 16:42:26 2012] [error] [client 66.69.??.???] Directory index  forbidden by Options directive:  /home/themotor..../public_html/wp-content/themes/localstarta/images/,  referer: [http://www....../wp-admin/admin.php?page=themestarta.php]("http://www.themotorpool.org/wp-admin/admin.php?page=themestarta.php")

Ben

---

### Post by ajgreeny on 2012-10-07
Can you open the file at all?
Why do you want to save it if you can't even open it?
Where did the file come from?

I'm baffled about what exactly you mean.

Let's see the output of ```
ls -al */path/to/file*
```which may give a clue.

If it is a plain text file you could try ```
sudo nano */path/to/file*
```

---

### Post by chiefguerra on 2012-10-07
I know it's kind of confusing, but it's basically a plugin within wordpress. A theme editor! It works great using MAMP localhost, but live using ubuntu 12.04 is whats not working out.



 I am seeing a difference in PHP versions. When I first start it off  on my localhost using MAMP I’m using PHP Version 5.4.4, on my live  server where I’m having issues with I’m using PHP Version  5.3.10-1ubuntu3.4.


Not sure if that makes a difference.

---

