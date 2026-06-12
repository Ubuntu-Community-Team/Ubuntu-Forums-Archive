---
title: "Daap itunes server - counter per user"
date: 2006-12-06
forum: Server Platforms
---

### Post by WzrdOfOost on 2006-12-06
Hello I wrote some php-code to check who played how many songs from my ubuntu daap music server.
[PHP]
<?php
$myFile = "mt-daapd.log";
$fh = fopen($myFile, 'r');
$theData = fread($fh, filesize($myFile));
fclose($fh);

$address = array('/172.19.3.22/','/172.19.3.19/','/172.19.3.18/') ;
$name = array(john, Joe, Lisa);
for ( $counter = 0; $counter <= 2; $counter += 1) {

if (preg_match_all($address[$counter], $theData, $user)) {
      echo $name[$counter]," ", count($user[0]), "<br />";
} else {
   echo $name[$counter]," did not play any songs";
}
}
?>
[/PHP]
check [my blog]("http://my-linux-server.blogspot.com") for my experiences with my music server.

---

