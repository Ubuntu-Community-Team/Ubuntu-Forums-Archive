---
title: "PHP Count round thousand to a K style count like facebook Share . . . Twitter Button"
date: 2010-11-07
forum: Server Platforms
---

### Post by mrebanza on 2010-11-07
***Ok so I am trying to turn my hit counter to round thousands to a single digit too display 3 thousand hits as 3K for example . . . Like the Facebook Share and Twitter Tweet Buttons do . . . here is my code . . . any idea what I am doing wrong? ***

[PHP]$postresultscount = (($resultscount) ? $resultscount->sumCount : 1);
    $k = 1000;
    $L = '';
    if ($postresultscount > $k) { $echoxcount = round($postresultscount/$k); $L = 'K';
    } elseif ($postresultscount == $k) { $echoxcount = 1; $L = 'K';
    } else { $echoxcount = $postresultscount; }

    echo 'document.write("'.$echoxcount.' '.$L.'")';[/PHP]

PS I am using the Top 10 Plugin for Wordpress . . . It is pretty kick *** with a ton of featuring . . . you can grab yourself a copy here . . . [http://wordpress.org/extend/plugins/top-10/](http://wordpress.org/extend/plugins/top-10/)

---

### Post by wongo888 on 2010-11-07
[PHP]

class Result{
    public $sumCount = 0;
    function __construct($count){
        $this->sumCount = $count;
    }   
}

//$resultscount = new Result(1000);
//$resultscount = new Result(10000);
$resultscount = new Result(1234567);

$postresultscount = (($resultscount) ? $resultscount->sumCount : 1); 
$k = 1000;
if ($postresultscount >= $k) { 
  $echoxcount = round($postresultscount/$k).'K';
} else { 
  $echoxcount = $postresultscount; 
}

echo 'document.write("'.$echoxcount.'")';
[/PHP]

---

