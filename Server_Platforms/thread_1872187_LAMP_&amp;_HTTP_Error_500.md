---
title: "LAMP &amp; HTTP Error 500"
date: 2011-10-30
forum: Server Platforms
---

### Post by Wangberg on 2011-10-30
I set up LAMP a while back and PHP & Apache have been working fine up until a short while ago.  It seems PHP is no longer working and returns

```
HTTP Error 500 (Internal Server Error): An unexpected condition was encountered while the server was attempting to fulfill the request. 
```

i read in another post that i should enable error reporting in my php.ini file, but i enabled error reporting in my script (which has always worked) as:

[PHP]ini_set ('display_errors', 1);
error_reporting (E_ALL | E_STRICT);[/PHP]

additionally, i can't seem to get any feedback from /var/log/apache2/access.log but this is what i see:

```

::1 - - [30/Oct/2011:21:02:40 +0800] "GET /favicon.ico HTTP/1.1" 404 501 "-" "Mozilla/5.0 (X11; Linux i686) AppleWebKit/535.1 (KHTML, like Gecko) Chrome/14.0.835.202 Safari/535.1"
::1 - - [30/Oct/2011:21:02:44 +0800] "GET /favicon.ico HTTP/1.1" 404 500 "-" "Mozilla/5.0 (X11; Linux i686) AppleWebKit/535.1 (KHTML, like Gecko) Chrome/14.0.835.202 Safari/535.1"
::1 - - [30/Oct/2011:21:02:54 +0800] "POST /handle_reg.php HTTP/1.1" 500 274 "http://localhost/register.html" "Mozilla/5.0 (X11; Linux i686) AppleWebKit/535.1 (KHTML, like Gecko) Chrome/14.0.835.202 Safari/535.1"

```

any insight in how i can get my LAMP server and PHP running again?

thanks.

---

### Post by SeijiSensei on 2011-10-30
Any pointers to where the problem lay in /var/log/apache2/error.log?  Internal server errors cover a vast waterfront but are often a problem with the software application involved (as opposed to directory permissions, etc.).  Have you updated all the software on the machine recently?

---

### Post by lykwydchykyn on 2011-10-30
access log does not hold any errors; it only shows successful requests.

Like the other poster said, you want to see the error.log in the same folder.

---

### Post by Wangberg on 2011-10-30
> **SeijiSensei said:**
> Any pointers to where the problem lay in /var/log/apache2/error.log?  Internal server errors cover a vast waterfront but are often a problem with the software application involved (as opposed to directory permissions, etc.).  Have you updated all the software on the machine recently?

You and lykwydchykyn are right.  checked the error.log and found a parse error.  missing a curly brace.  thanks fellas

but why am i getting an Error 500 and the errors not displaying?  must i hack the php.ini file as suggested in another thread on another forum?  although, this setup is not operating in a production or work environment, hacking php.ini doesn't seem  secure practice.

edit:  also, previous php scripts that were running or returning errors are now all returning this error 500.  I didn't make any changes to Komodo but did do a system upgrade about a week ago and did make some changes to handle_reg.php and then cp to /var/www.  Understand though, everything was working and scripts were running after the system upgrade and out of the blue started returning an error 500.

---

### Post by lykwydchykyn on 2011-10-30
As I understand it, the directives in php.ini are read before any files are parsed, so setting "display_errors" there means the setting will take effect regardless of what happens in the file.

OTOH, if you're setting the ini setting in the same file that has syntax errors, it's not going to execute the file in the first place, so your set_ini() never gets called.

It might be possible to make the setting using an .htaccess file, but that doesn't work on every system (didn't work on mine).

---

### Post by Wangberg on 2011-10-31
> **lykwydchykyn said:**
> As I understand it, the directives in php.ini are read before any files are parsed, so setting "display_errors" there means the setting will take effect regardless of what happens in the file.

OTOH, if you're setting the ini setting in the same file that has syntax errors, it's not going to execute the file in the first place, so your set_ini() never gets called.

It might be possible to make the setting using an .htaccess file, but that doesn't work on every system (didn't work on mine).

i appreciate your feedback but i should have been more explicit in what i was looking for, because we're missing the point here.  

Everything was working fine...no problems.  I wrote php file files, change the permission chmod 777, then cp file.php /var/www .  bing bam boom, [http://localhost/file.php](http://localhost/file.php) runs.  I think it's safe to say that PHP is not broken because phpinfo() works when i try it as a test.  

What i want to solve is:

1) why does error handling no longer work? 
2) how can i fix it so i don't get ERROR 500 without hacking php.ini?

I shouldn't have to edit my php.ini file to report errors and in the past, parse errors were reported in the web browser upon running the faulty php script.  

When i express, everything was working fine and then out of the blue i get error 500 messages, that's really what happened.  

What can i do to debug this issue so i can get back to an environment that doesn't require hacking system files?

