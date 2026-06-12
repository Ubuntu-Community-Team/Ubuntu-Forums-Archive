---
title: "PHP scraping Help"
date: 2009-09-06
forum: Server Platforms
---

### Post by zuber786 on 2009-09-06
I am trying to scrap table of gas prices from this website, but my mind is not working anymore
Please help me out.

this site I am trying to scrap from
```
http://www.sanantoniogasprices.com/
```


i am trying to get whole table which shows gas prices

this is the code I got

[PHP]

<?php


$url = "http://www.sanantoniogasprices.com/";
$raw = file_get_contents($url);
$newlines = array("\t","\n","\r","\x20\x20","\0","\x0B");

$content = str_replace($newlines, "", html_entity_decode($raw));
$start = strpos($content,'<table cellpadding="3" class="standard_table"');

$end = strpos($content,'</table>',$start) + 7;

$table = substr($content,$start,$end-$start);
preg_match_all("|<tr(.*)</tr>|U",$table,$rows);

foreach ($rows[0] as $row){



if ((strpos($row,'<th')===false)){

	preg_match_all("|<span(.*)</span>|U",$row,$cells);

		$rate = strip_tags($cells[0][0]);

	preg_match_all("|<td(.*)</td>|U",$row,$cells);

		$name = strip_tags($cells[0][1]);

	preg_match_all("|<a(.*)</a>|U",$row,$cells);

		$number = strip_tags($cells[0][0]);


echo "$number<br>";

}
}[/PHP]

---

