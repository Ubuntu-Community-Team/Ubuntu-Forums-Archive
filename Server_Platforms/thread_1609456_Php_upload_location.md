---
title: "Php upload location"
date: 2010-10-30
forum: Server Platforms
---

### Post by Cibico99 on 2010-10-30
I am running php on my ubuntu server, and I am trying to upload files to it. Heres my code:
```

<?php

$loc = '/var/www/upload/';


if ($_FILES["file"]["size"] > 0)
  {
  if ($_FILES["file"]["error"] > 0)
    {
    echo "Return Code: " . $_FILES["file"]["error"] . "<br />";
    }
  else
    {
    echo "Upload: " . $_FILES["file"]["name"] . "<br />";
    echo "Type: " . $_FILES["file"]["type"] . "<br />";
    echo "Size: " . ($_FILES["file"]["size"] / 1024) . " Kb<br />";
    echo "Temp file: " . $_FILES["file"]["tmp_name"] . "<br />";

    if (file_exists("upload/" . $_FILES["file"]["name"]))
      {
      echo $_FILES["file"]["name"] . " already exists. ";
      }
    else
      {
      move_uploaded_file($_FILES["file"]["tmp_name"],
      $loc . $_FILES["file"]["name"]);
      echo "Stored in: " . $loc . $_FILES["file"]["name"];
      }
    }
  }
else
  {
  echo "Invalid file";
  }
?> 

```
I use the move_uploaded_file(), but I can't get the location to work correctly. "/var/www/upload/" uploads to "/var/www/". This is the only way i can get this code to work. I would like to upload to "/var/www/upload/", any ideas?

---

### Post by SeijiSensei on 2010-10-30
Permissions?  The "www-data" user that Apache runs as must be able to write the file to /var/www/upload.  Try this:

```

cd /var/www
mkdir -p upload
sudo chown root.www-data upload
sudo chmod 0770 upload

```

This should let the Apache "user" write files into the upload directory.

Notice that I've limited rights to that directory to just root and members of group www-data.  Other users cannot see the uploaded files.  You might prefer 0775 permissions on upload to let other users see those files.

---

### Post by Cibico99 on 2010-10-31
I set up the permissions and it works perfectly. Thank you so much!

---

