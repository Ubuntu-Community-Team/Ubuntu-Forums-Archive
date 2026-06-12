---
title: "Ubuntu Apache-based File Upload/Directory"
date: 2012-02-15
forum: Server Platforms
---

### Post by hateborne on 2012-02-15
Evening ladies, gents, and trolls.

I am trying to setup a VERY basic site to host simple files. From my understanding, not putting an index.html (or some type of 'page') will cause Apache to spit up a 'files-in-directory' list. This is exactly what I need and works very well (this is intended to be anonymously accessed).

Now, the fun part. For uploads, I would like to require some sort of basic login. I would love to have it authenticate against Ubuntu as I am extremely lazy like that. If not, that is fine too. I just have no idea where I should begin.

My ghetto-ized solution to the directory browsing was to start with:
[B]/home/apache/public_html/index.html
[/B]
Then branch out to (intentionally missing index.html):
[B]/home/apache/public_html/addons
/home/apache/public_html/ui_files
/home/apache/public_html/scripts
/home/apache/public_html/misc[/B]

Would GREATLY appreciate any info as I literally knew nothing about PHP or HTML yesterday afternoon when I started this. My very feeble (and experimental) index.html and upload_file.php are below. I would also appreciate any basic security pointers. I am not looking to create the digital equivalent of Fort Knox, nor do I want a straw house.

index.html
```
<html>
<body>
<h1>File Uploader</h1>
<p>Select a File, Select a Path, Hit Upload</p>
<form action="upload_file.php" method="post"
enctype="multipart/form-data">
<label for="file">Filename:</label>
<input type="file" name="file" id="file" />
<br />
<br />
<select name="dstLoc">
    <option>Choose a Path...</option>
    <option>addons</option>
    <option>ui_files</option>
    <option>scripts</option>
    <option>misc</option>
</select>
<br />
<br />
<input type="submit" name="submit" value="Submit" />
</form>

</body>
</html> 
```upload_file.php
```
<?php

$max_filesize = 31457280;

if ($_FILES["file"]["error"] > 0)
  {
  echo "Error: " . $_FILES["file"]["error"] . "<br />";
  }
else
  {
  
   if (file_exists($_POST["dstLoc"] . "/" . $_FILES["file"]["name"]))
    {
      echo $_FILES["file"]["name"] . " already exists. ";
    }
   elseif ($_POST["dstLoc"] == "Choose a Path...")
    {    
    echo "A path must be selected to upload. Please try again";
    }
   else
    {
    echo "Upload: " . $_FILES["file"]["name"] . "<br />";
      echo "Type: " . $_FILES["file"]["type"] . "<br />";
      echo "Size: " . fileSizeUp($_FILES["file"]["size"]) . "<br />";
    move_uploaded_file($_FILES["file"]["tmp_name"],
    $_POST["dstLoc"] . "/" . $_FILES["file"]["name"]);
    echo "Stored in: /" . $_POST["dstLoc"] . "/" . $_FILES["file"]["name"];
    }
  }

function fileSizeUp($fs)
{
    $fs_temp = 0;
    $fs_temp = ($fs / 1024);
    if ($fs_temp > 1023)
        {
        $fs_temp = number_format(($fs_temp / 1024), 2);
        $fs_temp = $fs_temp . "MB";
        return $fs_temp;
        }
    else
        {
        $fs_temp = number_format(($fs_temp), 2);
        $fs_temp = $fs_temp . "KB";
        return $fs_temp;
        }
}
?>
```-Hate


(P.S. - Ubuntu 11.10 x86 Server)

---

