---
title: "Cron Jobs Wont Run"
date: 2016-02-15
forum: Server Platforms
---

### Post by PC-2011 on 2016-02-15
I been trying to get php cron jobs to run for the past few days and no luck. Hopfully someone can shed some light on what I have setup wrong.
To start with I have run "chmod +x filename" on every file I want to execute. secound I ran "crontab -e" to edit the cron file(File below). Is there something I'm missing from all of this?

```

# Edit this file to introduce tasks to be run by cron.
#
# Each task to run has to be defined through a single line
# indicating with different fields when the task will be run
# and what command to run for the task
#
# To define the time you can provide concrete values for
# minute (m), hour (h), day of month (dom), month (mon),
# and day of week (dow) or use '*' in these fields (for 'any').#
# Notice that tasks will be started based on the cron's system

# daemon's notion of time and timezones.
#
# Output of the crontab jobs (including errors) is sent through
# email to the user the crontab file belongs to (unless redirected).
#
# For example, you can run a backup of all your user accounts
# at 5 a.m every week with:
# 0 5 * * 1 tar -zcf /var/backups/home.tgz /home/
#
# For more information see the manual pages of crontab(5) and cron(8)
#
# m h  dom mon dow   command
0 10 * * * /user/bin/php /var/www/html/index.php
*/5 * * * * /user/bin/php /var/www/html/email.php

```

---

### Post by steeldriver on 2016-02-15
Did you mean to write

```

[COLOR=#0000ff]**/usr**[/COLOR]/bin/php

```

---

### Post by PC-2011 on 2016-02-15
Yes sorry I miss typed. Still not working.

---

### Post by SeijiSensei on 2016-02-15
What do you see in /var/log/syslog? 
```
grep CRON /var/log/syslog
```

---

### Post by MAFoElffen on 2016-02-15
There are 6 fields in crontab:
```

[COLOR=#000000][FONT=Times New Roman]minute    hour    day    month    day-of-week    year    <command>[/FONT][/COLOR]

```
On the first, when fed through a parser, it goes, and evaluates to "At 10:00 every day"

On the second, it fails on "could not parse expression: */5"...

The '/' character in crontab is a skip interval for a range... '*' is not a range... but if you wrote instead as:
```

0-55/5 * * * * /user/bin/php /var/www/html/email.php

```
Would evaluate to what I think you were shooting for: "At every 0, 5, 10, 15, 20, 25, 30, 35, 40, 45, 50 and 55th minute past every hour."

---

### Post by PC-2011 on 2016-02-15
I get this. I only copied the last few minutes because it seams very repetitive. It looks like its trying to execute email.php ever 5 minutes but if the code was executed an email should have been sent out with information in it. I know the php file works because if you open it from a browser it sends the email. I just dont want to open my browser ever 5 minutes 24/7 to have it execute the code.
```

Feb 15 23:30:01 james-Inspiron-1520 CRON[3000]: (root) CMD (/user/bin/php /var/www/html/email.php)
Feb 15 23:31:01 james-Inspiron-1520 CRON[3016]: (james) CMD (/usr/bin/date >> /home/james/cron_work.log)
Feb 15 23:32:01 james-Inspiron-1520 CRON[3023]: (james) CMD (/usr/bin/date >> /home/james/cron_work.log)
Feb 15 23:33:01 james-Inspiron-1520 CRON[3031]: (james) CMD (/usr/bin/date >> /home/james/cron_work.log)
Feb 15 23:34:01 james-Inspiron-1520 CRON[3037]: (james) CMD (/usr/bin/date >> /home/james/cron_work.log)
Feb 15 23:35:01 james-Inspiron-1520 CRON[3045]: (james) CMD (/usr/bin/date >> /home/james/cron_work.log)
Feb 15 23:35:01 james-Inspiron-1520 CRON[3048]: (root) CMD (/user/bin/php /var/www/html/email.php)
Feb 15 23:36:01 james-Inspiron-1520 CRON[3063]: (james) CMD (/usr/bin/date >> /home/james/cron_work.log)
Feb 15 23:37:01 james-Inspiron-1520 CRON[3070]: (james) CMD (/usr/bin/date >> /home/james/cron_work.log)
Feb 15 23:38:01 james-Inspiron-1520 CRON[3077]: (james) CMD (/usr/bin/date >> /home/james/cron_work.log)
Feb 15 23:39:01 james-Inspiron-1520 CRON[3085]: (james) CMD (/usr/bin/date >> /home/james/cron_work.log)
Feb 15 23:39:01 james-Inspiron-1520 CRON[3084]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -x /usr/lib/php5/sessionclean ] && [ -d /var/lib/php5 ] && /usr/lib/php5/sessionclean /var/lib/php5 $(/usr/lib/php5/maxlifetime))
Feb 15 23:40:01 james-Inspiron-1520 CRON[3102]: (root) CMD (/user/bin/php /var/www/html/email.php)
Feb 15 23:40:01 james-Inspiron-1520 CRON[3103]: (james) CMD (/usr/bin/date >> /home/james/cron_work.log)
Feb 15 23:41:01 james-Inspiron-1520 CRON[3121]: (james) CMD (/usr/bin/date >> /home/james/cron_work.log)
Feb 15 23:42:01 james-Inspiron-1520 CRON[3128]: (james) CMD (/usr/bin/date >> /home/james/cron_work.log)
Feb 15 23:43:01 james-Inspiron-1520 CRON[3136]: (james) CMD (/usr/bin/date >> /home/james/cron_work.log)
Feb 15 23:44:02 james-Inspiron-1520 CRON[3142]: (james) CMD (/usr/bin/date >> /home/james/cron_work.log)
Feb 15 23:45:01 james-Inspiron-1520 CRON[3150]: (root) CMD (/user/bin/php /var/www/html/email.php)
Feb 15 23:45:01 james-Inspiron-1520 CRON[3153]: (james) CMD (/usr/bin/date >> /home/james/cron_work.log)
Feb 15 23:46:01 james-Inspiron-1520 CRON[3168]: (james) CMD (/usr/bin/date >> /home/james/cron_work.log)
Feb 15 23:47:01 james-Inspiron-1520 CRON[3276]: (james) CMD (/usr/bin/date >> /home/james/cron_work.log)

```

