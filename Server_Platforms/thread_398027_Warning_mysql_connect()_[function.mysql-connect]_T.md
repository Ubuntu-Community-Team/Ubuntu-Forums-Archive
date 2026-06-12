---
title: "Warning: mysql_connect() [function.mysql-connect]: Too many connections in **"
date: 2007-03-31
forum: Server Platforms
---

### Post by envis on 2007-03-31
Hi!... i have difficulty finding where i can increase the number of connections my mysql is able to support on my Ubuntu 6.10 server

i get

Warning: mysql_connect() [function.mysql-connect]: Too many connections in **
(where i replace the address of the page with ** for privacy...)

all over the place on my pages on a crowded day like today >:o ! (saturday, 2h13 pm)

some webpage told me to boost the max_connections or something and restart mysqld!?!

cant find the max_connections anywhere in the config files i could think of... i checked in my php.ini and apache2.conf... i scratched the mysql files in /etc.. had 3 files there that i looked at closely, nothing seems to be about max connections in there.. i also found some mysqld stuff in /var/run/mysqld but there i didnt seem to find what i needed either...

does anyone know how i can fix the
Warning: mysql_connect() [function.mysql-connect]: Too many connections in **
error?

probably increase the amount of allowed connections, the server box doesnt seem to work hard at all the *******! i can surely boost that some more if i just knew where...

thanks in advance

---

### Post by envis on 2007-03-31
help!

---

### Post by envis on 2007-04-01
some page i manage to find in my search told my that if the "max_connections" was not in /etc/mysql/my.cnf to then add the line myself to the file.. i actually lost the page but they made me write something like
new var = max_connections=250
tried it, restarted apache, but kept getting the too many connections error.....

i changed it for just

max_connections=4000 (yea i chose 4000, everytime actually you think thats the problem? 4000 is too high so it doesnt work?)

im gonna try a lower number maybe... but i made sure i wrote that in the mysqld section...

anyways.. why isnt anyone helping me??

is it because nobody knows? or is there anything wrong with my post?

if you have any info please answer the post :)

---

### Post by envis on 2007-04-01
i mean.. that should not be so complicated.... i seem to have been able to learn that by default the mysql allows 100 simultaneous connections.... 

i dont want to change my scripts i run a lot of so complicated programs, like some immense constructions of codes and really, really have a LOT of visitors... but yet the computer hosting the server doesnt seem to work so hard at all im sure it could handle more.. im about to upgrade to a 20 times faster connection this week (server collocation) but it wont be so useful if the goddamn mysql cant allow any more ppl anyways....

anyone knows how i can change the max_connections of the mysql on my ubuntu 6.10 amd64 box (mysql.. 5.1 i think..)

thank you in advance!

---

### Post by envis on 2007-04-01
oh i think adding the max_connections parameter myself to the my.cnf file is the right thing to do but restarting the apache after is not enough!

now i restarted my computer and will see the results but i guess sudo /etc/init.d/mysqld or something like that might have done it too...

---

### Post by tturrisi on 2007-04-01
see:  [http://us3.php.net/manual/en/function.mysql-connect.php](http://us3.php.net/manual/en/function.mysql-connect.php)  [http://us3.php.net/manual/en/function.mysql-close.php](http://us3.php.net/manual/en/function.mysql-close.php)
You probably are not closing the connection in your php scripts.
Using mysql_close(): This explicitly closes the connections. The use of mysql_close() in conjunction with mysql_connect() would ensure that the connection is closed

---

