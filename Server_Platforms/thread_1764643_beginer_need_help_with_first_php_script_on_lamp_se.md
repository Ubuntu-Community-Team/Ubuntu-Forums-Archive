---
title: "beginer need help with first php script on lamp server"
date: 2011-05-22
forum: Server Platforms
---

### Post by RadarG on 2011-05-22
ok I'm a bit confused I was looking at this video located on youtube here [http://www.youtube.com/watch?v=xsasql8yWeQ&feature=related]("http://www.youtube.com/watch?v=xsasql8yWeQ&feature=related") I copied and made a test.php file that contained the following code;

<?php


$connect = @mysql_connect ("localhost","root","xxxxxxx") or die("Well this is really messed up. We are dispatching an army of trained monkeys to fix this error please try again later.");

mysql_select_db("test")or die ("database does not exist");


  if($connect) {
  
  echo "yes";
  
  }else{
  
  echo "no";
  
  }



?>

I than saved this file as test.php and saved it to my windows desktop. I than used WinSCP to copy it to my /tmp folder on my lamp server. I than fired up putty and copied it to the /var/www when I go to local IP/test I only see the blank page. I was a bit confused so I repeated the steps again and took out the password for root I was expecting to receive an error message but I still only saw test again. Did I do something wrong. Thanks in advance.

---

### Post by tapi0n on 2011-05-22
Been ages since I used php to connect to a database. But iirc you need to add the port of your local host too. 

Also I've never used LAMP but does it include the php dependencies like libapache2-php?

---

### Post by SeijiSensei on 2011-05-22
Do you have php5-mysql installed?

Is the MySQL server running?  Did you create the database?

What errors do you see in /var/log/apache2/error.log?

---

### Post by tgalati4 on 2011-05-22
Yes, you need to connect to a specific port (probably 3306).  It is defined in your mysql configuration (/etc/mysql/my.cnf)  Also verify your mysql database name, user, and password.

---

### Post by RadarG on 2011-05-24
I figured it out I had my php wrong. I will edit my db config to use a different port thanks

---

### Post by RadarG on 2011-05-24
> **tgalati4 said:**
> Yes, you need to connect to a specific port (probably 3306).  It is defined in your mysql configuration (/etc/mysql/my.cnf)  Also verify your mysql database name, user, and password.

do I have to use a port? or can I just leave it the default? I think that mine is just setup as local host.

**update**
I checked my cnf and its using 3306 should I use a different port?

---

### Post by tgalati4 on 2011-05-24
localhost:3306

---

