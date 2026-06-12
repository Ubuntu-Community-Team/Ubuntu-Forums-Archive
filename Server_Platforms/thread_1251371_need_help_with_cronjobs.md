---
title: "need help with cronjobs"
date: 2009-08-27
forum: Server Platforms
---

### Post by mjfroggy on 2009-08-27
Hello all,

I have a php based script for my website. The file is in var/www/cronjobs      My issue is the cron job is not working.

here is what I did
1) in the php script file I put the following on the top line
#!/usr/bin/php
Should the above be inside a  <?php tag ??

next in ssh I did
sudo chmod +x correctiveactions.php

next I did 
crontab -e
 using nano the file that opened I have the below
#m h dom mon dow command
10 03 * * * /var/www/cronjobs/correctiveactions.php

so the above should run every day of every month at 3:10  however 3:10 came andwent and it did not run??

any suggestions on what I missed?
Thanks

---

### Post by tribaldata on 2009-08-27
Hi mjfroggy, 

I believe that the crontab is in 24hour format so you shoudl try
10 15 * * * /var/www/cronjobs/correctiveaction.php

Hope this help

---

### Post by mjfroggy on 2009-08-27
Well I changed the line via nano to

23 16 * * * /var/www/cronjobs/correctiveactions.php

which should be 4:23 USA EST but it still did not work. when I remove the #!/usr/bin/php and run the php via my internet browser it works.

I am thinking maybe the cronjob won't run the php script cause I have it in a folder in my var/www directory?? I also made just I
sudo chmod x+ the cronjobs folder

Maybe its how I have the hashbag setup I have 
[php]
#!/usr/bin/php
<?php
//my php code below
[/php]

maybe I should remove the <?php   ?> tags from the file or ??
thanks for the help

---

### Post by jay.parnaby on 2009-08-27
It's a long time since I did this but I seem to remember that to execute a PHP script as a cron job needs to specify the interpreter then the script to execute.

Try this

```

#m h dom mon dow command
10 03 * * * /usr/bin/php /var/www/cronjobs/correctiveactions.php

```

---

### Post by nandemonai on 2009-08-28
> **jay.parnaby said:**
> it's a long time since i did this but i seem to remember that to execute a php script as a cron job needs to specify the interpreter then the script to execute.

Try this

```

#m h dom mon dow command
10 03 * * * /usr/bin/php /var/www/cronjobs/correctiveactions.php

```

+1

---

