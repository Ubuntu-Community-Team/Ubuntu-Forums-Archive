---
title: "Transfer php script"
date: 2009-07-24
forum: Server Platforms
---

### Post by Eviltechie on 2009-07-24
I'm trying to get a simple php script to work on my server. The script is supposed to return a value from a csv file. It works on my friends server, but it doesn't do anything on mine.

You can view his phpinfo() here [http://test.techmastertelecom.com/ivan/phpinfo.php](http://test.techmastertelecom.com/ivan/phpinfo.php)

And mine here [http://radio.awardia.net/phpinfo.php](http://radio.awardia.net/phpinfo.php)

And the script here...

```
<?php
$hostname = "http://wikicomphelp.com:8000/status2.xsl";

$file_handle = fopen($hostname, "r");

while (!feof($file_handle) ) {

$line_of_text = fgetcsv($file_handle, 1024);

}

fclose($file_handle);

//echo $line_of_text[2];
echo($line_of_text[5]);
//print_r($line_of_text);

$parts = explode(',', $line_of_text[2]);
$parts[5] = $current_song;

echo $current_song;

?>
```

---

