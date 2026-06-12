---
title: "Error Message: could not find driver for PDO Connection"
date: 2017-06-01
forum: Server Platforms
---

### Post by bhg2 on 2017-06-01
I am trying to build a LAMP server.  Currently, I can use PHP to connect to MySQL with MYSQLI, but when I attempt to make a connection with PDO, I get "Error Message: could not find driver."  I have browsed this and other forums and attempted the solutions provided.  I changed localhost to 127.0.0.1, I enabled modules in the .ini file, and several other potential solutions, including using apt-get to install several suggested packages.  I am using all current software.  The text for the PDO connection is below.  My phpinfo() page includes a PDO section, which I have also pasted below.  Any help would be greatly appreciated.

<?php

session_start();

$DB_host = 'mysqpl:host=127.0.0.1;dbname=rtr';
$DB_user = 'xx';
$DB_pass = 'xx';


try
{
    $DB = new PDO($DB_host, $DB_user, $DB_pass);

}
catch(PDOException $e)
{
    $error_message= $e->getMessage();
    include('database_error.php');
    exit ();
}


?>
Link to screen shot:

[URL="https://ibb.co/fKfFkv"]https://ibb.co/fKfFkvnk

[/URL]

---

### Post by bhg2 on 2017-06-15
What additional information can I provide that would help to troubleshoot this problem?  Thanks.

---

