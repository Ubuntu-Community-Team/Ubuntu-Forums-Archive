---
title: "Easiest Way to Install Two Instances of MySQL on One Machine?"
date: 2007-05-20
forum: Server Platforms
---

### Post by mikestefff on 2007-05-20
Hey,

I was wondering what the easiest way is to install mysql twice on one machine, hopefully using apt so it can be removed easily if needed. Basically I am looking for the easiest way to be able to backup my main MySQL without having the tables lock, and I don't want to have a master/slave across two separate machines. If  you can suggest a better idea instead, that would be great.

Thanks,
Mike

---

### Post by mikestefff on 2007-05-21
Perhaps a link even?

---

### Post by DrNick on 2007-05-21
How about just copying everything in /var/lib/mysql onto your backups?

---

### Post by mikestefff on 2007-05-21
Without the tables being locked, doing that will (could) provide inaccurate backups. Especially as the tables grow and it takes longer to copy the files.

---

### Post by tturrisi on 2007-05-21
use a php script tp backup mysql or phpmyadmin>export

here's a script I have that will create a .SQL file of all tables in the db along w/ the data (including the create statements so can easily rebuild the db.:

```
<? 

// MySQL hostname

$host = "localhost";

//MySQL databasename

$dbname ="XXXXXXXX";

// MySQL user

$uname = "XXXXXXXX";

// MySQL password

$upass ="XXXXXXXX";

// set FALSE to get table content

$structure_only=false;

//set TRUE to to get file with dump

$output = true;





//////////////////////////////////////////////////

//

//  phpMyDump v 1.0

//

//  check for new version

//  http://szewo.com/php/mydump/eng

//

// some functions are adapted from the phpMyAdmin 

//

//  do not change anything below this line

//////////////////////////////////////////////////

function mysqlbackup($host,$dbname, $uid, $pwd, $structure_only, $crlf) {  

  

 $con=@mysql_connect("localhost",$uid, $pwd) or die("Could not connect");  

 $db=@mysql_select_db($dbname,$con) or die("Could not select db");



 // here we check MySQL Version

 $result=@mysql_query("SELECT VERSION() AS version"); 

 if ($result != FALSE && @mysql_num_rows($result) > 0) {

  $row   = @mysql_fetch_array($result);

  $match = explode('.', $row['version']);

 } else {

  $result=@mysql_query("SHOW VARIABLES LIKE \'version\'"); 

  if ($result != FALSE && @mysql_num_rows($result) > 0){

   $row   = @mysql_fetch_row($result);

   $match = explode('.', $row[1]);

  }

 }



 if (!isset($match) || !isset($match[0])) {

  $match[0] = 3;

 }

 if (!isset($match[1])) {

  $match[1] = 21;

 }

 if (!isset($match[2])) {

  $match[2] = 0;

 }

 if(!isset($row)) {

  $row = '3.21.0';

 }



 define('MYSQL_INT_VERSION', (int)sprintf('%d%02d%02d', $match[0], $match[1], intval($match[2])));

 define('MYSQL_STR_VERSION', $row['version']);

 unset($match);



 $sql = "# MySQL dump by phpMyDump".$crlf;

 $sql.= "# Host: $host Database: $dbname".$crlf;

 $sql.= "----------------------------".$crlf;

 $sql.= "# Server version: ".MYSQL_STR_VERSION.$crlf;



 $sql.= $crlf.$crlf.$crlf;     

 out(1,$sql);

 $res=@mysql_list_tables($dbname);  

 $nt=@mysql_num_rows($res);  



 for ($a=0;$a<$nt;$a++) {  

  $row=mysql_fetch_row($res);  

  $tablename=$row[0];



  $sql=$crlf."# ----------------------------------------".$crlf."# table structure for table '$tablename' ".$crlf;

  // For MySQL < 3.23.20  

  if (MYSQL_INT_VERSION >= 32321) {

   $result=mysql_query("SHOW CREATE TABLE $tablename");

   if ($result != FALSE && mysql_num_rows($result) > 0) {

    $tmpres = mysql_fetch_array($result);

    $pos           = strpos($tmpres[1], ' (');

    $tmpres[1]     = substr($tmpres[1], 0, 13)

                     . $tmpres[0]

                     . substr($tmpres[1], $pos);

				 

    $sql .= $tmpres[1].";".$crlf.$crlf;

   }

   mysql_free_result($result);

  } else { 

   $sql.="CREATE TABLE $tablename(".$crlf;  

   $result=mysql_query("show fields  from $tablename",$con);  



   while ($row = mysql_fetch_array($result)) {

    $sql .= "  ".$row['Field'];

    $sql .= ' ' . $row['Type'];

    if (isset($row['Default']) && $row['Default'] != '') {

     $sql .= ' DEFAULT \'' . $row['Default'] . '\'';

    }

    if ($row['Null'] != 'YES') {

     $sql .= ' NOT NULL';

    }

    if ($row['Extra'] != '') {

     $sql .= ' ' . $row['Extra'];

    }

    $sql .= ",".$crlf;

   }

 

   mysql_free_result($result);

   $sql = ereg_replace(',' . $crlf . '$', '', $sql);

 

   $result = mysql_query("SHOW KEYS FROM $tablename");

    while ($row = mysql_fetch_array($result)) {

     $ISkeyname    = $row['Key_name'];

     $IScomment  = (isset($row['Comment'])) ? $row['Comment'] : '';

     $ISsub_part = (isset($row['Sub_part'])) ? $row['Sub_part'] : '';

     if ($ISkeyname != 'PRIMARY' && $row['Non_unique'] == 0) {

      $ISkeyname = "UNIQUE|$kname";

     }

     if ($IScomment == 'FULLTEXT') {

      $ISkeyname = 'FULLTEXT|$kname';

     }

     if (!isset($index[$ISkeyname])) {

      $index[$ISkeyname] = array();

     }

     if ($ISsub_part > 1) {

      $index[$ISkeyname][] = $row['Column_name'] . '(' . $ISsub_part . ')';

     } else {

      $index[$ISkeyname][] = $row['Column_name'];

     }

    } 

    mysql_free_result($result);

    

    while (list($x, $columns) = @each($index)) {

     $sql     .= ",".$crlf;

     if ($x == 'PRIMARY') {

      $sql .= '  PRIMARY KEY (';

      } else if (substr($x, 0, 6) == 'UNIQUE') {

      $sql .= '  UNIQUE ' . substr($x, 7) . ' (';

     } else if (substr($x, 0, 8) == 'FULLTEXT') {

      $sql .= '  FULLTEXT ' . substr($x, 9) . ' (';

     } else {

      $sql .= '  KEY ' . $x . ' (';

     }

     $sql     .= implode($columns, ', ') . ')';

    } 

    $sql .=  $crlf.");".$crlf.$crlf;

  

  } 

  out(1,$sql);

 if ($structure_only == FALSE) {

  // here we get table content

  $result = mysql_query("SELECT * FROM  $tablename");

  $fields_cnt   = mysql_num_fields($result);

  while ($row = mysql_fetch_row($result)) {

   $table_list     = '(';

   for ($j = 0; $j < $fields_cnt; $j++) {

    $table_list .= mysql_field_name($result, $j) . ', ';

   }

   $table_list = substr($table_list, 0, -2);

   $table_list     .= ')';



   $sql = 'INSERT INTO ' . $tablename 

                                   . ' VALUES (';

   for ($j = 0; $j < $fields_cnt; $j++) {

    if (!isset($row[$j])) {

     $sql .= ' NULL, ';

    } else if ($row[$j] == '0' || $row[$j] != '') {

     $type          = mysql_field_type($result, $j);

     // a number

     if ($type == 'tinyint' || $type == 'smallint' || $type == 'mediumint' || $type == 'int' ||

                        $type == 'bigint'  ||$type == 'timestamp') {

      $sql .= $row[$j] . ', ';

     }

     // a string

     else {

      $dummy  = '';

      $srcstr = $row[$j];

      for ($xx = 0; $xx < strlen($srcstr); $xx++) {

       $yy = strlen($dummy);

       if ($srcstr[$xx] == '\\')   $dummy .= '\\\\';

       if ($srcstr[$xx] == '\'')   $dummy .= '\\\'';

       if ($srcstr[$xx] == "\x00") $dummy .= '\0';

       if ($srcstr[$xx] == "\x0a") $dummy .= '\n';

       if ($srcstr[$xx] == "\x0d") $dummy .= '\r';

       if ($srcstr[$xx] == "\x1a") $dummy .= '\Z';

       if (strlen($dummy) == $yy)  $dummy .= $srcstr[$xx];

      }

      $sql .= "'" . $dummy . "', ";

     }

    } else {

     $sql .= "'', ";

    } // end if

   } // end for

   $sql = ereg_replace(', $', '', $sql);

   $sql .= ");".$crlf;

   out(1,$sql);   



  } 

  mysql_free_result($result);

  } 

 }

 return;  

}  



function define_crlf() {

 global $HTTP_USER_AGENT;

 $ucrlf = "\n";

 if (strstr($HTTP_USER_AGENT, 'Win')) {

  $ucrlf = "\r\n";

 }

 else if (strstr($HTTP_USER_AGENT, 'Mac')) {

  $ucrlf = "\r";

 }

 else {

  $ucrlf = "\n";

 }

 return $ucrlf;

} 



//print the result

function out($fptr,$s)   { 

 echo $s; 

} 



if (ereg('Opera(/| )([0-9].[0-9]{1,2})', $HTTP_USER_AGENT, $log_version)) {

 define('USER_BROWSER_AGENT', 'OPERA');

} else if (ereg('MSIE ([0-9].[0-9]{1,2})', $HTTP_USER_AGENT, $log_version)) {

 define('USER_BROWSER_AGENT', 'IE');

} else if (ereg('OmniWeb/([0-9].[0-9]{1,2})', $HTTP_USER_AGENT, $log_version)) {

 define('USER_BROWSER_AGENT', 'OMNIWEB');

} else if (ereg('Mozilla/([0-9].[0-9]{1,2})', $HTTP_USER_AGENT, $log_version)) {

 define('USER_BROWSER_AGENT', 'MOZILLA');

} else if (ereg('Konqueror/([0-9].[0-9]{1,2})', $HTTP_USER_AGENT, $log_version)) {

 define('USER_BROWSER_AGENT', 'KONQUEROR');

} else {

 define('USER_BROWSER_AGENT', 'OTHER');

}



  $mime_type = (USER_BROWSER_AGENT == 'IE' || USER_BROWSER_AGENT == 'OPERA')

                   ? 'application/octetstream'

                   : 'application/octet-stream';



				   

$now = gmdate('D, d M Y H:i:s') . ' GMT';

$filename = $dbname;

$ext = "sql";

$crlf = define_crlf();

// Send headers

if ($output == true) {

 header('Content-Type: ' . $mime_type);

 header('Expires: ' . $now);

 // lem9 & loic1: IE need specific headers

 if (USER_BROWSER_AGENT == 'IE') {

  header('Content-Disposition: inline; filename="' . $filename . '.' . $ext . '"');

  header('Cache-Control: must-revalidate, post-check=0, pre-check=0');

  header('Pragma: public');

 } else {

  header('Content-Disposition: attachment; filename="' . $filename . '.' . $ext . '"');

  header('Pragma: no-cache');

      

 }

 mysqlbackup($host,$dbname,$uname,$upass,$structure_only,$crlf);

} 

 else {

 echo "<html><body><pre>";

 echo htmlspecialchars(mysqlbackup($host,$dbname,$uname,$upass,$structure_only,$crlf));

 echo "</PRE></BODY></HTML>";

}

?>
```

