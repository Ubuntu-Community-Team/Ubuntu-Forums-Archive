---
title: "How do you get regular expressions working in PHP"
date: 2009-07-21
forum: Server Platforms
---

### Post by Captain_Glen on 2009-07-21
Hi,

I am trying to scrape a web page using PHP and curl but I don't understand regular expressions.  I have read a lot about them on the web but am totally lost.

Here is my code:
```
<?php
$url = 'http://www.acttab.com.au/interbet/odds?mting=MR01000';
$ch = curl_init($url);
curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
$raw = curl_exec($ch);
$newlines = array("\t","\n","\r","\x20\x20","\0","\x0B");
$content = str_replace($newlines, "", html_entity_decode($raw));

$start = strpos($content,'<table width=650 border=0 cellspacing=0 cellpadding=3');

// Plus 8 is wrong
$end = strpos($content,'</table>',$start) + 8;

$table = substr($content,$start,$end-$start);

var_dump($table);

preg_match_all("/<tr bgcolor=#eeeeee>(.*)</tr>/", $table, $eRows);
var_dump($eRows);
//preg_match_all("|<tr bgcolor=#bbbbbb>(.*)</tr>|U", $curl_scraped_page, $bRows);
//var_dump($bRows);
curl_close($ch);
echo $curl_scraped_page;
?>
```

I want to get the rows between <tr bgcolor=#eeeeee> and </tr> But I get this error:

```
Warning: preg_match_all() [function.preg-match-all]: Unknown modifier 't' in /var/www/php.php on line 18
NULL 
```

Any help would be appreciated.

---

### Post by t0mppa on 2009-07-22
Firstly, this isn't really a forum for programming advice, just for getting your Ubuntu networking issues set up. Simply migrating to another forum, like [Stack Overflow]("http://stackoverflow.com") will also give more thorough answers, as the folks there are more accustomed to explaining these things.

As per your problem, I haven't written any PHP in a while, but I believe your problem is the unescaped forward slash in the closing tag. Since you are using forward slashes as delimiters, ie. to define the beginning and end of the find pattern and anything after them will be interpreted as modifiers. So, your find pattern becomes: "<tr bgcolor=#eeeeee>(.*)<" and then the modifiers part is: "tr>/" and thus it complains from the t letter as it doesn't match any modifiers.

Simply putting a \ infront of the / to escape any special meaning for it and just use it as a string character should fix the error you're getting or then you can change the delimiters to some other character that is not encountered in the string, as PHP should support any delimiter. And adding the i modifier in the end means it's case insensitive, which usually comes in handy as HTML is case insensitive as well.

All in all, give this a try:```
preg_match_all("/<tr bgcolor=#eeeeee>(.*)<\/tr>/i", $table, $eRows);
```

---

### Post by Captain_Glen on 2009-07-22
Thanks, that worked! :)

---