Thanks in advance!

---

### Post by lykwydchykyn on 2011-10-31
> **Wangberg said:**
> 
1) why does error handling no longer work? 
2) how can i fix it so i don't get ERROR 500 without hacking php.ini?


If you want specific answers, you're going to have to give specific information.  So far we know this:

> **Wangberg said:**
> 
edit:  also, previous php scripts that were running or returning errors are now all returning this error 500.  I didn't make any changes to Komodo but did do a system upgrade about a week ago and did make some changes to handle_reg.php and then cp to /var/www.  Understand though, everything was working and scripts were running after the system upgrade and out of the blue started returning an error 500.

What "system upgrade" did you do?  What packages were upgraded?  Was this a release upgrade?  What releases?
What's Komodo?
What's handle_reg.php?

---

### Post by Wangberg on 2011-10-31
> **lykwydchykyn said:**
> 
What "system upgrade" did you do?  What packages were upgraded?  Was this a release upgrade?  What releases?

i used 
```

aptitude install update
aptitude install upgrade-full

```

please specify what logs i should post for the specific packages updated.  but again, these upgrades took place prior to any problems.  

> 
What's Komodo?
What's handle_reg.php?

Komodo Edit, version 6.1.3, build 8844, platform linux-libcpp6-x86.  Built on Tue Sep 27 19:25:26 2011.

handle_reg.php 
```

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
	<head>
		<meta http-equiv="Content-Type" content="text/html; charset=utf-8"/>
		<title>Registration</title>
		<style type="text/css" media="screen">
			.error { color:red; }
		</style>
			
	</head>
	<body>
		<h2>Registration Results</h2>
		
		<?php //Script 6.7 - handle_reg.php
		
		/* This script receives eight values from register.thml:
		  email, password, confirm, month, day, year, color, submit */
				
		ini_set ('display_errors', 1);
		error_reporting (E_ALL | E_STRICT); //show all problems possible.
		
		// Flag variable to track success:
		
		$okay = TRUE;
		
		// Validate the email address:
		
		if (empty($_POST['email'])){
			print '<p class="error">Please enter your email address.</p>';
			$okay = FALSE;
		}
		
		// Validate the Password:
		
		if (empty($_POST['password'])) {
			print '<p class="error">Please enter your password.</p>';
			$okay = FALSE;
		}
		
		// Check the two passwords for equality:
		
		if ($_POST['password'] != $_POST ['confirm']) {
			print '<p class="error">Your confirmed password does not match the original password.</p>';
			$okay = FALSE;			
		}
		
		
		// Validate Birthday:
		
		$birthday = '';
		
		// Validate Month:
		
		if (is_numeric($_POST['month'])){
			$birthday = $_POST['month'] . '-';
		} else {
			print '<p class="error>Please select the month you were born.</p>';
			$okay = FALSE;
		}
		
		// Validate Day:
		
		if (is_numeric($_POST['day'])){
			$birthday .= $_POST['day'] . '-';
		} else {
			print '<p class="error>Please select the Day you were born.</p>';
			$okay = FALSE;
		}
		// Validate Year:
		
		if ( is_numeric($_POST['year']) AND (strlen($_POST['year']) == 4) ) {
			
		// Check that they were born before 2011
		
			if ($_POST['year'] >= 2011) {
				print '<p class="error">Either you entered your birth year incorrectly or you come from the future...what is it Future Boy?</p>';
				$okay = FALSE;
			} else {
				$birthday .= $_POST['year'];
			}
			
		} else {
			print '<p class="error">Please enter the year you were born as four digits.</p>';
			$okay = FALSE;
		}
		
		// Validate the color
		
		switch ($_POST['color']) {
			case 'red':
				print '<p style="color:red;">Red is your favorite color</p>';
				break;
			case 'yellow':
				print '<p style="color:yellow;">Yellow is your favorite color</p>';
				break;
			case 'blue';
				print '<p style="color:blue;">Blue is your favorite color...hoe</p>';
				break;
			case 'green';
				print '<p style="color:green;">Green is your favorite color</p>';
				break;
		} //end of switch
		
		// $color = '';
		
		// if ($_POST['color'] == 'red') {
		//	$color .= $_POST['color'];
		// } elseif ($_POST['color'] == 'green') {
		//	$color .= $_POST['color'];
		// } elseif ($_POST['color'] == 'yellow') {
		//	$color .= $_POST['color'];
		// } elseif ($_POST['blue'] == 'blue') {
		//	$color .= $_POST['color'];
			
		} else { //Problem!
			print '<p class="error">Please select your favorite color.</p>';
			$okay = FALSE;
		}
		
		
		
		// If there were no errors print a success message:
		
		if ($okay) {
			print '<p>You have been successfully registered (but not really).</p>';
			print "<p>You entered your birthday as $birthday.</p>";
		//	print "<p>Your favorite color is $color.</p>"; -- DELETED because switch is being used instead.
		}
	
		
		?>
		
		
	</body>
</html>

```

