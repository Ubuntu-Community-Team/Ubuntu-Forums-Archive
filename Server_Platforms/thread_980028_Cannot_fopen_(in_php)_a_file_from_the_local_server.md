---
title: "Cannot fopen (in php) a file from the local server."
date: 2008-11-12
forum: Server Platforms
---

### Post by mickey78 on 2008-11-12
Hello guys.

I have a server running ubuntu 7.10
Most of the things on it are running smoothly.

I have this problem that makes me bang my head.

I am running a php script, that tries to open a file from the local server, and it gives me a connection refused problem. I have tried EVERYTHING i could think of, and it doesnt work.

So I reduced it to something VERRRRY basic, and still gives me the error. Here is the details

<?php
$file = fopen('http://www.mydomain.com/myfile.txt', 'r');
?>

And this simple thing gives me:
Warning: fopen([http://www.mydomain.com/myfile.txt](http://www.mydomain.com/myfile.txt)) [function.fopen]: failed to open stream: Connection refused in /var/www/script.php on line 10

Now off course, my real script isnt something like that, but I wanted to make it very simple to eliminate all the sources.

Also, I can open the file in my browser no problem there.

I can fopen any other URL from any other server, but everytime i try to fopen a localfile, i get this.

Any help would be VERY appreciated!

Thanks a lot

---

### Post by pdescham49 on 2008-11-12
> **mickey78 said:**
> Hello guys.

I have a server running ubuntu 7.10
Most of the things on it are running smoothly.

I have this problem that makes me bang my head.

I am running a php script, that tries to open a file from the local server, and it gives me a connection refused problem. I have tried EVERYTHING i could think of, and it doesnt work.

So I reduced it to something VERRRRY basic, and still gives me the error. Here is the details

<?php
$file = fopen('http://www.mydomain.com/myfile.txt', 'r');
?>

And this simple thing gives me:
Warning: fopen([http://www.mydomain.com/myfile.txt](http://www.mydomain.com/myfile.txt)) [function.fopen]: failed to open stream: Connection refused in /var/www/script.php on line 10

Now off course, my real script isnt something like that, but I wanted to make it very simple to eliminate all the sources.

Also, I can open the file in my browser no problem there.

I can fopen any other URL from any other server, but everytime i try to fopen a localfile, i get this.

Any help would be VERY appreciated!

Thanks a lot

if you open up a shell on your local machine and do this:
```

  dig www.mydomain.com

```

what do you get. 

and in a shell also what happens when you do

```

wget http://www.mydomain.com/myfile.txt

```

post your results.

---

### Post by CrucifiedEgo on 2008-11-12
So, are you trying to fopen a file from the local webserver via http, or a local file via the path (eg /var/www/path/to/myfile.txt)?  if it's the former, are you using [http://localhost](http://localhost) or the domain name?  if it's the latter, do you have safe_mode on or a open_basedir restriction set?

---

