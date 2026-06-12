---
title: "[SOLVED] tweaking php.ini (large file uploading)"
date: 2008-08-21
forum: Server Platforms
---

### Post by woodsonoversoul on 2008-08-21
Hello all,
I'm trying to upload several large (>100mb) flac files with a PHP script. I've been able to upload smaller files (small .txt files, images, etc.) but I can't make it work with the larger ones. Here is some of my info:

/////////////////////////////

php.ini:
;;;;;;;;;;;;;;;;
; File Uploads ;
;;;;;;;;;;;;;;;;

; Whether to allow HTTP file uploads.
file_uploads = On

; Temporary directory for HTTP uploaded files (will use system default if not
; specified).
;upload_tmp_dir =

; Maximum allowed size for uploaded files.
upload_max_filesize = 200M


;;;;;;;;;;;;;;;;;;;
; Resource Limits ;
;;;;;;;;;;;;;;;;;;;

max_execution_time = 30     ; Maximum execution time of each script, in seconds
max_input_time = 300 ; Maximum amount of time each script may spend parsing request data
;max_input_nesting_level = 64 ; Maximum input variable nesting level
memory_limit = 200M      ; Maximum amount of memory a script may consume (16MB)

//////////////////////////////

and here's the script:

```

<html>
<head></head>
<body>
<form action="<?=$PHP_SELF?>" method="post" enctype="multipart/form-data">
<br><br>
Choose a file to upload:<br>
<input type="file" name="upload_file">
<br>
<input type="submit" name="submit" value="submit">
</form>

<?php

	//set_time_limit(0);
	
	$file_name = $_FILES['upload_file']['name'];
	$tmp_file_name = $_FILES['upload_file']['tmp_name'];
	
	if(!is_uploaded_file($_FILES['upload_file']['tmp_name'])) {
		$error = "Please upload a file";
	}
	else {
		echo "correct! good job!";
		echo "Some file information: <br>";
		echo "You uploaded: $file_name <br>";
		}
		if((!empty($_FILES['upload_file'])) && ($_FILES['upload_file']['error'] == 0)) {
			echo "file succsesfully uploaded!<br>";
			copy($_FILES['upload_file']['tmp_name'],"/home/dan/Desktop/uploads/".$_FILES['upload_file']['name']);
			unlink($_FILES['upload_file']['tmp_name']);
		}
		else{ echo "file not uploaded yet<br>";}
		
		
	?>
</body>
</html>

```

//////////////////////////////////

Anyone see anything that might interfere with me uploading large files?

---

### Post by wirepuller134 on 2008-08-21
We have had complaints about uploads failing.  What we have discovered to be at fault most of the time is browser time outs on the users machine.  The average upload speed on a home network is very slow.

---

### Post by windependence on 2008-08-21
Do you get any error messages?

-Tim

---

### Post by cdenley on 2008-08-21
Try adding
```

<input type="hidden" name="MAX_FILE_SIZE" value="209715200" />

```

You might also want to check the LimitRequestBody setting in apache.
[http://httpd.apache.org/docs/2.2/mod/core.html#limitrequestbody](http://httpd.apache.org/docs/2.2/mod/core.html#limitrequestbody)

---

### Post by woodsonoversoul on 2008-08-21
Thanks cdenley!! That worked great! Can you translate that into MB?

---