---

### Post by lykwydchykyn on 2011-10-31
Check /var/log/aptitude for a log of recent updates via aptitude.

---

### Post by Wangberg on 2011-10-31
> **lykwydchykyn said:**
> Check /var/log/aptitude for a log of recent updates via aptitude.

```

Aptitude 0.4.11.11: log report
Fri, Oct  7 2011 15:11:29 +0800

IMPORTANT: this log only lists intended actions; actions which fail due to
dpkg problems may not be completed.

Will install 74 packages, and remove 0 packages.
195MB of disk space will be used
===============================================================================
[INSTALL, DEPENDENCIES] linux-headers-2.6.32-34
[INSTALL, DEPENDENCIES] linux-headers-2.6.32-34-generic
[INSTALL] linux-image-2.6.32-34-generic
[UPGRADE] adobe-flash-properties-gtk 10.3.183.4-0lucid1 -> 11.0.1.152-0lucid1
[UPGRADE] adobe-flashplugin 10.3.183.4-0lucid1 -> 11.0.1.152-0lucid1
[UPGRADE] apt 0.7.25.3ubuntu9.6 -> 0.7.25.3ubuntu9.7
[UPGRADE] apt-transport-https 0.7.25.3ubuntu9.6 -> 0.7.25.3ubuntu9.7
[UPGRADE] apt-utils 0.7.25.3ubuntu9.6 -> 0.7.25.3ubuntu9.7
[UPGRADE] ca-certificates 20090814 -> 20090814ubuntu0.10.04.1
[UPGRADE] cups 1.4.3-1ubuntu1.3 -> 1.4.3-1ubuntu1.5
[UPGRADE] cups-bsd 1.4.3-1ubuntu1.3 -> 1.4.3-1ubuntu1.5
[UPGRADE] cups-client 1.4.3-1ubuntu1.3 -> 1.4.3-1ubuntu1.5
[UPGRADE] cups-common 1.4.3-1ubuntu1.3 -> 1.4.3-1ubuntu1.5
[UPGRADE] firefox 3.6.21+build1+nobinonly-0ubuntu0.10.04.1 -> 3.6.23+build1+nobinonly-0ubuntu0.10.04.1
[UPGRADE] firefox-branding 3.6.21+build1+nobinonly-0ubuntu0.10.04.1 -> 3.6.23+build1+nobinonly-0ubuntu0.10.04.1
[UPGRADE] firefox-gnome-support 3.6.21+build1+nobinonly-0ubuntu0.10.04.1 -> 3.6.23+build1+nobinonly-0ubuntu0.10.04.1
[UPGRADE] gimp 2.6.8-2ubuntu1.3 -> 2.6.8-2ubuntu1.4
[UPGRADE] gimp-data 2.6.8-2ubuntu1.3 -> 2.6.8-2ubuntu1.4
[UPGRADE] gnome-power-manager 2.30.0-0ubuntu1 -> 2.30.0-0ubuntu1.1
[UPGRADE] google-chrome-stable 13.0.782.220-r99552 -> 14.0.835.202-r103287
[UPGRADE] google-talkplugin 2.2.2.0-1 -> 2.3.2.0-1
[UPGRADE] libavcodec52 4:0.5.1-1ubuntu1.1 -> 4:0.5.1-1ubuntu1.2
[UPGRADE] libavformat52 4:0.5.1-1ubuntu1.1 -> 4:0.5.1-1ubuntu1.2
[UPGRADE] libavutil49 4:0.5.1-1ubuntu1.1 -> 4:0.5.1-1ubuntu1.2
[UPGRADE] libcups2 1.4.3-1ubuntu1.3 -> 1.4.3-1ubuntu1.5
[UPGRADE] libcupscgi1 1.4.3-1ubuntu1.3 -> 1.4.3-1ubuntu1.5
[UPGRADE] libcupsdriver1 1.4.3-1ubuntu1.3 -> 1.4.3-1ubuntu1.5
[UPGRADE] libcupsimage2 1.4.3-1ubuntu1.3 -> 1.4.3-1ubuntu1.5
[UPGRADE] libcupsmime1 1.4.3-1ubuntu1.3 -> 1.4.3-1ubuntu1.5
[UPGRADE] libcupsppdc1 1.4.3-1ubuntu1.3 -> 1.4.3-1ubuntu1.5
[UPGRADE] libgimp2.0 2.6.8-2ubuntu1.3 -> 2.6.8-2ubuntu1.4
[UPGRADE] libgksu2-0 2.0.13~pre1-1ubuntu4.1 -> 2.0.13~pre1-1ubuntu4.2
[UPGRADE] libgtk-vnc-1.0-0 0.3.10-2ubuntu2 -> 0.3.10-2ubuntu2.1
[UPGRADE] libnss3-1d 3.12.9+ckbi-1.82-0ubuntu0.10.04.1 -> 3.12.9+ckbi-1.82-0ubuntu0.10.04.3
[UPGRADE] libphonon4 4:4.6.2-0ubuntu5.2 -> 4:4.6.2-0ubuntu5.3
[UPGRADE] libpostproc51 4:0.5.1-1ubuntu1.1 -> 4:0.5.1-1ubuntu1.2
[UPGRADE] libqt4-assistant 4:4.6.2-0ubuntu5.2 -> 4:4.6.2-0ubuntu5.3
[UPGRADE] libqt4-dbus 4:4.6.2-0ubuntu5.2 -> 4:4.6.2-0ubuntu5.3
[UPGRADE] libqt4-designer 4:4.6.2-0ubuntu5.2 -> 4:4.6.2-0ubuntu5.3
[UPGRADE] libqt4-help 4:4.6.2-0ubuntu5.2 -> 4:4.6.2-0ubuntu5.3
[UPGRADE] libqt4-network 4:4.6.2-0ubuntu5.2 -> 4:4.6.2-0ubuntu5.3
[UPGRADE] libqt4-opengl 4:4.6.2-0ubuntu5.2 -> 4:4.6.2-0ubuntu5.3
[UPGRADE] libqt4-qt3support 4:4.6.2-0ubuntu5.2 -> 4:4.6.2-0ubuntu5.3
[UPGRADE] libqt4-script 4:4.6.2-0ubuntu5.2 -> 4:4.6.2-0ubuntu5.3
[UPGRADE] libqt4-scripttools 4:4.6.2-0ubuntu5.2 -> 4:4.6.2-0ubuntu5.3
[UPGRADE] libqt4-sql 4:4.6.2-0ubuntu5.2 -> 4:4.6.2-0ubuntu5.3
[UPGRADE] libqt4-sql-mysql 4:4.6.2-0ubuntu5.2 -> 4:4.6.2-0ubuntu5.3
[UPGRADE] libqt4-sql-sqlite 4:4.6.2-0ubuntu5.2 -> 4:4.6.2-0ubuntu5.3
[UPGRADE] libqt4-svg 4:4.6.2-0ubuntu5.2 -> 4:4.6.2-0ubuntu5.3
[UPGRADE] libqt4-test 4:4.6.2-0ubuntu5.2 -> 4:4.6.2-0ubuntu5.3
[UPGRADE] libqt4-webkit 4:4.6.2-0ubuntu5.2 -> 4:4.6.2-0ubuntu5.3
[UPGRADE] libqt4-xml 4:4.6.2-0ubuntu5.2 -> 4:4.6.2-0ubuntu5.3
[UPGRADE] libqt4-xmlpatterns 4:4.6.2-0ubuntu5.2 -> 4:4.6.2-0ubuntu5.3
[UPGRADE] libqtcore4 4:4.6.2-0ubuntu5.2 -> 4:4.6.2-0ubuntu5.3
[UPGRADE] libqtgui4 4:4.6.2-0ubuntu5.2 -> 4:4.6.2-0ubuntu5.3
[UPGRADE] librsvg2-2 2.26.3-0ubuntu1 -> 2.26.3-0ubuntu1.1
[UPGRADE] librsvg2-common 2.26.3-0ubuntu1 -> 2.26.3-0ubuntu1.1
[UPGRADE] libsmbclient 2:3.4.7~dfsg-1ubuntu3.7 -> 2:3.4.7~dfsg-1ubuntu3.8
[UPGRADE] libswscale0 4:0.5.1-1ubuntu1.1 -> 4:0.5.1-1ubuntu1.2
[UPGRADE] libwbclient0 2:3.4.7~dfsg-1ubuntu3.7 -> 2:3.4.7~dfsg-1ubuntu3.8
[UPGRADE] linux-generic 2.6.32.33.39 -> 2.6.32.34.40
[UPGRADE] linux-headers-generic 2.6.32.33.39 -> 2.6.32.34.40
[UPGRADE] linux-image-generic 2.6.32.33.39 -> 2.6.32.34.40
[UPGRADE] linux-libc-dev 2.6.32-33.72 -> 2.6.32-34.77
[UPGRADE] opera 11.50.1074 -> 11.51.1087
[UPGRADE] phonon 4:4.6.2-0ubuntu5.2 -> 4:4.6.2-0ubuntu5.3
[UPGRADE] samba 2:3.4.7~dfsg-1ubuntu3.7 -> 2:3.4.7~dfsg-1ubuntu3.8
[UPGRADE] samba-common 2:3.4.7~dfsg-1ubuntu3.7 -> 2:3.4.7~dfsg-1ubuntu3.8
[UPGRADE] samba-common-bin 2:3.4.7~dfsg-1ubuntu3.7 -> 2:3.4.7~dfsg-1ubuntu3.8
[UPGRADE] smbclient 2:3.4.7~dfsg-1ubuntu3.7 -> 2:3.4.7~dfsg-1ubuntu3.8
[UPGRADE] smbfs 2:3.4.7~dfsg-1ubuntu3.7 -> 2:3.4.7~dfsg-1ubuntu3.8
[UPGRADE] thunderbird 3.1.13+build1+nobinonly-0ubuntu0.10.04.1 -> 3.1.15+build1+nobinonly-0ubuntu0.10.04.1
[UPGRADE] tzdata 2011g-0ubuntu0.10.04 -> 2011j-0ubuntu0.10.04
[UPGRADE] xulrunner-1.9.2 1.9.2.21+build1+nobinonly-0ubuntu0.10.04.1 -> 1.9.2.23+build1+nobinonly-0ubuntu0.10.04.1
===============================================================================

Log complete.
Aptitude 0.4.11.11: log report
Fri, Oct  7 2011 19:08:55 +0800

IMPORTANT: this log only lists intended actions; actions which fail due to
dpkg problems may not be completed.

Will install 63 packages, and remove 0 packages.
395MB of disk space will be used
===============================================================================
[INSTALL, DEPENDENCIES] ant
[INSTALL, DEPENDENCIES] ant-gcj
[INSTALL, DEPENDENCIES] ant-optional
[INSTALL, DEPENDENCIES] ant-optional-gcj
[INSTALL, DEPENDENCIES] ca-certificates-java
[INSTALL, DEPENDENCIES] default-jdk
[INSTALL, DEPENDENCIES] default-jre
[INSTALL, DEPENDENCIES] default-jre-headless
[INSTALL, DEPENDENCIES] eclipse-jdt
[INSTALL, DEPENDENCIES] eclipse-pde
[INSTALL, DEPENDENCIES] eclipse-platform
[INSTALL, DEPENDENCIES] eclipse-platform-data
[INSTALL, DEPENDENCIES] eclipse-plugin-cvs
[INSTALL, DEPENDENCIES] eclipse-rcp
[INSTALL, DEPENDENCIES] fastjar
[INSTALL, DEPENDENCIES] gcj-4.4-base
[INSTALL, DEPENDENCIES] gcj-4.4-jre-lib
[INSTALL, DEPENDENCIES] icedtea-6-jre-cacao
[INSTALL, DEPENDENCIES] jarwrapper
[INSTALL, DEPENDENCIES] junit
[INSTALL, DEPENDENCIES] junit4
[INSTALL, DEPENDENCIES] libaccess-bridge-java
[INSTALL, DEPENDENCIES] libaccess-bridge-java-jni
[INSTALL, DEPENDENCIES] libasm3-java
[INSTALL, DEPENDENCIES] libcommons-beanutils-java
[INSTALL, DEPENDENCIES] libcommons-codec-java
[INSTALL, DEPENDENCIES] libcommons-collections3-java
[INSTALL, DEPENDENCIES] libcommons-compress-java
[INSTALL, DEPENDENCIES] libcommons-digester-java
[INSTALL, DEPENDENCIES] libcommons-el-java
[INSTALL, DEPENDENCIES] libcommons-httpclient-java
[INSTALL, DEPENDENCIES] libcommons-logging-java
[INSTALL, DEPENDENCIES] libdb-je-java
[INSTALL, DEPENDENCIES] libdb4.7-java
[INSTALL, DEPENDENCIES] libdb4.7-java-gcj
[INSTALL, DEPENDENCIES] libecj-java
[INSTALL, DEPENDENCIES] libequinox-osgi-java
[INSTALL, DEPENDENCIES] libgcj-bc
[INSTALL, DEPENDENCIES] libgcj-common
[INSTALL, DEPENDENCIES] libgcj10
[INSTALL, DEPENDENCIES] libhamcrest-java
[INSTALL, DEPENDENCIES] libicu4j-java
[INSTALL, DEPENDENCIES] libjasper-java
[INSTALL, DEPENDENCIES] libjaxp1.3-java
[INSTALL, DEPENDENCIES] libjetty-java
[INSTALL, DEPENDENCIES] libjline-java
[INSTALL, DEPENDENCIES] libjsch-java
[INSTALL, DEPENDENCIES] libjtidy-java
[INSTALL, DEPENDENCIES] liblucene2-java
[INSTALL, DEPENDENCIES] libregexp-java
[INSTALL, DEPENDENCIES] libservlet2.4-java
[INSTALL, DEPENDENCIES] libservlet2.5-java
[INSTALL, DEPENDENCIES] libslf4j-java
[INSTALL, DEPENDENCIES] libxerces2-java
[INSTALL, DEPENDENCIES] libxt-dev
[INSTALL, DEPENDENCIES] openjdk-6-jdk
[INSTALL, DEPENDENCIES] openjdk-6-jre
[INSTALL, DEPENDENCIES] openjdk-6-jre-headless
[INSTALL, DEPENDENCIES] openjdk-6-jre-lib
[INSTALL, DEPENDENCIES] realpath
[INSTALL, DEPENDENCIES] sat4j
[INSTALL, DEPENDENCIES] tzdata-java
[INSTALL] eclipse
===============================================================================

Log complete.
Aptitude 0.4.11.11: log report
Fri, Oct  7 2011 22:20:48 +0800

IMPORTANT: this log only lists intended actions; actions which fail due to
dpkg problems may not be completed.

Will install 0 packages, and remove 0 packages.
===============================================================================
===============================================================================

Log complete.
Aptitude 0.4.11.11: log report
Fri, Oct  7 2011 22:23:30 +0800

IMPORTANT: this log only lists intended actions; actions which fail due to
dpkg problems may not be completed.

Will install 0 packages, and remove 63 packages.
395MB of disk space will be freed
===============================================================================
[REMOVE, NOT USED] ant
[REMOVE, NOT USED] ant-gcj
[REMOVE, NOT USED] ant-optional
[REMOVE, NOT USED] ant-optional-gcj
[REMOVE, NOT USED] ca-certificates-java
[REMOVE, NOT USED] default-jdk
[REMOVE, NOT USED] default-jre
[REMOVE, NOT USED] default-jre-headless
[REMOVE, NOT USED] eclipse-jdt
[REMOVE, NOT USED] eclipse-pde
[REMOVE, NOT USED] eclipse-platform
[REMOVE, NOT USED] eclipse-platform-data
[REMOVE, NOT USED] eclipse-plugin-cvs
[REMOVE, NOT USED] eclipse-rcp
[REMOVE, NOT USED] fastjar
[REMOVE, NOT USED] gcj-4.4-base
[REMOVE, NOT USED] gcj-4.4-jre-lib
[REMOVE, NOT USED] icedtea-6-jre-cacao
[REMOVE, NOT USED] jarwrapper
[REMOVE, NOT USED] junit
[REMOVE, NOT USED] junit4
[REMOVE, NOT USED] libaccess-bridge-java
[REMOVE, NOT USED] libaccess-bridge-java-jni
[REMOVE, NOT USED] libasm3-java
[REMOVE, NOT USED] libcommons-beanutils-java
[REMOVE, NOT USED] libcommons-codec-java
[REMOVE, NOT USED] libcommons-collections3-java
[REMOVE, NOT USED] libcommons-compress-java
[REMOVE, NOT USED] libcommons-digester-java
[REMOVE, NOT USED] libcommons-el-java
[REMOVE, NOT USED] libcommons-httpclient-java
[REMOVE, NOT USED] libcommons-logging-java
[REMOVE, NOT USED] libdb-je-java
[REMOVE, NOT USED] libdb4.7-java
[REMOVE, NOT USED] libdb4.7-java-gcj
[REMOVE, NOT USED] libecj-java
[REMOVE, NOT USED] libequinox-osgi-java
[REMOVE, NOT USED] libgcj-bc
[REMOVE, NOT USED] libgcj-common
[REMOVE, NOT USED] libgcj10
[REMOVE, NOT USED] libhamcrest-java
[REMOVE, NOT USED] libicu4j-java
[REMOVE, NOT USED] libjasper-java
[REMOVE, NOT USED] libjaxp1.3-java
[REMOVE, NOT USED] libjetty-java
[REMOVE, NOT USED] libjline-java
[REMOVE, NOT USED] libjsch-java
[REMOVE, NOT USED] libjtidy-java
[REMOVE, NOT USED] liblucene2-java
[REMOVE, NOT USED] libregexp-java
[REMOVE, NOT USED] libservlet2.4-java
[REMOVE, NOT USED] libservlet2.5-java
[REMOVE, NOT USED] libslf4j-java
[REMOVE, NOT USED] libxerces2-java
[REMOVE, NOT USED] libxt-dev
[REMOVE, NOT USED] openjdk-6-jdk
[REMOVE, NOT USED] openjdk-6-jre
[REMOVE, NOT USED] openjdk-6-jre-headless
[REMOVE, NOT USED] openjdk-6-jre-lib
[REMOVE, NOT USED] realpath
[REMOVE, NOT USED] sat4j
[REMOVE, NOT USED] tzdata-java
[REMOVE] eclipse
===============================================================================

Log complete.
Aptitude 0.4.11.11: log report
Fri, Oct  7 2011 22:24:30 +0800

IMPORTANT: this log only lists intended actions; actions which fail due to
dpkg problems may not be completed.

Will install 42 packages, and remove 0 packages.
198MB of disk space will be used
===============================================================================
[INSTALL, DEPENDENCIES] ant
[INSTALL, DEPENDENCIES] ant-gcj
[INSTALL, DEPENDENCIES] ant-optional
[INSTALL, DEPENDENCIES] ant-optional-gcj
[INSTALL, DEPENDENCIES] eclipse-platform-data
[INSTALL, DEPENDENCIES] eclipse-rcp
[INSTALL, DEPENDENCIES] fastjar
[INSTALL, DEPENDENCIES] gcj-4.4-base
[INSTALL, DEPENDENCIES] gcj-4.4-jre-lib
[INSTALL, DEPENDENCIES] jarwrapper
[INSTALL, DEPENDENCIES] libcommons-beanutils-java
[INSTALL, DEPENDENCIES] libcommons-codec-java
[INSTALL, DEPENDENCIES] libcommons-collections3-java
[INSTALL, DEPENDENCIES] libcommons-compress-java
[INSTALL, DEPENDENCIES] libcommons-digester-java
[INSTALL, DEPENDENCIES] libcommons-el-java
[INSTALL, DEPENDENCIES] libcommons-httpclient-java
[INSTALL, DEPENDENCIES] libcommons-logging-java
[INSTALL, DEPENDENCIES] libdb-je-java
[INSTALL, DEPENDENCIES] libdb4.7-java
[INSTALL, DEPENDENCIES] libdb4.7-java-gcj
[INSTALL, DEPENDENCIES] libecj-java
[INSTALL, DEPENDENCIES] libequinox-osgi-java
[INSTALL, DEPENDENCIES] libgcj-bc
[INSTALL, DEPENDENCIES] libgcj-common
[INSTALL, DEPENDENCIES] libgcj10
[INSTALL, DEPENDENCIES] libicu4j-java
[INSTALL, DEPENDENCIES] libjasper-java
[INSTALL, DEPENDENCIES] libjaxp1.3-java
[INSTALL, DEPENDENCIES] libjetty-java
[INSTALL, DEPENDENCIES] libjline-java
[INSTALL, DEPENDENCIES] libjsch-java
[INSTALL, DEPENDENCIES] libjtidy-java
[INSTALL, DEPENDENCIES] liblucene2-java
[INSTALL, DEPENDENCIES] libregexp-java
[INSTALL, DEPENDENCIES] libservlet2.4-java
[INSTALL, DEPENDENCIES] libservlet2.5-java
[INSTALL, DEPENDENCIES] libslf4j-java
[INSTALL, DEPENDENCIES] libxerces2-java
[INSTALL, DEPENDENCIES] realpath
[INSTALL, DEPENDENCIES] sat4j
[INSTALL] eclipse-platform
===============================================================================

Log complete.
Aptitude 0.4.11.11: log report
Sat, Oct  8 2011 13:05:55 +0800

IMPORTANT: this log only lists intended actions; actions which fail due to
dpkg problems may not be completed.

Will install 0 packages, and remove 42 packages.
198MB of disk space will be freed
===============================================================================
[REMOVE, NOT USED] ant
[REMOVE, NOT USED] ant-gcj
[REMOVE, NOT USED] ant-optional
[REMOVE, NOT USED] ant-optional-gcj
[REMOVE, NOT USED] eclipse-platform-data
[REMOVE, NOT USED] eclipse-rcp
[REMOVE, NOT USED] fastjar
[REMOVE, NOT USED] gcj-4.4-base
[REMOVE, NOT USED] gcj-4.4-jre-lib
[REMOVE, NOT USED] jarwrapper
[REMOVE, NOT USED] libcommons-beanutils-java
[REMOVE, NOT USED] libcommons-codec-java
[REMOVE, NOT USED] libcommons-collections3-java
[REMOVE, NOT USED] libcommons-compress-java
[REMOVE, NOT USED] libcommons-digester-java
[REMOVE, NOT USED] libcommons-el-java
[REMOVE, NOT USED] libcommons-httpclient-java
[REMOVE, NOT USED] libcommons-logging-java
[REMOVE, NOT USED] libdb-je-java
[REMOVE, NOT USED] libdb4.7-java
[REMOVE, NOT USED] libdb4.7-java-gcj
[REMOVE, NOT USED] libecj-java
[REMOVE, NOT USED] libequinox-osgi-java
[REMOVE, NOT USED] libgcj-bc
[REMOVE, NOT USED] libgcj-common
[REMOVE, NOT USED] libgcj10
[REMOVE, NOT USED] libicu4j-java
[REMOVE, NOT USED] libjasper-java
[REMOVE, NOT USED] libjaxp1.3-java
[REMOVE, NOT USED] libjetty-java
[REMOVE, NOT USED] libjline-java
[REMOVE, NOT USED] libjsch-java
[REMOVE, NOT USED] libjtidy-java
[REMOVE, NOT USED] liblucene2-java
[REMOVE, NOT USED] libregexp-java
[REMOVE, NOT USED] libservlet2.4-java
[REMOVE, NOT USED] libservlet2.5-java
[REMOVE, NOT USED] libslf4j-java
[REMOVE, NOT USED] libxerces2-java
[REMOVE, NOT USED] realpath
[REMOVE, NOT USED] sat4j
[REMOVE] eclipse-platform
===============================================================================

Log complete.
Aptitude 0.4.11.11: log report
Sat, Oct  8 2011 15:32:02 +0800

IMPORTANT: this log only lists intended actions; actions which fail due to
dpkg problems may not be completed.

Will install 1 packages, and remove 0 packages.
7,569kB of disk space will be used
===============================================================================
[INSTALL] php5-cli
===============================================================================

Log complete.
Aptitude 0.4.11.11: log report
Fri, Oct 21 2011 01:16:48 +0800

IMPORTANT: this log only lists intended actions; actions which fail due to
dpkg problems may not be completed.

Will install 8 packages, and remove 0 packages.
9,339kB of disk space will be used
===============================================================================
[INSTALL, DEPENDENCIES] gnome-do-docklets
[INSTALL, DEPENDENCIES] libgdata1.4-cil
[INSTALL, DEPENDENCIES] libgnomedesktop2.20-cil
[INSTALL, DEPENDENCIES] libnotify0.4-cil
[INSTALL, DEPENDENCIES] librsvg2-2.18-cil
[INSTALL, DEPENDENCIES] libwnck2.20-cil
[INSTALL] gnome-do
[INSTALL] gnome-do-plugins
===============================================================================

Log complete.
Aptitude 0.4.11.11: log report
Fri, Oct 21 2011 01:18:43 +0800

IMPORTANT: this log only lists intended actions; actions which fail due to
dpkg problems may not be completed.

Will install 3 packages, and remove 0 packages.
3,256kB of disk space will be used
===============================================================================
[INSTALL, DEPENDENCIES] libmono-getoptions2.0-cil
[INSTALL, DEPENDENCIES] python-docky
[INSTALL] docky
===============================================================================

Log complete.
Aptitude 0.4.11.11: log report
Fri, Oct 21 2011 01:34:12 +0800

IMPORTANT: this log only lists intended actions; actions which fail due to
dpkg problems may not be completed.

Will install 0 packages, and remove 11 packages.
12.6MB of disk space will be freed
===============================================================================
[REMOVE, NOT USED] gnome-do-docklets
[REMOVE, NOT USED] libgdata1.4-cil
[REMOVE, NOT USED] libgnomedesktop2.20-cil
[REMOVE, NOT USED] libmono-getoptions2.0-cil
[REMOVE, NOT USED] libnotify0.4-cil
[REMOVE, NOT USED] librsvg2-2.18-cil
[REMOVE, NOT USED] libwnck2.20-cil
[REMOVE, NOT USED] python-docky
[REMOVE] docky
[REMOVE] gnome-do
[REMOVE] gnome-do-plugins
===============================================================================

Log complete.

```

