---
title: "setting up a ubuntu 7.10 server!!!!!!"
date: 2008-04-02
forum: Server Platforms
---

### Post by wallywal on 2008-04-02
hi there,

This is the first time i have used ubuntu, and my boss at work wants me to set it up as a lamp server, but i have no idea what i am doing! i can get it set up to the point where i can get into the root buy typing su thren password, but everything else after that i just cant get my head around! 

my boss knows how to do it, but he is away for a week and he wants me to have it up and running for when he gets back :( 

i doing like using command line, I would prefer a GUI! i am good at learning but i need someone to show me how to do it, coz i dont understand some over post etc!

would really appreciate if anyone could help me! 

Thanks Gary

---

### Post by ryazkhan on 2008-04-04
LAMP (Linux Apache MySQL PHP)
You already have linux running so you took care of L
```
sudo apt-get install apache2
``` will take care of A
Never configure mysql so cannot help with  M
> sudo apt-get install php5
sudo apt-get install libapache2-mod-php5
sudo /etc/init.d/apache2 restart  it will take care of P
So you have LAP up and running but we missing M here. 

To test A   **[COLOR="Blue"][http://localhost]("http://localhost")[/COLOR]**
To test P  > gedit /var/www/testphp.php
Insert the following line into the new file [COLOR="blue"]<?php phpinfo(); ?>[/COLOR]
To test it > sudo /etc/init.d/apache2 restart
 and  [COLOR="blue"][http://localhost/testphp.php]("http://localhost/testphp.php")[/COLOR]
Follow this:
[http://ubuntuguide.org/wiki/Dapper#Apache_HTTP_Server]("http://ubuntuguide.org/wiki/Dapper#Apache_HTTP_Server")

---

