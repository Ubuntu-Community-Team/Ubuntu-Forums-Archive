---
title: "how to embed a .sh program to a webpage"
date: 2011-12-15
forum: Server Platforms
---

### Post by Fertech on 2011-12-15
I need help adding a #!/bin/sh file to a website, Is just a simple "hello worlds"  I can get it to print in the terminal, but how do I get it to print in a website?

---

### Post by Lars Noodén on 2011-12-15
You just have to precede your output with the right MIME type:

```

#!/bin/sh

echo "Content-type: text/plain\n\n";

echo "Hello, World!";

```

---

### Post by Fertech on 2011-12-15
okay I got the hello world in the terminal, but how do I send that output to a html, like to my /var/www/index.html

I know how to do a hello world in html code but I trying to do it in a .shell script .sh

---

### Post by Lars Noodén on 2011-12-16
You have to put it in a directory that allows CGI scripts to run.  The default for Apache2 is [font=Courier New]/usr/lib/cgi-bin[/font].

What are you really trying to do?

---

### Post by Fertech on 2011-12-17
Okay I will look into that, what I'm really trying to do is make website tool 
something like whatsmyip.org,  but since I don't know to much for now trying to 
keep it simple,  something more like an output of a simple hello world text.

---

### Post by lisati on 2011-12-17
PHP might be easier and more appropriate than shell scripts. A small incomplete example, which you can save in a ".php" file, might be as follows:

[PHP]
<?php
$ip=$_SERVER['REMOTE_ADDR'];
echo "Your current IP address is $ip\n";
?>
[/PHP]
The line **<?php** opens up the PHP portion of the file, **$ip=$_SERVER['REMOTE_ADDR'];** gets the IP address of the person viewing the page, **echo "Your current IP address is $ip\n";** displays the info on the screen, and **?>** wraps things up.

---

### Post by Fertech on 2011-12-17
so echo is the output to the screen. so if I want to echo ifconfig eth0 how would I do that.

---

### Post by lisati on 2011-12-17
If you want to run system commands from PHP, have a look here: [http://php.net/manual/en/function.system.php](http://php.net/manual/en/function.system.php)

CAUTION: if you are making your web page accessible by the public and you want to display the output of system commands, you will need to give some thought to system security, making sure that rogues don't access your system maliciously.

---

### Post by Lars Noodén on 2011-12-17
> **Fertech said:**
> so echo is the output to the screen. so if I want to echo ifconfig eth0 how would I do that.

Same as for any other program output, precede it with the appropriate MIME type.  Since the output will be normal text, that's the MIME type to use:

```

#!/bin/sh

echo "Content-type: text/plain\n\n";

/sbin/ifconfig;

```

If you want to do something like whatsmyip.org, then you can use one of the environment variables:

```

#!/bin/sh

echo "Content-type: text/plain\n\n";

echo "You are connecting from" ${REMOTE_ADDR};

```

See [env](http://manpages.ubuntu.com/manpages/oneiric/en/man1/env.1posix.html) for a full list of variables in use.

---

### Post by yifangt on 2012-03-01
I came to have similar question following this thread. 
I have bioinformatic program (say BLAST, many website have this program, especially NCBI). I was wondering how this program is embedded in the website (put aside the options, input file, output file, parameters etc). 
It seems like to embed the program into HTML, right? How? I tried to view the source code of the website, and totally got lost. 
I am just a beginner trying to learn programming, and need take a course, but I want to start with this ABC. Thank you for your education!

---

