---
title: "php uploads, max post size etc"
date: 2008-06-05
forum: Server Platforms
---

### Post by robinc on 2008-06-05
Hello all,

I'm currently running a bog standard LAMP stack in my front room to store files on, use as a media server etc.

I've written some file upload bits and pieces, i changed the max upload and max post size to 1000M and it all worked fine for larger files.

Now I've set the max upload and post to 5000M and it still won't allow me to upload larger than 1GB, I've tried 5G as a value too.

Before anyone suggests yes i have run /etc/init.d/apache2 restart :)



Any ideas?

---

### Post by lsmobrian on 2008-06-05
Have you tried increasing memory allowed for php and execution time

---

### Post by robinc on 2008-06-06
Hi, thanks for your reply! 

I just tried them to no avail :(

---

### Post by hyper_ch on 2008-06-06
where did you alter it (and what exactely did you alter) and do you run php as module or a cgi?

---

### Post by cdenley on 2008-06-06
Are you sure there is enough free space left in /tmp and the destination?
```

df -h

```

---

### Post by robinc on 2008-06-06
Hi, everyone,I think PHP is running as a module, I changed 



/etc/php5/apache2/php.ini 

post_max_size=5G
upload_max_filesize = 5G

also tried

post_max_size=5000M
upload_max_filesize=5000M


I verifed the changed had been applied by running phpinfo(); each time.

Thanks again for your help.

Also I have about 90GB spare which I'm assuming will be enough to upload 3G files even with tmps etc?

---

### Post by hyper_ch on 2008-06-07
Now you need to alter the max execution time of a script... by default it's 60 seconds I think... if you want to upload 5gb it takes more.

Furthermore you also need to limit the max memory the script may use:

max_execution_time = 30     ; Maximum execution time of each script, in seconds
max_input_time = 60 ; Maximum amount of time each script may spend parsing request data
memory_limit = 4M      ; Maximum amount of memory a script may consume (16MB)

Don't ask me for the exact values that you have to put in there, but figure it you.

and of course restart apache afterwards ;)

---

### Post by quelx on 2008-06-07
FWIW, from [http://www.php.net/move_uploaded_file](http://www.php.net/move_uploaded_file)

> If you find that large files do not upload in PHP even though you've changed the max_upload_size , this is because you need to change the max memory size varible too. The entire file is loaded into memory before it is saved to disk.

---

