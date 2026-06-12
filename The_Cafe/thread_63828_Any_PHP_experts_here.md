---
title: "Any PHP experts here?"
date: 2005-09-09
forum: The Cafe
---

### Post by xmastree on 2005-09-09
I'm trying to make a simple web gallery using [this](http://www.blazonry.com/scripting/photos1_how.php) method. It looks simple, and to add more pictures I just need to upload them, along with the GIF thumbnails.
However, while it works for him, it doesn't seem to work for me.  :neutral: 

The thumbnails are shown, but when I click one I don't see the image.
[Here](http://xmastree.34sp.com/test/gallery.php) is my attempt. There are six files there. c2-1.jpg c2-2.jpg, c2-3.jpg and their respective gifs. However, when I click a thumbnail, c2-1.gif, it tries to load c2-1.gif.jpg rather than c2-1.jpg.

I've modified the  original script by changing the background, and removing the -01 from the filename (the original had high res images reduced and renamed file-01.jpg, mine doesn't).

the bit that's going wrong seems to be this part:
```
$jpglink = substr($file, 0, 8);
echo "<td><a href=\"$jpglink.jpg\"><img src=\"$file\" height=\"$size[1]\" width=\"$size[0]\" border=\"0\" hspace=\"10\" vspace=\"20\"></a>";
```
Presumably $jpglink comes from the gif, but it's including the extension in the link.

---

### Post by heimo on 2005-09-09
It fails because it assumes file names to be longer, at least 8 chars + extension, I believe.

---

### Post by xmastree on 2005-09-09
Thanks. exactly 8 characters actually.
I renamed a couple of my files. the kids on the beach is 8 characters, another one is 9 but it chops off the last character.

So, it's 8 or nothing.
I guess that's what the 8 means here:
```
$jpglink = substr($file, 0, 8);
```
Cheers.

(I must learn to program someday)

---

### Post by Kvark on 2005-09-09
[QUOTE=xmastree]Thanks. exactly 8 characters actually.
I renamed a couple of my files. the kids on the beach is 8 characters, another one is 9 but it chops off the last character.

So, it's 8 or nothing.
I guess that's what the 8 means here:
```
$jpglink = substr($file, 0, 8);
```
Cheers.

(I must learn to program someday)[/QUOTE]
By guessing from memory I think the script will handle filenames of any length if that line is changed to:
```
$jpglink = substr($file, 0, strrpos($file,'.'));
```

---

### Post by JoshHendo on 2005-09-09
[QUOTE=Kvark]By guessing from memory I think the script will handle filenames of any length if that line is changed to:
```
$jpglink = substr($file, 0, strrpos($file,'.'));
```[/QUOTE]
 try this =\:

<?php
$jpglink = substr($file, 0, 8);
?>
<td><a href=\"<? echo ($jpglink.jpg); ?>\"><img src=\"<?php echo($file); ?>\" height=\"<? echo ($size[1]); ?>\" width=\"<? ($size[0]); ?>\" border=\"0\" hspace=\"10\" vspace=\"20\"></a>";
I have done something similar to that in the past :)

---

### Post by xmastree on 2005-09-09
[QUOTE=Kvark]By guessing from memory I think the script will handle filenames of any length if that line is changed to:
```
$jpglink = substr($file, 0, strrpos($file,'.'));
```[/QUOTE]
Excellent!

Thanks.

---

### Post by xmastree on 2005-09-09
[QUOTE=JoshHendo]try this =\:

<?php
$jpglink = substr($file, 0, 8);
?>[/quote]Smileys, eh? do they work in code?  :-P
Strange that the forum converts eight/bracket to colon/cool/colon

Look at Kvark's quote of the code I posted... bizarre.

---

### Post by JoshHendo on 2005-09-09
[QUOTE=xmastree]Smileys, eh? do they work in code?  :-P
Strange that the forum converts eight/bracket to colon/cool/colon

Look at Kvark's quote of the code I posted... bizarre.[/QUOTE]
 woops :P. 8)

---

### Post by majikstreet on 2005-09-09
xmastree:
I reccommend the book Beginning PHP 5 and MYSQL From Novice to Professional by W. Jason GIlmore


majikstreet

---

### Post by JoshHendo on 2005-09-11
[QUOTE=majikstreet]xmastree:
I reccommend the book Beginning PHP 5 and MYSQL From Novice to Professional by W. Jason GIlmore


majikstreet[/QUOTE]
 I reccoment the php.net documentation. Much cheaper :D

---

### Post by majikstreet on 2005-09-11
[QUOTE=JoshHendo]I reccoment the php.net documentation. Much cheaper :D[/QUOTE]
 It is very good there, but this is really an excellent book!

---

