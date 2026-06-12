---
title: "php/apache permission issues"
date: 2009-09-20
forum: Server Platforms
---

### Post by MrBucket101 on 2009-09-20
I'm trying to have a simple php script upload a file to a directory on my server, the same directory as the script.

[http://mrbucket101.kicks-a*s.net/test/](http://mrbucket101.kicks-a*s.net/test/)

i am getting a permissions error in that it isn't allowed to move the file to the proper directory.
```
Warning: move_uploaded_file(/desktop.ini) [function.move-uploaded-file]: failed to open stream: Permission denied in /var/www/test/upload.php on line 29

Warning: move_uploaded_file() [function.move-uploaded-file]: Unable to move '/tmp/php4hkbcv' to '/desktop.ini' in /var/www/test/upload.php on line 29
Sorry, there was a problem uploading your file.
```

I've tried ```
chmod -R 0777,0775,0757, /var/www/test
``` and that didn't work.

I'm sure its a permissions issue of some sort, i just cant seem to figure it out.


here is my index.html:
```
<form enctype="multipart/form-data" action="upload.php" method="POST">
Please choose a file: <input name="uploaded" type="file" /><br />
<input type="submit" value="Upload" />
</form>
```

here is my php script.

```
<?php
$target = "/";
$target = $target . basename( $_FILES['uploaded']['name']) ;
$ok=1;

//This is our size condition
if ($uploaded_size > 350000)
{
echo "Your file is too large.<br>";
$ok=0;
}

//This is our limit file type condition
if ($uploaded_type =="text/php")
{
echo "No PHP files<br>";
$ok=0;
}

//Here we check that $ok was not set to 0 by an error
if ($ok==0)
{
Echo "Sorry your file was not uploaded";
}

//If everything is ok we try to upload it
else
{
if(move_uploaded_file($_FILES['uploaded']['tmp_name'], $target))
{
echo "The file ". basename($_FILES['uploadedfile']['name']). " has been uploaded"; 
}
else
{
echo "Sorry, there was a problem uploading your file.";
}
}
?> 
```


any help is appreciated.

Thanks :)


EDIT:

I've solved the problem. The script was trying to upload to an invalid directory, and the permissions warning was throwing me off i guess.

---

