---
title: "lamp stack"
date: 2009-03-25
forum: Server Platforms
---

### Post by macjak on 2009-03-25
I can't seem to get msql test script to run. After installing php and apache I then installed mysql. I have since read that "mysql support cannot be added later after php is compiled and installed" Mysql support is activated during php installation. I used the synaptic manager to reinstall php but I still can't connect with msql script. I'm able to login to the mysql monitor and php tests ok. When I run 'mysql -u root -p ping' it outputs "mysql is alive!" However when I run either the mysql or the mysqli version of the script I still get:
Fatal Error; call to undefined function mysql_connect() in /var/www/mysql_up.php.
<?php
/* Program: mysql_up.php
 * Desc:    Connects to MySQL Server and 
 *          outputs settings.
 */
 echo "<html>
       <head><title>Test MySQL</title></head>
       <body>";
 $host="localhost";
 $user="root";
 $password="mypassword";

 $cxn = mysql_connect($host,$user,$password);
 $sql="SHOW STATUS";
 $result = mysql_query($sql);
 if($result == false)
 {
    echo "<h4>Error: ".mysql_error($cxn)."</h4>";
 }
 else
 {
   /* Table that displays the results */
   echo "<table border='1'>
         <tr><th>Variable_name</th>
             <th>Value</th></tr>";
   for($i = 0; $i < mysql_num_rows($result); $i++) 
   {
     echo "<tr>";
     $row_array = mysql_fetch_row($result);
      for($j = 0;$j < mysql_num_fields($result);$j++) 
      {
         echo "<td>".$row_array[$j]."</td>\n";
      }
   }
   echo "</table>";
 }
?>
</body></html>

---

