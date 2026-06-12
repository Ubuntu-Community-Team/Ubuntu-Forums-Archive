---
title: "Problem with send emails from cron"
date: 2018-02-05
forum: Server Platforms
---

### Post by poliman-pl on 2018-02-05
I have Ubuntu 16.04 LTS. I added cron jobs in ISPConfig3. Cronjobs work nicely.  I have in  /etc/cron.d file ispc_web28 (created by ISP panel). In the first line of this file is  MAILTO=''. I changed it to MAILTO=[EMAIL="cron_isp@domain.com"]cron_isp@domain.com[/EMAIL]  but nothing happens. I have fully operational ISP server with  postfix/dovecot which is able to send emails. I also checked from  console: 
```
echo Test | mail -s Test cron_isp@domain.com
```
and I got an email too. No idea what is wrong. Somebody any hints?

I have also few quite annoying problems. On the server is deployed few websites. Each has own LE SSL. 
1. No idea why certs are not renewed automatically. I can put log file I don't see wrong things there.
2. When some cert for particular website will expire then after enter  address of this site in browser I have opened first site added under ISP  but without certificate. It's probably, because ISP turn on first added  site but under address of domain which has expired cert (of course  after click add exception for certificate in browser). When I put in  browser address of this first site it has nice green padlock.
3. Sometimes I have to turn on LE SSL and SSL checboxes then click Save  button few times (of course after each I wait for propagate), because  for first time both checkboxes are unchecked.

---

### Post by LHammonds on 2018-02-05
If the command works from the console prompt but not in crontab, then it is most-likely due to crontab having a reduced environment...most specifically the search path.  

Type the following at the console:
```
which mail
```
```
which echo
```

If the result were /usr/sbin/echo and /usr/sbin/mail then modify your crontab command as such:

```
/usr/sbin/echo Test | /usr/sbin/mail -s Test cron_isp@domain.com
```

LHammonds

---

### Post by poliman-pl on 2018-02-05
```

root@s1:/etc/cron.d# which mail
/usr/bin/mail
root@s1:/etc/cron.d# which echo
/bin/echo

```

Should I put in ispc_web28, which looks like below:
```
 
MAILTO=''
SHELL='/bin/sh'
*/5     *       *       *       *       web28   /usr/bin/php /var/www/clients/client11/web28/web/public/admin/cron.php ActivationEmail >>/var/www/clients/client11/web28/private/cron.log 2>>/var/www/clients/client11/web28/private/cron_error.log #example.com

```

in MAILTO variable this piece of code -> /usr/sbin/echo Test | /usr/sbin/mail -s Test [EMAIL="cron_isp@domain.com"]cron_isp@domain.com[/EMAIL] ??

PS
I also tried with:
/usr/bin/php -q 
/usr/bin/php -f

---

### Post by LHammonds on 2018-02-05
Are you trying to send mail using php's mail function or /usr/bin/mail?

I have not tried to run .php code via the command-line so I'm not 100% positive how you have this setup.

EDIT: It seems like you are mixing shell script/environment variables with PHP code.

LHammonds

---

### Post by spjackson on 2018-02-05
> 
```
 
MAILTO=''
SHELL='/bin/sh'
*/5     *       *       *       *       web28   /usr/bin/php /var/www/clients/client11/web28/web/public/admin/cron.php ActivationEmail >>/var/www/clients/client11/web28/private/cron.log 2>>/var/www/clients/client11/web28/private/cron_error.log #example.com

```

Cron sends email only if there is any output from the job. Since you are redirecting both stdout (>>) and stderr (2>>) there can never be any output, so no email will ever be sent by cron for this job. Whether that job itself should send its own email is a different matter.

---

### Post by poliman-pl on 2018-02-06
Ok, now I know what's the problem. These two redirection are added automatically by ISPConfig panel. Really appreciate your answer. But I am not sure for 100% is that the source of problem. I checked cron.log and cron_error.log files which is also automatically created and for which is redirection. This file is empty. If file is empty and if I would delete both redirections, cron would send emails?

PS
MAILTO option should looks like MAILTO=some@email or MAILTO='some@email'?
Do you know guys maybe LetsEncrypt subject and problems which I wrote in my 1st post? I need some script which would renew certs after 3 months - some script added to cron.

---

