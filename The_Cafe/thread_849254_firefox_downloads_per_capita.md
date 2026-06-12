---
title: "firefox downloads per capita"
date: 2008-07-04
forum: The Cafe
---

### Post by howlingmadhowie on 2008-07-04
hi everybody.

i was quite bored at work today so i wrote this:

link gone...

it fetches the population list from wikipedia and the download numbers from firefox and combines them.

maybe someone will find it interesting

howie

---

### Post by Trail on 2008-07-04
Interesting :)

---

### Post by Canis familiaris on 2008-07-04
But it has no meaning. Most of the population does not have Computers. And many people would have downloaded Firefox multiple times

---

### Post by howlingmadhowie on 2008-07-07
i'd say it has some meaning. it shows the amount of downloads by people with computers without package managers who use firefox as a percentage of the population.

---

### Post by dominiquec on 2008-07-07
> i was quite bored at work today so i wrote this:

Boredom is the mother of invention. :)

---

### Post by fktt on 2008-07-07
Well, i still run feisty so i downloaded the tarball off of the homepage.

And not too bad for estonia, i suppose,
what with about 70% of estonians using internet
(but not all probably have their very own computeres).

:)

---

### Post by Masoris on 2008-07-07
It's hard to read, sort please.
Which country did first rank? Switzerland(4.05610465878%)???

---

### Post by howlingmadhowie on 2008-07-07
> **Masoris said:**
> It's hard to read, sort please.
Which country did first rank? Switzerland(4.05610465878%)???

here's the source. released under gpl3 or later.

if you build in a sorting function, i'll upload it :)
```
<?php
$downloadData=array();
$populationData=array();
$tmpArray=array();

$handle=fopen("http://www.spreadfirefox.com/en-US/worldrecord?showtable=true", "r");
$downloadString= stream_get_contents($handle);
fclose($handle);
$point=strpos($downloadString, "download_data");
$str=substr($downloadString, $point);
$point=strpos($str, "</tr>");

$str=substr($str, $point+5);

$point=strpos($str, "</table>");
$str=substr($str, 0, $point);

while($point=strpos($str, "</tr>")) {
  $tmpArray[]=substr($str, 0, $point);
  $str=substr($str, $point+5);
}

foreach($tmpArray as $entry) {
  $str=substr($entry, strpos($entry, "<td>")+4);
  $name=substr($str, 0, strpos($str, "</td>"));

  $str=substr($str, strpos($str, "<td>")+4);
  $downloads=substr($str, 0, strpos($str, "</td>"));

  $downloadData[trim($name)]=str_replace(",", "", trim($downloads));
}

//print_r($downloadData);



$handle=fopen("http://en.wikipedia.org/wiki/List_of_countries_by_population", "r");
$populationString=stream_get_contents($handle);
fclose($handle);

$point=strpos($populationString, "wikitable sortable");
$str=substr($populationString, $point+20);
$point=strpos($str, "</table>");
$str=substr($str, 0, $point);

$str=substr($str, strpos($str, "<tr>")+4);
$str=substr($str, strpos($str, "<tr>")+4);
$str=substr($str, strpos($str, "<tr>")+4); 

$tmpArray=array();
while($point=strpos($str, "</tr>")) {
    $tmpArray[]=substr($str, 0, $point);
    $str=substr($str, $point+5);
}

#$entry=$tmpArray[5];
foreach($tmpArray as $entry) {
   $str=substr($entry, strpos($entry, "<td>")+4);
   $str=substr($str, strpos($str, "<td"));

   $namestr=substr($str, 0, strpos($str, "</td>"));
   $namestr=substr($namestr, strpos($namestr, "</span>")+7);
   $namestr=substr($namestr, 0, strpos($namestr, "</a>"));
   $namestr=substr($namestr, strpos($namestr, '">')+2);

   $str=substr($str, strpos($str, "<td>")+4);
   $population=substr($str, 0, strpos($str, "<"));

   $populationData[trim($namestr)]=str_replace(",", "", trim($population));
}

//print_r($populationData);

echo "<html><head><title>pro nase</title></head><body><table>";

$count=0;
foreach(array_keys($populationData) as $popKey) {
   foreach(array_keys($downloadData) as $downKey) {
     if($downKey==$popKey || strpos(strtoupper($popKey), strtoupper($downKey))!=FALSE) {
       $percent=$downloadData[$downKey] / $populationData[$popKey] * 100;
       echo '<tr><td>'.$popKey.'</td><td>'.$populationData[$popKey].'</td><td>'.$downloadData[$downKey].'</td><td>'.$percent.' %</td></tr>';
       $count++;
       continue;
     }
  }
}

echo '</table>';
echo $count.' Treffer</body></html>';


?>
```

---

### Post by howlingmadhowie on 2008-07-13
i built in the sorting function myself :)

---