---

### Post by mikestefff on 2007-05-21
Thank you but please reread my post. Backing up in general isn't the problem. I do that now. The problem is being able to backup correctly without locking the tables. I am pretty sure your script would require the tables to be locked, to ensure a correct backup. The database is the backend of a very active, live website, and i cannot freeze the site everytime I want to backup.

So I believe replication is the best option. And instead of having a master/slave across two systems, I want to just use one. I also believe the only way to achieve that is to install two instances of mysql on the same machine.

---

### Post by Brazen on 2007-05-21
Just a quick glance over tturrisi's script and it looks like it should copy the databases just fine without locking the tables.

If you want a simpler approach or just want to use a BASH script instead of php, check out the 'mysqldump' command.  It can copy the databases just fine without locking the database or causing any downtime whatsoever.

---

### Post by mikestefff on 2007-05-21
I'm sure it can perform the backup fine without locking, but I was told numerous times that such methods of backup, being done with the tables unlocked, produce unreliable backups.

With replication, I can lock the replicated database, back it up, then it will update itself once completed. 

So if there an easy way to set this up?

---

### Post by Brazen on 2007-05-21
As a long-time (though reluctant) database admin, I think whoever told you that does not know what he is talking about.  I've backuped up live databases using mysqldump before and used the copy for testing/development and never had a problem.  The way mysqldump works, there is no need or benefit from locking the tables.