---

### Post by lykwydchykyn on 2011-10-31
About when would you say that the upgrade which caused the problem happened?

As far as the log shows, the only update that has anything to do with php or apache is an update to php5-cli on the 8th.  The changelog for that update can be found here (assuming from the kernel version that you're on lucid):
[http://changelogs.ubuntu.com/changelogs/pool/main/p/php5/php5_5.3.2-1ubuntu4.10/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/p/php5/php5_5.3.2-1ubuntu4.10/changelog)

---

### Post by Wangberg on 2011-11-06
SOLVED:

There was nothing wrong with my system setup, i just had never experienced a parse error in the past which are not reported in the browser unless DISPLAY_ERRORS is ON in the php.ini .  It is PHP practice that sets these parameters and leads to an ERROR 500 message in the browser.  php.ini DISPLAY_ERRORS is default to OFF in production environment:

php.ini
```

; display_errors
;   Default Value: On
;   Development Value: On
;   Production Value: Off

```

and the corresponding line should be changed to:

```

display_errors = ON

```

I guess when i installed LAMP, it assumed i was working in a production environment.  

thanks for all your help

---

### Post by koenn on 2011-11-07
> **Wangberg said:**
> S  php.ini DISPLAY_ERRORS is default to OFF in production environment:


I guess when i installed LAMP, it assumed i was working in a production environment.  

thanks for all your help

yeah, that's it. 
It's possible older versions shipped with "development" params, that would explain why you expected such errors to be shown in the browser,
but it's getting more customary to tighten security a bit.

The reasoning is that errors that show up in the browser potentially reveal too much information about the underlying system, and triggering errors to get that kind of info is a basic attack/reconnaissance technique against websites/web servers.

---

