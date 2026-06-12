---
title: "Php error."
date: 2009-05-11
forum: Server Platforms
---

### Post by dragos240 on 2009-05-11
I was uploading an upload script to my website, for a simple desktop upload site much like ourdesktops.com, oddly, it just displays the contents of the file: Here is the file:
```

$target_path = "";

$target_path = $target_path . basename( $_FILES['uploadedfile']['name']); 

if(move_uploaded_file($_FILES['uploadedfile']['tmp_name'], $target_path)) {
    echo "The file ".  basename( $_FILES['uploadedfile']['name']). 
    " has been uploaded";
} else{
    echo "There was an error uploading the file, please try again!";
}


```

---

### Post by Dr Small on 2009-05-11
Your post is very vague. 
Is your file extension name **.php**, and did you include the Php header and footer tags, like this?
[php]<?php
$target_path = "";

$target_path = $target_path . basename( $_FILES['uploadedfile']['name']); 

if(move_uploaded_file($_FILES['uploadedfile']['tmp_name'], $target_path)) {
    echo "The file ".  basename( $_FILES['uploadedfile']['name']). 
    " has been uploaded";
} else{
    echo "There was an error uploading the file, please try again!";
}
?>[/php]

---

### Post by trentscott4 on 2009-05-11
Check out [http://extplorer.sf.net](http://extplorer.sf.net) or [http://ajaxplorer.info](http://ajaxplorer.info).

I've worked on both projects and you might find them more to your liking.  :)

---

