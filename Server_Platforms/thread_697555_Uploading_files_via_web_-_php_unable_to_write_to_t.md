---
title: "Uploading files via web - php unable to write to /tmp"
date: 2008-02-15
forum: Server Platforms
---

### Post by socktan on 2008-02-15
Hi All

I am a bit of a loss while trying to write a short and sweet upload file php script on a local web server running Ubuntu 6.06LTS.

My test file is a small 16KB file called image.jpg.  

I think my issue lies within the web-data user being unable to write to /tmp, but I'm not sure.  I've set /tmp to 777 and left the user/group as root.  

 I'm hoping someone can help point me in the right direction in trouble shooting.

Here is the php code I'm using...

```


<?
print_r($_POST);

if($_POST["action"] == "Upload Image")
{
unset($imagename);

if(!isset($_FILES) && isset($HTTP_POST_FILES))
$_FILES = $HTTP_POST_FILES;
?>
<pre>
<? print_r($_FILES);?>
</pre>

<?

if(!isset($_FILES['image_file']))
$error["image_file"] = "An image was not found.";


$imagename = basename($_FILES['image_file']['name']);
 $imagename;

if(empty($imagename))
$error["imagename"] = "The name of the image was not found.";

if(empty($error))
{
$newimage = "/upload/" . $imagename;
echo $newimage;
$result = @move_uploaded_file($_FILES['image_file']['tmp_name'], $newimage);
if(empty($result))
$error["result"] = "There was an error moving the uploaded file.";
}

}

?>


<form method="POST" enctype="multipart/form-data" name="image_upload_form" action="<?$_SERVER["PHP_SELF"];?>">
<p><input type="file" name="image_file" size="20"></p>
<p><input type="submit" value="Upload Image" name="action"></p>
</form>

<?
if(is_array($error))
{
while(list($key, $val) = each($error))
{
echo $val;
echo "<br>\n";
}
}
?>
```

And the output, minus html entities:

```

Array ( [action] => Upload Image )

Array
(
    [image_file] => Array
        (
            [name] => image.jpg
            [type] => image/jpeg
            [tmp_name] => /tmp/phpz66ueY
            [error] => 0
            [size] => 13110
        )

)

/upload/image.jpg

```

I don't know the status of [error] in $image_file, if I look in /tmp/ on the ubuntu server, the file does not exist.  

I've set /tmp to 777 (user root/group root) which hasn't helped much.

I have limited knowledge of php - perhaps the problem exists in the script.  I'm not sure, so I'm looking for any type of help.

Thanks in advance,

-
Chris.

---

### Post by astrotech226 on 2008-02-15
This actually looks OK.  Are you sure the problem isn't that you can't write to the /upload directory?  PHP will remove the temp file when the script is done and that's why you can't see it.  A quick and easy test is to copy the temp file to another name in the /tmp directory.  You will see that copy at the end of the script.

Change this line and see what happens:

```
$newimage = "/tmp/" . $imagename;
```

You should see /tmp/image.jpg if all went well.

---

### Post by socktan on 2008-02-15
Thanks for the reply, you are exactly right.

The image is uploading but not able to copy to the /upload/ directory - the reason?  because /upload/ doesn't exist, first of all.

I needed to specify the full path to the upload directory in /var/www/web/upload rather than just /upload/

Thanks again for your help - the problem was so simple that I was over looking it.

Cheers!

--
Chris.

---

