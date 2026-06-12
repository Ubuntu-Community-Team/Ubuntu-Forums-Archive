---
title: "htaccess"
date: 2009-07-07
forum: Server Platforms
---

### Post by kennedy7 on 2009-07-07
Hello all, I have a php script [http://bsat87.thruhere.net/jpg](http://bsat87.thruhere.net/jpg) that uploads jpg and png files. It works great, but i have one problem. If there is file named 1.jpg already on the server and you want to upload a file named 1.jpg it overwrites the file already on the server.
Is there a way i could keep it from happening, perhaps rename the file that is being upload to something like 1_.jpg so that it wont overwrite any pictures? would there be something i could put in my .htaccess file to keep overwriting from happening. Thanks in advance

---

### Post by MystaMax on 2009-07-07
This should probably be implemented in your php script. PHP has a file_exists function. Here is a link to it - [http://us.php.net/file_exists]("http://us.php.net/file_exists").

Here is a quick code snippet of how it'd be done:

[PHP]
<?php
$filename = '/path/to/foo.txt';

if (file_exists($filename)) {
    echo "The file $filename exists";
} else {
    echo "The file $filename does not exist";
}
?>
[/PHP]

DISCLAIMER: Code snippet above was taken directly from the PHP manual.

---

### Post by kennedy7 on 2009-07-07
Thank you man, ill try that

---

### Post by Thirtysixway on 2009-07-07
Boy scouts eh?  I do my troop's site.

I setup the site using Drupal.  Let's me restrict who can upload images and makes it easier to manage.  You could take a look at Drupal or another CMS if you're looking at controlling/giving users access to contribute content.

---

### Post by kennedy7 on 2009-07-30
What is your troop website

---