---

### Post by nerdtron on 2016-02-16
```
 
Feb 15 23:30:01 james-Inspiron-1520 CRON[3000]: (root) CMD (/user/bin/php /var/www/html/email.php)
```

The cron is triggered properly and runs the needed command. Now is your command working as expected? did you  include the absolute path on your variables inside your script?
Might as well post the script here so we can analyze further.

---

### Post by SeijiSensei on 2016-02-16
```
 
Feb 15 23:30:01 james-Inspiron-1520 CRON[3000]: (root) CMD (/user/bin/php /var/www/html/email.php)
```

The log says you are still using "/user/bin/php" rather than "/usr/bin/php".

As for the syntax, "*/5" is perfectly acceptable to mean "run at times when the minutes are divisible by five."  I use constructions like that all the time in crontab.

---

### Post by PC-2011 on 2016-02-16
I rebooted my system and the log shows this now.
```

Feb 16 10:30:39 james-Inspiron-1520 cron[887]: (CRON) INFO (pidfile fd = 3)
Feb 16 10:30:39 james-Inspiron-1520 cron[972]: (CRON) STARTUP (fork ok)
Feb 16 10:30:40 james-Inspiron-1520 cron[972]: (CRON) INFO (Running @reboot jobs)
Feb 16 10:31:00 james-Inspiron-1520 CRON[1697]: (james) CMD (/usr/bin/date >> /home/james/cron_work.log)
Feb 16 10:32:01 james-Inspiron-1520 CRON[2467]: (james) CMD (/usr/bin/date >> /home/james/cron_work.log)
Feb 16 10:33:01 james-Inspiron-1520 CRON[2561]: (james) CMD (/usr/bin/date >> /home/james/cron_work.log)
Feb 16 10:34:01 james-Inspiron-1520 CRON[2715]: (james) CMD (/usr/bin/date >> /home/james/cron_work.log)
Feb 16 10:35:01 james-Inspiron-1520 CRON[2775]: (root) CMD (/usr/bin/php /var/www/html/email.php)
Feb 16 10:35:01 james-Inspiron-1520 CRON[2774]: (james) CMD (/usr/bin/date >> /home/james/cron_work.log)
Feb 16 10:36:02 james-Inspiron-1520 CRON[2911]: (james) CMD (/usr/bin/date >> /home/james/cron_work.log)

```

Script is located in the default lamp directory for hosting a website.
If I right click the file and get its location it shows it in the /var/www/html so the location is correct

