---
title: "New Cronjob PHP"
date: 2012-04-09
forum: Server Platforms
---

### Post by the1joker on 2012-04-09
Hello everybody.
Im trying to apply a cronjob for a ticker i need to use on my site.
i simply used a php script to create my crtonjobs which i pasted into nano.
for ($i=0;$i<60;$i++){
if ($i < 10){
echo "0".$i." * * * * php /home/tobias/www/scnew/inc/run_tick.php<BR>";
}
else {
echo $i." * * * * php /home/tobias/www/scnew/inc/run_tick.php<BR>";
}
} 
 
and the result after pasting
tobias@ubuntu:~$ crontab -l
00 * * * * php /home/tobias/www/scnew/inc/run_tick.php
etc.....
59 * * * * php /home/tobias/www/scnew/inc/run_tick.php
 
And the content of run_tick.php
 
<?php require_once "initialize.php"; ?>
<?php print $Tick->run_tick(); ?> 
 
If i call the page in my browser it works fine and gives me my results..
New Year 465. 
Tick Done:thejoker, Year: 465. 
Tick Done:toobster, Year: 465. 
Tick Done:tobias, Year: 465. 
Succesfully wrote to log file. /home/tobias/www/scnew/logs/ticklog_2012040917.txt
yes i know this is not safe, but safety is no concern if i cant make it work :)
My cronjob doesnt p[erform, maybe with errors, but i don't know where to look for those....
 
I'm runnning Ubuntu 11.10...
Thx!!

---

### Post by the1joker on 2012-04-09
Found the solution, the use of relative path wasn't liked

---

