---
title: "Ubuntu Server file Upload help"
date: 2011-07-20
forum: Server Platforms
---

### Post by bcdixon on 2011-07-20
I will preface this by saying that I am a complete ubuntu n00b.

i just installed Ubuntu Server on an old machine and I was playing around with some php scripts. I was trying to get a simple file upload script to work but I'm completely stumped.

I have run the exact same script with success on a local MAMP setup.


Here is the complete script:

[PHP]
<html>
<head>
<title>upload test</title>
</head>
<body>
      <form method='post' action='index.php' enctype='multipart/form-data'>
             <input type='hidden' name='MAX_FILE_SIZE' value='50000000'/>
             <input type='file' name='file1'/>
             <input type='submit' value='upload file'/>
      </form>

       <?php
              if (isset($_FILES['file1'])) {
                      $filetype = $_FILES['file1']['type'];
                      $filesize = $_FILES['file1']['size'];
                      $tmpname = $_FILES['file1']['tmp_name'];
                      $name = $_FILES['file1']['name'];
 
                       echo "file type: $filetype<br />";
                       echo "file size: $filesize<br />";
                       echo "file tmp_name: $tmpname<br />";
                       echo "file name: $name<br />";

              }
        ?>

</body>
</html>
[/PHP]

When I access this webpage in a browser and upload I file (for example named departing.jpg), the page reloads and displays:

file type: 
file size: 0
file tmp_name: 
file name: departing.jpg

I think it is an issue of file permissions but again I'm stumped. I have run chown
chown www-data:www-data /var
chown www-data:www-data /var/www
chown www-data:www-data upload/var/www/TestDir

And I have chown-ed for the directory that stores the temporary files (as declared in the php.ini)
chown www-data:www-data /var/tmp

I even tried chmod-ing all of the above directories to 777 (which I know is very insecure) and still no luck.

I also checked the php.ini file to make sure that file uploads were permitted and it is set to On. the maximum upload size is also considerably larger than the images I have been testing with.

please help!!!

Also sorry if this is not in the correct section, didn't really know where to post.

---

### Post by Entilza on 2011-07-20
[http://www.w3schools.com/php/php_file_upload.asp](http://www.w3schools.com/php/php_file_upload.asp)

---

### Post by bcdixon on 2011-07-20
Thanks I actually used this page as an example. Is there something I'm missing?

---

### Post by Entilza on 2011-07-20
You'll have to move the temp file afterwards but I think your problem lies somewhere in php/apache.  Your script worked on my test box.  Also you want it as index.php are you sure? as a default page?

Create a page "info.php"

<? phpinfo(); ?>

Check the upload sections.

---

### Post by bcdixon on 2011-07-20
Ok i created the info.php page and looked at the upload sections:

file_uploads: On
max_file_uploads: 20
upload_max_filesize:2M
upload_tmp_dir:no value

I had specified the upload_tmp_dir before (and called chown www-data:www-data /var/test) to test the file permissions but it gave me the same result so I have changed it back to the default which is apparently none.

any ideas?

Thanks again for your help.

---

### Post by Entilza on 2011-07-20
Mine has the same settings, and it's using /tmp for the temporary location.

Try using the example from the w3schools exactly just cut and paste everything and try again.

Is it actually doing the upload?

---

### Post by bcdixon on 2011-07-20
Well after 2 days of making no progress I finally gave up and reinstalled Ubuntu Server. Problem solved. The script uploads my file. I must have accidentally changed some permissions somewhere along the line. Thanks for the help.

---

