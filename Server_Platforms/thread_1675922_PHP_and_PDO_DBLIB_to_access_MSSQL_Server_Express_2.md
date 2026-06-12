---
title: "PHP and PDO_DBLIB to access MSSQL Server Express 2005"
date: 2011-01-26
forum: Server Platforms
---

### Post by zbenta on 2011-01-26
I have to transfer some sites from one server to another and one of them accesses a MSSQLServer. I made the trasnferenceo of the sites and then i got an error regarding the database access. After some "googling" around i found that i had no enabled MSSQL access on my php. To solve this problem I installed freetds and PDO_DBLIB.
After the installation of this site i stopped getting the anoying error "driver not found" and got the following error:

```

Error!: SQLSTATE[01002] Adaptive Server connection failed (severity 9)

```I've setup a test page to allow the connection to my server:

```

<?php
 // define( 'INC_DIR', "../../../inc/" );                                                               
  define( 'INC_DIR', "/var/ESR/tools/inc/" );
  include( INC_DIR . "common.php" );
  include( INC_DIR . "login.php" );                                                                     
  
  $conServer      = connection( 'dblib', 'my_server_ip:1433' ,'my_db', 'my_user', 'my_pass', false )    ;
                                                                                                        
?>


```The connection is made using the following function:

```

function connection($driver, $host, $dbname, $user, $pass, $die = true )
{
 //  print( "[Connecting to database: $dbname - host: $host]" );
  try {
     $conn = new PDO("$driver:host=$host;dbname=$dbname", $user, $pass /*, array( PDO::FETCH_ASSOC )*/ );
     $conn->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
  }
  catch (PDOException $e) {

     print "Error!: " . $e->getMessage() . "<br />";
     if ( !$die ) return null;
     die();
  }
  return $conn;
}


```my php has the following configuration regarding PDO:

$ php -i | grep PDO
PDO
PDO support => enabled
PDO drivers => dblib, mysql
PDO Driver for FreeTDS/Sybase DB-lib => enabled
PDO Driver for MySQL => enabled

if i try:
 $ telnet  my_ip  1433 
I can access the mssql server

Can anyone give me a hand on this one?

---

