---
title: "Execute a .php file via command line"
date: 2010-11-16
forum: Server Platforms
---

### Post by chrislynch8 on 2010-11-16
Hi,

I have a php file that I need to execute via a cronjob. This file should be run by the www-data user as its a file in my /var/www/project folder.

When I run this file under root (php -f cron.php) everything works perfectly, but I want it to run under the www-data to be safe.

Before I run it vai crontab I tried it via command line as the www-data user and I receive errors

Fatal Error: Allowed memory size of 8388608 bytes expired (tried to allocate 232 bytes). 

But when I run it as the root user I get no errors and everything works correctly.

The file cron.php is used to process automated tasks in my CRM. So I don't really want to have the root user running a crontab every few mintues for this.

Must the www-data user be given more permissions? I am using Ubuntu 6.06LTS
PHP - 5.1.2
Apache  - 2.0.55
MySQL - 5.0.22

---

### Post by Ryan Dwyer on 2010-11-16
What is your script doing? Can you post the code so I can find out why it's reaching the memory limit?

---

### Post by chrislynch8 on 2010-11-17
The script is managing a scheduler for my CRM for automated tasks. Here is the file but it seems that the issue happens while its doing some other functions called.

It runs fine as root but any other user it hits the memory limit - which is why I think its just a settings

chdir(realpath(dirname(__FILE__)));
 
 require_once('include/entryPoint.php');

if(empty($current_language)) {
	$current_language = $sugar_config['default_language'];
}
$app_list_strings = return_app_list_strings_language($current_language);
$app_strings = return_application_language($current_language);

global $current_user;
$current_user = new User();
$current_user->getSystemUser();

///////////////////////////////////////////////////////////////////////////////
////	PREP FOR SCHEDULER PID
$GLOBALS['log']->debug('--------------------------------------------> at cron.php <--------------------------------------------');

$cachePath = 'cache/modules/Schedulers';
$pid = 'pid.php';
if(!is_dir($cachePath)) {
	mkdir_recursive($cachePath);
}
if(!is_file($cachePath.'/'.$pid)) {
	if(is_writable($cachePath)) { // the "file" does not yet exist
		write_array_to_file('timestamp', array(strtotime(date('H:i'))) , $cachePath.'/'.$pid);
		require_once($cachePath.'/'.$pid);
	} else {
		$GLOBALS['log']->fatal('Scheduler cannot write PID file.  Please check permissions on '.$cachePath);
	}
} else {
	if(is_writable($cachePath.'/'.$pid)) {
		require_once($cachePath.'/'.$pid);
	} else {
		$GLOBALS['log']->fatal('Scheduler cannot read the PID file.  Please check permissions on '.$cachePath);
	}
}
////	END PREP FOR SCHEDULER PID
///////////////////////////////////////////////////////////////////////////////

///////////////////////////////////////////////////////////////////////////////
////	EXECUTE IF VALID TIME (NOT DDOS)




if($timestamp[0] < strtotime(date('H:i'))) {
	if(is_writable($cachePath.'/'.$pid)) {
		write_array_to_file('timestamp', array(strtotime(date('H:i'))) , $cachePath.'/'.$pid);
		require('modules/Schedulers/Scheduler.php');
		$s = new Scheduler();
		$s->flushDeadJobs();
		$s->checkPendingJobs();
	} else {
		$GLOBALS['log']->fatal('Scheduler cannot write PID file.  Please check permissions on '.$cachePath);
	}
} else {
	$GLOBALS['log']->fatal('If you see a whole string of these, there is a chance someone is attacking your system.');
}
$exit_on_cleanup = true;
sugar_cleanup($exit_on_cleanup);
?>

---

### Post by koenn on 2010-11-17
there something in /etc/security/limits.conf that looks like it could limit www-data (or non-root users iin general)'s use of memory or so ?

---

### Post by Ryan Dwyer on 2010-11-18
> 
if(!is_dir($cachePath)) {
mkdir_recursive($cachePath);
}


I'm going to guess that the user doesn't have permission to create those directories and the mkdir_recursive() function doesn't check for failure. Therefore it goes into an infinite loop trying to create a directory until PHP's memory is exhausted.

---

