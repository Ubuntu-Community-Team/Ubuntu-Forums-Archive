---
title: "Any PHP gurus here?"
date: 2009-12-06
forum: The Cafe
---

### Post by PartisanEntity on 2009-12-06
I noticed we have some fellow web developers here. I am quite a newbie at PHP, and trying to write a search script. I want to generate a link from a mysql_query result.

This is what I have so far but I get errors:

```
while($rowOne = mysql_fetch_array($content))
{
echo '<a href="searchmultiple.php?SearchTerm='.$rowOne['term'].'&FromLanguage='.$FromLanguage.'&SearchID='$rowOne['id'].'">'.$rowOne['term'].'</a>';
} 
```

Here is the error I get:

> Parse error: syntax error, unexpected T_VARIABLE, expecting ',' or ';' in /Applications/MAMP/htdocs/eilv/search.php on line 36  

Any idea what could be causing this? I can't see it.

:)

---

### Post by Sam on 2009-12-06
A dot is missing (in bold red below)...

```
while($rowOne = mysql_fetch_array($content))
{
echo '<a href="searchmultiple.php?SearchTerm='.$rowOne['term'].'&FromLanguage='.$FromLanguage.'&SearchID='**[COLOR="Red"].[/COLOR]**$rowOne['id'].'">'.$rowOne['term'].'</a>';
}
```


You can also put variables in the string to avoid too much concatenations. You may gain in clarity.
```
while($rowOne = mysql_fetch_array($content))
{
echo "<a href=\"searchmultiple.php?SearchTerm={$rowOne['term']}&FromLanguage={$FromLanguage}&SearchID={$rowOne['id']}\">{$rowOne['term']}</a>";
}
```

---

### Post by Bachstelze on 2009-12-06
You're missing a period before [font=monospace]$rowOne['id'][/font].

Also what Sam said.

---

### Post by NoaHall on 2009-12-06
I concur with the above statements.

When you get a error like the above, usually the best way to find the cause is to ask someone else to check. If you keep staring at it, you won't see it.

---

### Post by Mmmbopdowedop on 2009-12-06
[PHP]<? 
while($rowOne = mysql_fetch_array($content))
{
?>
<a href="searchmultiple.php?SearchTerm=<?php echo $rowOne['term']; ?>&FromLanguage=<?php echo $FromLanguage; ?>&SearchID=<? echo $rowOne['id']; ?>"><?php echo $rowOne['term']; ?></a>
<?
}
?>[/PHP]

I find it easier to close php for that section, keeps all the highlighting there, more readable. :)

---

### Post by Bachstelze on 2009-12-06
Also good practice says to replace & with &amp;.

---

### Post by PartisanEntity on 2009-12-07
Thanks everyone for all the great feedback and tips.

I stared at it for about 2 hours and could not see that the dot was missing :) *facepalm*

---