However, to answer your question... There is no easy way.  [http://dev.mysql.com/doc/refman/5.0/en/multiple-servers.html](http://dev.mysql.com/doc/refman/5.0/en/multiple-servers.html)

I would highly suggest you read up on database backup on that same site though.
edit: went ahead and grabbed the link for ya: [http://dev.mysql.com/doc/refman/5.0/en/backup.html](http://dev.mysql.com/doc/refman/5.0/en/backup.html)

---

### Post by mikestefff on 2007-05-21
Ok, thank you, but I have to go with what every other person I've talked to is telling me.

Is there an easy to install mysql twice in Ubuntu, hopefully using apt?

---

### Post by Brazen on 2007-05-21
You are going with what others have said, versus the official MySQL documentation on doing backups?!  Suit yourself.

Pritay sure you won't find a way to install it twice using apt.  Best case is probably be able to install it once with apt and then compile a second instance the way that documenation says to.

---

### Post by mikestefff on 2007-05-22
Where in the documentation does it say that you can get accurate and reliable backups using mysqldump without the tables being locked on an active database??

i tried compiling and changing the socket but I can't get it to work.

---

### Post by mikestefff on 2007-05-22
"To get a consistent backup, do a LOCK TABLES on the relevant tables"

---

### Post by tturrisi on 2007-05-22
Well, depending on what your database is doing, and how the info is submitted, and what type of info is stored, you could always just create a new db called bak and alter your insert statements so the data is entered into two databases at the same time, then just run a cron job that gzips the bak db files themselves.  You could probably do this easily with one line of code that calls a separate php script which grabs the input from your forms and inserts the data into the second db.  You could even probably set a delay for when the second script executes so that if one submits a form the next page is displayed and the bak script executes after the data gets posted & submitted to the main db.

---

### Post by mikestefff on 2007-05-22
The problem with that is that while the copied db is locked and backing up, its not going to be able to receive the input. Once the backup is over, it will be left short. The beauty with replication is that the copy db can go offline for days then catch itself up from the logs.

So..can anyone help me install it twice? There was a decent tutorial on howtoforge but it wasnt ubuntu based and I couldn't get it to work.

---

### Post by Brazen on 2007-05-22
> **mikestefff said:**
> "To get a consistent backup, do a LOCK TABLES on the relevant tables"

Reread the first three paragraphs on that page.  That line you quoted is specifically talking about making a copy of the files directly (ie. doing something like "tar -cjf mysql.bak /var/lib/mysql").

> **mikestefff said:**
> Where in the documentation does it say that you can get accurate and reliable backups using mysqldump without the tables being locked on an active database??

On that same page:
"For InnoDB tables, it is possible to perform an online backup that takes no locks on tables; see Section 8.13, “mysqldump — A Database Backup Program”."

---

### Post by Brazen on 2007-05-22
Also, this isn't a competition.  If you were given misinformation, then that is not your fault.  But for reals, the official MySQL documentation backs me up on this, and I'm just trying to help.  I think the way you are going is unnecessary, going to be harder to maintain if you get it working in the first place, and just be a huge frustration when, as I quoted above, "it is possible to perform an online backup that takes no locks on tables."  That is assuming you are using InnoDB tables which is the default.

Good luck, whichever way you choose.

---

### Post by mikestefff on 2007-05-22
I don't remember you mentioning Innodb. Anyway, as of now I can't use it. 

Thanks for helping.

If anyone else is reading this - if someone could help me out with installing twice that would be great.

---

