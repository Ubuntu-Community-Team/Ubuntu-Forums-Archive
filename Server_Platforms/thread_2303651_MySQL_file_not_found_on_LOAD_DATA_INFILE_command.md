---
title: "MySQL file not found on LOAD DATA INFILE command"
date: 2015-11-20
forum: Server Platforms
---

### Post by bazianm on 2015-11-20
I am using:

MySQL 5.5.46-0ubuntu0.14.04.2.
PHP Version 5.5.9-1ubuntu4.14
CodeIgniter version 3.0.0

Scenario. User specifies two files which, upon submit are uploaded and properly named. I have confirmed that this works perfectly. 

After the files are uploaded, I copy them to the /tmp/ folder on the server and then send up a LOAD DATA command as follows:

[php]
$lcSQL = "LOAD DATA $local INFILE '$tcFile' " .
         "INTO TABLE `$tcTable` " .
         "FIELDS TERMINATED BY ',' " .
         "LINES TERMINATED BY '\\n' " .
         "IGNORE 1 LINES " .
         "(field list here, truncated for space) ";
$this->db->query($lcSQL);
[/php]

The table and file variables are passed through to the controller. 

OK, the bottom line is that I am getting a database error that the file I am passing through does not exist. Trouble is, it does. I have visually confirmed this.

Some more details:

1) I set the permissions of the file to 777
2) I checked the case and every character of the file name. It definitely exists.

I am kind of lost with this. I cannot figure out what is wrong here. I figure a permissions issue but I cannot imagine what it would be. If I am copying the file to /tmp/ and setting it to 0777, there should be no problem? 

Any thoughts on this?

Thanks in advance

---

