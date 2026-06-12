---
title: "file upload"
date: 2012-01-30
forum: Server Platforms
---

### Post by subhojit on 2012-01-30
hello, i am trying to do file upload in php using apache2 web server. I have used the code sample for file upload in php in w3schools.com. the problem is i cannot find where the uploaded gets stored. any help pls...

---

### Post by coffeecat on 2012-01-30
*Thread moved to **Server Platforms**.*

---

### Post by a2j on 2012-01-30
> **subhojit said:**
> hello, i am trying to do file upload in php using apache2 web server. I have used the code sample for file upload in php in w3schools.com. the problem is i cannot find where the uploaded gets stored. any help pls...

another example why you should never use "sample code" if you don't know what it does.

---

### Post by ruffEdgz on 2012-01-30
> **a2j said:**
> another example why you should never use "sample code" if you don't know what it does.
Agreed but lets see what we have here.

I think I found the sample code you are talking about here: [http://www.w3schools.com/php/php_file_upload.asp](http://www.w3schools.com/php/php_file_upload.asp)

If you scroll down, there is sample code for the front end part of the PHP code while the others are for the processing of the uploaded file.

Scroll down near the bottom of the page, you should see the section called 'Saving the Uploaded File', did you follow or understand the code there?

The whole code is important but this part is important when saving the uploaded file successfully:
```

    if (file_exists("upload/" . $_FILES["file"]["name"]))
      {
      echo $_FILES["file"]["name"] . " already exists. ";
      }
    else
      {
      move_uploaded_file($_FILES["file"]["tmp_name"],
      "upload/" . $_FILES["file"]["name"]);
      echo "Stored in: " . "upload/" . $_FILES["file"]["name"];
      }

```
In this example, its saving the file into a directory called 'upload/' which is probably in the apache2 root directory (I haven't done this example myself so I am guessing from my experience).

The first thing you will want to do is:
[LIST=1]
[*]Read the full PHP upload example
[*]Understand what is happening behind the scences
[*]Make sure all the parts are setup behind the scence (i.e. directories are there, files in place, etc...)
[*]After steps 1-3 are complete, try the example yourself
[/LIST]

Cheers!

---

### Post by subhojit on 2012-01-30
> **ruffEdgz said:**
> Agreed but lets see what we have here.

I think I found the sample code you are talking about here: [http://www.w3schools.com/php/php_file_upload.asp](http://www.w3schools.com/php/php_file_upload.asp)

If you scroll down, there is sample code for the front end part of the PHP code while the others are for the processing of the uploaded file.

Scroll down near the bottom of the page, you should see the section called 'Saving the Uploaded File', did you follow or understand the code there?

The whole code is important but this part is important when saving the uploaded file successfully:
```

    if (file_exists("upload/" . $_FILES["file"]["name"]))
      {
      echo $_FILES["file"]["name"] . " already exists. ";
      }
    else
      {
      move_uploaded_file($_FILES["file"]["tmp_name"],
      "upload/" . $_FILES["file"]["name"]);
      echo "Stored in: " . "upload/" . $_FILES["file"]["name"];
      }

```
In this example, its saving the file into a directory called 'upload/' which is probably in the apache2 root directory (I haven't done this example myself so I am guessing from my experience).

The first thing you will want to do is:
[LIST=1]
[*]Read the full PHP upload example
[*]Understand what is happening behind the scences
[*]Make sure all the parts are setup behind the scence (i.e. directories are there, files in place, etc...)
[*]After steps 1-3 are complete, try the example yourself
[/LIST]

Cheers!

i have understood the code and then tried. as you are saying the file gets saved in apache2 root dir, but there is no such directory called upload. i found this problem when i tried to upload the same file again and it didnt showed the error "file already exists'. i have ubuntu 11.04 OS

---

### Post by subhojit on 2012-01-30
> **a2j said:**
> another example why you should never use "sample code" if you don't know what it does.

yes mate i have understood that code and then tried. i had used that same code once in Windows and it worked there smoothly. and now, i am using ubuntu 11.04 OS for doing the same thing and cant find the uploaded files.

---

### Post by subhojit on 2012-01-30
> **subhojit said:**
> i have understood the code and then tried. as you are saying the file gets saved in apache2 root dir, but there is no such directory called upload. i found this problem when i tried to upload the same file again and it didnt showed the error "file already exists'. i have ubuntu 11.04 OS

hey buddy i found the solution. actually it was all permission ****

---

