---
title: "Error logging in to PhpPgAdmin"
date: 2010-05-07
forum: Server Platforms
---

### Post by TylerF on 2010-05-07
PhpPgAdmin worked fine until yesterday. I can't be sure what's caused the problem but I do know that it was working fine after I upgraded to 10.04 but after applying some updates yesterday I'm having this problem. Now when I try to login the right frame goes blank and on the left pane I see an error:

Error Loading all_db.php?subject=server&action=tree&server=localhost%3A5432%3Aallow (500: Internal Server Error)

Nothing related shows in the postgresql logs but in the apache logs I keep seeing this:

> PHP Fatal error:  Class 'ADODB_BASE_RS' not found in /usr/share/phppgadmin/libraries/adodb/adodb.inc.php on line 2704,     referer: [http://localhost/phppgadmin/browser.php](http://localhost/phppgadmin/browser.php)

I've had a look at that bit of code and it looks like this:

[PHP]
	//==============================================================================================	
	// CLASS ADORecordSet
	//==============================================================================================	

	if (PHP_VERSION < 5) include_once(ADODB_DIR.'/adodb-php4.inc.php');
	else include_once(ADODB_DIR.'/adodb-iterator.inc.php');
	/**
	 * RecordSet class that represents the dataset returned by the database.
	 * To keep memory overhead low, this class holds only the current row in memory.
	 * No prefetching of data is done, so the RecordCount() can return -1 ( which
	 * means recordcount not known).
	 */
	class ADORecordSet extends ADODB_BASE_RS {
[/PHP]
Line 2704 is the last line given and ADODB_BASE_RS is defined in both adodb-php4.inc.php and adodb-iterator.inc.php
Also ADODB_DIR is '/usr/share/phppgadmin/libraries/adodb' and both the adodb-php4.inc.php and adodb-iterator.inc.php files are in that directory.

If I change the above 'include_once' to just 'include' then the right frame shows this:

> Syntax error in file: /usr/share/phppgadmin/libraries/adodb/drivers/adodb-postgres7.inc.php
ADONewConnection error: [-998: could not load the database driver for ''] in ADONewConnection(, )

And the Apache error log shows this:

> PHP Fatal error:  Call to a member function setFetchMode() on a non-object in /usr/share/phppgadmin/classes/database/Co    nnection.php on line 24, referer: [http://localhost/phppgadmin/browser.php](http://localhost/phppgadmin/browser.php)

I could just keep poking around the code, but I thought I would ask here to see if anyone had an idea about what's going on. Oh and I forgot to mention I've tried removing and reinstalling PhpPgAdmin using sudo apt-get --purge remove phppgadmin 
Any help would be much appreciated :)

---

### Post by TylerF on 2010-05-17
Looks like uninstalling the php-apc packaged fixed it for me.

---