Here is my email.php script. My index.php script is vary similar. Both scripts run fine from a browser.
```

#!/usr/bin/php -q
<?php
ini_set('display_errors', 'On');
error_reporting(E_ALL);
set_time_limit(4000);
 $servername = "localhost";
$username = "root";
$password = "password";
$dbname = "database";
$conn = new PDO("mysql:host=$servername;dbname=$dbname", $username, $password);
// set the PDO error mode to exception
$conn->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
// Connect to gmail
$imapPath = '{imap.gmail.com:993/imap/ssl}INBOX';
$username = 'username@example.com';
$password = 'password@example';
 
// try to connect
$inbox = imap_open($imapPath,$username,$password) or die('Cannot connect to Gmail: ' . imap_last_error());
// search and get unseen emails, function will return email ids
$emails = imap_search($inbox,'Unseen');


/* if emails are returned, cycle through each... */
if($emails)
{

  /* begin output var */
  $output = '';

  /* put the newest emails on top */
  rsort($emails);

  /* for every email... */
  foreach($emails as $email_number)
  {
    $email="";
    /* get information specific to this email */
    $overview = imap_fetch_overview($inbox,$email_number,0);
    $message = strtolower(imap_fetchbody($inbox,$email_number,1));
    print $message;
    /* output the email header information */
    $from = $overview[0]->from;
    if(0==strcmp($message,strtolower("stop")))
    {
         $output = substr($from, 0, strpos($from, '@'));
         try {
                // sql to delete a record
                $sql = "DELETE FROM client WHERE cell=".$output;

                //use exec() because no results are returned
                $conn->exec($sql);
                echo "Record deleted successfully";
                }
        catch(PDOException $e)
            {
                echo $sql . "<br>" . $e->getMessage();

            $conn = null;
            $email = "You have been removed";
        }
    }
    if(0==strcmp($message,strtolower("like")))
    {
        $email = "Thank you for voting";
    }
    if(0==strcmp($message,strtolower("dislike")))
    {
        $email = "Thank you for voting";
    }
    if(mail($from,"",$email))
        {
            echo "<br>Mail has sent ".$email;
        }
        else
        {
            echo "<br>Mail has not been sent ".$email;
        }
   }
}

/* close the connection */
imap_close($inbox);
?>
```

---

### Post by SeijiSensei on 2016-02-16
Rather than running them from a browser, have you run the script from the terminal?  To replicate the situation in crontab where root is the user, use sudo:
```
sudo /usr/bin/php /var/www/html/email.php
```

---

### Post by PC-2011 on 2016-02-16
I just tried that and got this. I tried lunching it from both the standard php application and php5.
```

 /usr/bin/php /var/www/html/email.php
PHP Fatal error:  Call to undefined function imap_open() in /var/www/html/email.php on line 19

Fatal error: Call to undefined function imap_open() in /var/www/html/email.php on line 19
root@james-Inspiron-1520:~# /usr/bin/php5 /var/www/html/email.php
PHP Fatal error:  Call to undefined function imap_open() in /var/www/html/email.php on line 19

Fatal error: Call to undefined function imap_open() in /var/www/html/email.php on line 19

```
I'm at a loss at this point. Why would a function work from the browser opening it but not from a command line.

---

### Post by MAFoElffen on 2016-02-16
the script is not finding imap in memory, so cannot find the function of imap... so is one of two things-- (1) Not installed and enabled. (2) Installed, but not enabled.
```

sudo apt-get install php5-imap
```
^Would check if it is installed. If so it would skip. If not it would install it. You can confirm that by using phpinfo(), which would show imap in the output.


However it's not enabled by default so enable it with:
```

sudo php5enmod imap

```
After it is enabled, then restart apache:
```

service apache2 restart

```

**Edit-- [COLOR=#ff0000]But wait...[/COLOR]** It works in a browser (so finds it in memory) but not from a script? (where it doesn't)... That has to do with the shell environment, SO...
add this line to the file /etc/php5/cli/php.ini:
```

extension=imap.so 

```
That should add a pointer/reference to it from shell and cli...

---

### Post by PC-2011 on 2016-02-16
That worked! I had no idea that you have to activate extensions in a different place for the command line to read it. Thank you for all your help. I would have never thought of that.

---

### Post by MAFoElffen on 2016-02-16
Your are welcome. If solved, please revisit the first page of this thread > Link in upper right that says "Thread Tools" > "Mark as Solved". That will help others to find answers to their issues faster.

---

