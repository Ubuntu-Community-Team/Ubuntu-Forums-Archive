---
title: "Using Post File with Apache AB - PHP script"
date: 2008-10-15
forum: Server Platforms
---

### Post by IQRules on 2008-10-15
Here is my insert.php, 

$ cat insert.php
<?php
$mysqli = mysqli_connect("localhost", "joeuser", "somepass", "testDB"); 


if (mysqli_connect_errno()) { 
         printf("Connect failed: %s\n", mysqli_connect_error()); 
         exit(); 


} else { 


         $sql = "INSERT INTO testTable (testField) VALUES ('".$_POST["testfield"]."')"; 
         $res = mysqli_query($mysqli, $sql); 

         if ($res === TRUE) { 
                 echo "A record has been inserted."; 
         } else { 
                 printf("Could not insert record: %s\n", mysqli_error($mysqli)); 
         } 


         mysqli_close($mysqli); 



} 


$ cat insert_post.txt 
testfield=newone 

Is this correct here? 


$ ab -p ./insert_post.txt  [http://local/Sites/insert.php](http://local/Sites/insert.php) 


Is the insert_post.txt and insert.php required to be in the same subdir?

---

