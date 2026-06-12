---
title: "Help needed with a simple php script?"
date: 2010-10-06
forum: Server Platforms
---

### Post by Jose Catre-Vandis on 2010-10-06
Just want a very simple directory listing output, no real need for hyperlinks, preferably with a line space between items, that the end user can print out.

I have this code, just don't have the knowledge to make it do what I want.

> <?php
 if ($handle = opendir('.')) {
   while (false !== ($file = readdir($handle)))
      {
          if ($file != "." && $file != "..")
      {
              $thelist .= '<a href="'.$file.'">'.$file.'</a>';
          }
       }
  closedir($handle);
  }
?>
<P>List of files:</p>
<P><?=$thelist?></p>

Thanks

---

### Post by watom on 2010-10-06
In the simple case where your script is working but don't output the way you like, you can change this line :
$thelist .= '<a href="'.$file.'">'.$file.'</a>';
to
$thelist .= $file.'<br>';

Hope it helps,
Thomas

---

### Post by Jose Catre-Vandis on 2010-10-06
Thomas, that's great, thank you.

Here's my code now, I have included the directory name at the top
> <?php
if ($handle = opendir('.')) {
while (false !== ($file = readdir($handle)))
{
if ($file != "." && $file != "..")
{
$thelist .= $file.'<br><br>';
}
}
closedir($handle);
$dir = getcwd();
echo basename($dir);
}
?>
<P><?=$thelist?></p>

This outputs:

```
MyDirectory

File 1

File 2

File 3

dir.php
```

can i also stop the php file from showing up in the list?

---

### Post by Jose Catre-Vandis on 2010-10-06
Don't worry, found what I needed
> 
<?php
if ($handle = opendir('.')) {
while (false !== ($file = readdir($handle)))
{
if ($file != '.' && $file != '..' && $file != 'dir.php')
{
$thelist .= $file.'<br><br>';
}
}
closedir($handle);
$dir = getcwd();
echo basename($dir);

}
?>
<p><?=$thelist?></p>

Returns:
```
MyDirectory

File 1

File 2

File 3
```

---

### Post by Ryan Dwyer on 2010-10-06
You might be interested in looking up the glob() function ([http://php.net/glob](http://php.net/glob)). You can do things like glob('*.txt') which returns an array of only text files.

---

### Post by Jose Catre-Vandis on 2010-10-06
> **Ryan Dwyer said:**
> You might be interested in looking up the glob() function ([http://php.net/glob](http://php.net/glob)). You can do things like glob('*.txt') which returns an array of only text files.

Yes, have seen that in use in similar scripts. Thanks for your input.

---

### Post by Jose Catre-Vandis on 2010-10-07
Since implimenting the first script, I realised it wasn't sorting alpha/numerically, so had a dig about and found the following which provided much the same but with sorting
> 
<?php
$path = ".";
$narray=array();
$dir_handle = @opendir($path) or die("Unable to open $path");
//echo "Directory Listing of $path<br/>";
$i=0;
while($file = readdir($dir_handle))
{
         if ($file != '.' && $file != '..' && $file != 'dirlist.php' && $file != '.htaccess' && $file != 'dlf' && $file != 'index.php' && $file != 'ft2.php.old' && $file != 'ft2.php')
        {
                //echo "<a href='$path/$file'>$file</a><br/>";
                $narray[$i]=$file;
                $i++;
        }
}
sort($narray);

for($i=0; $i<sizeof($narray); $i++)
{
$thelist .= $narray[$i]. '<br/><br/>';
//echo "<a href=".chr(34).$path.$narray[$i].chr(34).">".$narray[$i]."</a><br/>";
}

//closing the directory
closedir($dir_handle);
$dir = getcwd();
$bas = basename($dir);
?>
<p><font face="Century Gothic, Arial, Verdana"><b><?=$bas?></b></font></p>
<br>
<br>
<p><font face="Century Gothic, Arial, Verdana"><?=$thelist?></font></p>
(I've done a bit of work on formatting the output too)

---