### Post by poliman-pl on 2018-02-06
cron.php file looks like below:
```

<?php
/* Define path to application directory */
defined('APPLICATION_PATH') || define('APPLICATION_PATH', realpath(dirname(__FILE__) . '/../../application'));

/* Define path to files directory */
defined('FILES_PATH') || define('FILES_PATH', realpath(dirname(__FILE__) . '/../../data/files'));

/* Define application environment */
defined('APPLICATION_ENV') || define('APPLICATION_ENV', (getenv('APPLICATION_ENV') ? getenv('APPLICATION_ENV') : 'production'));

define('PUBLIC_PATH', APPLICATION_PATH . '/../public');
define('MEDIA_PATH', APPLICATION_PATH.'/../public/media');

/* Ensure the library is on include_path */
set_include_path(implode(PATH_SEPARATOR, array(
        realpath(APPLICATION_PATH . '/../library'),
        get_include_path(),
)));

/** Zend_Application */
require_once 'Zend/Application.php';


$application = new Zend_Application(
                APPLICATION_ENV,
                array(
                        'bootstrap' => array(
                                'class' => 'BootstrapCron',
                                'path' => APPLICATION_PATH . '/BootstrapCron.php',
                ),
                'config' => array(
                        APPLICATION_PATH . '/configs/global.ini',
                        APPLICATION_PATH . '/configs/admin.ini',
                )
        )
);

$_GET['plugins'] = parseArgs($argv);
$application->bootstrap()
                ->run();

function parseArgs($argv) {
        $argv = (is_array($argv)) ? $argv : array();

        array_shift($argv);
        $out = array();
        foreach($argv as $arg) {
                if(substr($arg, 0, 2) == '--') {
                        $eqPos = strpos($arg, '=');
                        if($eqPos === false) {
                                $key = substr($arg, 2);
                                $out[$key] = isset($out[$key]) ? $out[$key] : true;
                        } else {
                                $key = substr($arg, 2, $eqPos - 2);
                                $out[$key] = substr($arg, $eqPos + 1);
                        }
                } else if(substr($arg, 0, 1) == '-') {
                        if(substr($arg, 2, 1) == '=') {
                                $key = substr($arg, 1, 1);
                                $out[$key] = substr($arg, 3);
                        } else {
                                $chars = str_split(substr($arg, 1));
                                foreach($chars as $char) {
                                        $key = $char;
                                        $out[$key] = isset($out[$key]) ? $out[$key] : true;
                                }
                        }
                } else {
                        $out[] = $arg;
                }
        }
        return $out;
}

```

---

### Post by LHammonds on 2018-02-06
The PHP code doesn't seem to have any kind of mail function in it so you will only get mail if you configure it to do so where you call the script.  This also means you do not have to troubleshoot PHP's mail function for this.

As for the MAILTO question, you don't have to use quotes at all if your value does not contain spaces.  If it does, you can use single or double quotes but you must be consistent (if you start with a single quote, end with the single quote)

By default, cron will mail the local user of the cron job unless you specify the MAILTO variable.  If the MAILTO variable is assigned an empty string, it will not try to send mail at all.

Example: Disable mail being sent
```

MAILTO=''
SHELL='/bin/sh'
*/5     *       *       *       * web28 echo "This is a test of the emergency broadcast system"

```

Example: Specify an email address for output of any job
```

MAILTO='cron_isp@domain.com'
SHELL='/bin/sh'
*/5     *       *       *       * web28 echo "This is a test of the emergency broadcast system"

```

Example: Send email to different address per job. 1st job will use MAILTO address, 2nd job will not use mail
```

MAILTO='cron_isp@domain.com'
SHELL='/bin/sh'
*/5     *       *       *       * web28 echo "This is a test of the emergency broadcast system"
*/5     *       *       *       * web28 echo "This is a test of the emergency broadcast system" > /dev/null 2>&1
*/5     *       *       *       * web28 echo "This is a test of the emergency broadcast system"| /usr/bin/mail -s "Subject line" other@address.com
*/5     *       *       *       * web28 echo "This is a test of the emergency broadcast system"| /usr/bin/mail -s "Subject line" another@address.com

```

In the above examples, I'd use the explicit /usr/bin/mail option to make it painfully clear you are wanting email for any output of that job and what email address you want it going to.

LHammonds

---

### Post by poliman-pl on 2018-02-06
Thank you for answers and each of these possible options. To sum up - after deletion of both redirections sending mail will work. On old server from project using above cronjobs sending emails work fine. Value for MAILTO does not contain spaces -> [EMAIL="cron_isp@domain.com"]cron_isp@domain.com[/EMAIL], so I can use without ' '.

PS
Do you know something about renewing Lets Encrypt certs?

---

### Post by LHammonds on 2018-02-07
> **poliman-pl said:**
> Do you know something about renewing Lets Encrypt certs?No, I mostly use self-signed certs and GoDaddy certs...and none of it is automated.

I'm not sure I would use any kind of automation service either.  Certs, like domain renewals, do not expire very often and it is important enough for me to make sure it is handled correctly so I do it myself when the time comes to make updates.  I like to make sure it is done without any disruption to services.  It doesn't take much of my time to maintain and it is a critical part of my services.

LHammonds

---

### Post by poliman-pl on 2018-02-08
LetsEncrypt expire after each 3 months. LHammonds, do you use some script or do it manually?

---

### Post by LHammonds on 2018-02-08
> **poliman-pl said:**
> LetsEncrypt expire after each 3 months. LHammonds, do you use some script or do it manually?

In the  [Configure  for secure (SSL) access](http://hammondslegacy.com/forum/viewtopic.php?f=40&t=239#p565) section of my documentation for setting  up NextCloud, I show how I create self-signed certificates which won't  expire for 3 years...or 10 years if you want.

However, I do not  have any step-by-step documentation for the GoDaddy certs.  I only did  that one time and didn't remember to document the steps...but it was  mostly just go to their web site, download the SSL archive and extract  it on my server.  Renewing would be an identical procedure except just  overwriting the existing certs.

LHammonds

---

### Post by spjackson on 2018-02-08
> **poliman-pl said:**
> LetsEncrypt expire after each 3 months. LHammonds, do you use some script or do it manually?
I use Mail-In-A-Box [https://mailinabox.email/](https://mailinabox.email/) which automatically renews my LetsEncrypt certificate. You could perhaps have a look at how it does it.

---

### Post by poliman-pl on 2018-02-09
Thanks guys for your help. I will check it.

---

