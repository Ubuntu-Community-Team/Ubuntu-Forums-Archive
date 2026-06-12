---
title: "Read text file data as Decimal vales using PHP"
date: 2012-01-12
forum: Server Platforms
---

### Post by jmknash on 2012-01-12
Hi all,

I have a script which I have sourced online which reads a text file and dumps the data as hexadecimal values on a page. How could this be modified to output decimal instead?

Is there a better code avail?


Code:

`<?php

$handle = @fopen("binarydu.txt", "r");
if ($handle) {
    while (!feof($handle)) {
        $hex = bin2hex(fread ($handle , 4 ));
        print $hex."\n";
    }
    fclose($handle);

}

?>`


Btw, I'm a noob :) 

Jon

---

### Post by ocia on 2012-01-13
[http://nl2.php.net/manual/en/function.hexdec.php](http://nl2.php.net/manual/en/function.hexdec.php)

At least if you know what you're expecting...
Could you otherwise provide an example of in and output?

Good luck!

---

### Post by jmknash on 2012-01-13
ocia,

Basically a command is sent to robotics hardware on a ubuntu platform requesting a battery voltage check and the value is written in a single ASCII value into a file.

Currently, character 't' can be read which translates as Hex=74 binary=1110100 or which I want it to show output on webpage as a decimal=116 (11.6 volt).

How could hexdec be tied into the script?

Thanks

---

### Post by ocia on 2012-01-13
I just found this on another forum:
[PHP]
<?php 
function bin2str($in) 
{ 
   $in = str_split($in, 8); // NOTE: this function is PHP5 only 
   for($i = 0, $n = count($in); $i < $n; ++$i) 
   { 
       $in[$i] = chr(bindec($in[$i])); 
   } 
   return implode('', $in); 
} 
?>
[/PHP]

The forum is: [http://www.codingforums.com/showthread.php?t=102643](http://www.codingforums.com/showthread.php?t=102643)

Hope this helps...
Otherwise, try Googling: "bin2str php" ;)

---

