---
title: "File creation error on apache2 .cgi file"
date: 2011-01-14
forum: Server Platforms
---

### Post by dheerajrav on 2011-01-14
Hello,

I am using python as a cgi for a simple game that i'm planning to run on a website. It requires the user to enter his name and age. This is saved in a file newly created in his/her name.

However, I'm getting this error
<!-- The above is a description of an error in a Python program, formatted
 63      for a Web browser because the 'cgitb' module was enabled.  In case you
 64      are not reading this in a Web browser, here is the original traceback:
 65 
 66 Traceback (most recent call last):
 67   File "/var/www/webprog.cgi", line 51, in &lt;module&gt;
 68     main()
 69   File "/var/www/webprog.cgi", line 44, in main
 70     file_data(form["name"].value, form["age"].value)
 71   File "/var/www/webprog.cgi", line 33, in file_data
 72     fout=os.open("list/tmp.txt",os.O_CREAT,0777)
 73 OSError: [Errno 13] Permission denied: 'list/tmp.txt'
 74 
 75 -->

Any idea why this is happening??

---

### Post by James78 on 2011-01-14
You should use fcgi for this. CGI restarts the application on every request, but fcgi keeps the application in the server memory, so it's much faster and less consuming.

Anyways though, what are the permissions on it?
```
ls -l /var/www/list/tmp.txt
```

---

### Post by dheerajrav on 2011-01-14
A new file is created everytime a new user plays the game. Thats how I want it to be. But I've not been able to create the file.

---

### Post by dheerajrav on 2011-01-14
A new file is created everytime a new user plays the game. Thats how I want it to be. But I've not been able to create the file.

---

### Post by James78 on 2011-01-14
Well, in general, you want to make sure the file created is owned by user and group www-data, as well as having sufficient read and write. 644 should be good enough.

---

