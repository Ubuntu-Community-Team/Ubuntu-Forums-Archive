---
title: "permission uploading graph output by script"
date: 2015-06-20
forum: Server Platforms
---

### Post by monkeybrain20122 on 2015-06-20
Hi, 

The setup of my server is like this

webroot is in /srv/www/webtest
output directory is /srv/www/webtest/outputs

The permissions are 
```
drwxr-x--- 3 monkeybrain www-data  webtest

drwxrwx--- 2 monkeybrain www-data  outputs

```
I run a script in apache to create a graph in the outputs folder /src/www/webtest/output

Its permissions are 
```

-rw-r--r-- 1 www-data www-data  graph.png
```

Now I am trying to retrieve the graph and show it on the browser. I test with a html script call testupload.html in the webtest directory 
testupload.html

```
<!DOCTYPE html>
<html>
    <head>
    <title>test upload path</title>
    </head>

    <body>
        <h1>
             graph
            <p><img src="outputs/graph.png"/></p>
        </h1>

    </body>
</html>





```

I call testupload.html from the browser but it always shows a brolken icon instead of the graph. It is a permission issue because if I change the owner of the graph to myself then it shows.

I want to be able to run the test script, for it to produce a graph in /srv/www/webtest/outputs and show it on the browser. What should I do? Thanks.

---

### Post by monkeybrain20122 on 2015-06-20
Hi, can a moderator please correct the typo in the title please? (outut to output) Thanks.

---

### Post by bapoumba on 2015-06-20
Done (and that is what reporting a thread can also be used for) :)

---

### Post by TheFu on 2015-06-20
Try
            ```
<p><img src="/outputs/graph.png"/></p>
```

Doesn't look like a permissions issue from here, though I would setgid the directory.

Also - I'm not an expert at HTML, but the first line seems wrong.

---

### Post by redmk2 on 2015-06-21
> **monkeybrain20122 said:**
> Hi, 

The setup of my server is like this

webroot is in /srv/www/webtest
output directory is /srv/www/webtest/outputs

The permissions are 
```
drwxr-x--- 3 monkeybrain www-data  webtest

drwxrwx--- 2 monkeybrain www-data  outputs

```
I run a script in apache to create a graph in the outputs folder /src/www/webtest/output

Its permissions are 
```

-rw-r--r-- 1 www-data www-data  graph.png
```

Now I am trying to retrieve the graph and show it on the browser. I test with a html script call testupload.html in the webtest directory 
testupload.html

```
<!DOCTYPE html>
<html>
    <head>
    <title>test upload path</title>
    </head>

    <body>
        <h1>
             graph
            <p><img src="outputs/graph.png"/></p>
        </h1>

    </body>
</html>





```

I call testupload.html from the browser but it always shows a brolken icon instead of the graph. It is a permission issue because if I change the owner of the graph to myself then it shows.

I want to be able to run the test script, for it to produce a graph in /srv/www/webtest/outputs and show it on the browser. What should I do? Thanks.

I think you are too restrictive with your permissions.  I don't see why you have set the permissions to 770 on the _outputs_ folder.  With my setup I have a _images_ **folder** at ./<virtual_host/images/ with the permissions of 775.  This seems to allow files that have 664 permissions and are world read only.  This setup works great.  The user or group doesn't matter as long as the file is available to be read by www-data.

I also have something like this as the code for a png file to be displayed```
<img src="./images/IMG_001.png"/>
```
The leading dot (.) makes the path relative.  The dot (.) represents the webroot so the path is: webroot/images/IMG_01.png.  I would add a leading dot (.) to the path in your web page.

When you see the broken icon you can right click on it and it should give you options to see exactly what is going on. What happens if you try and "view image"?  What are the properties of the image?

---

### Post by monkeybrain20122 on 2015-06-21
Hi, prepending the path with a dot doesn't help. Right click show image and it says "image contains errors and cannot be displayed"

It is strange. I created an output folder called outputs1 one level above webtest (where the script generates the graph lives) and replaced the upload path with 
"../outputs1/graph.png" then it works.

The permissions of the files and the folders are the same.
This works with path "../outputs1/graph.png"
```
drwxrwx--- 2 monkeybrain www-data  outputs1 (/srv/www/outputs1)
-rw-r--r-- 1 www-data www-data  graph.png
```

This doesn't work with "outputs/graph.png", "/outputs/graph.png" or "./outputs/graph.png"
```
drwxrwx--- 2 monkeybrain www-data  outputs (/srv/www/webtest/outputs) 
-rw-r--r-- 1 www-data www-data 4679 Jun 20 23:07 graph.png


```


  > I don't see why you have set the permissions to 770 on the _outputs_ folder.  With my setup I have a _images_ **folder**  at ./<virtual_host/images/ with the permissions of 775.  This seems  to allow files that have 664 permissions and are world read only.  This  setup works great.  The user or group doesn't matter as long as the file  is available to be read by www-data.

Since the output folder belongs to group www-data with permission rwx there is no need for the world to read the folder.

---

### Post by Lars Noodén on 2015-06-21
> **monkeybrain20122 said:**
> Hi, prepending the path with a dot doesn't help. Right click show image and it says "image contains errors and cannot be displayed"

What does the web server's error log say at that time?

---

### Post by monkeybrain20122 on 2015-06-21
I figured it out!

I am using RApache to run R with Apache. [http://rapache.net/manual.html](http://rapache.net/manual.html) The script that produced the graph is written in a mixed codes of html and R and handled via the R package brew. To this end I edited the Apache's config so that files inside the webtest folder are interpreted as brew scripts and passed through brew. Now the png file is not a brew script hence the error. I tested by commenting out the brew block in apache's config, restarted apache and reran the upload test (with path "outputs/graph.png" without dot or /) and it worked. 

So the output folder has to be placed outside the directory where the brew scripts reside.

There should be some errors from R but I don't see them. Apache's error log is not very illuminating. It is just full of entries like
```
127.0.0.1 - - [21/Jun/2015:06:36:12 -0400] "GET /webtest/outputs/graph.png HTTP/1.1" 200 5120 "http://webtest.com/testupload.html" "Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/43.0.2357.81 Safari/537.36 OPR/30.0.1835.59"
```

---

### Post by TheFu on 2015-06-21
Permissions and location of testupload.html?

BTW, it is important from a security perspective to have any user uploads go to a different domain to avoid malformed uploads being used to attack people.  I don't know how the big players deal with uploads, but I assume they run each through a conversion tool to strip out any bogus code embedded in the file type uploaded too - images get "converted" - videos get transcoded - all to protect us from nefarious uploads.

---

### Post by monkeybrain20122 on 2015-06-21
> **TheFu said:**
> Permissions and location of testupload.html?

```
-rw-rw-r-- 1 monkeybrain www-data  testupload.html

```

It is inside webtest folder with permission

```
drwxr-x--- 2 monkeybrain www-data webtest
```


> 
BTW, it is important from a security perspective to have any user uploads go to a different domain to avoid malformed uploads being used to attack people.  I don't know how the big players deal with uploads, but I assume they run each through a conversion tool to strip out any bogus code embedded in the file type uploaded too - images get "converted" - videos get transcoded - all to protect us from nefarious uploads.

I don't quite understand this. Can you give an example set up?

---

### Post by TheFu on 2015-06-21
> **monkeybrain20122 said:**
> 

I don't quite understand this. Can you give an example set up?

twitter.com
twittpic.com

Pretty much EVERY site that allows upload from end users does this. It is part of the HTTPS security model and why just using a subdomain is NOT sufficient to avoid the attack vector.  OWASP likely has a fuller explanation.

As we get older, we condense knowledge. I've done that do know to always have a different domain for uploads than viewing and I don't remember all the reasons why. Sorry.

[https://serverfault.com/questions/91394/why-when-to-have-a-separate-media-server-for-images-mp3s-flvs-etc](https://serverfault.com/questions/91394/why-when-to-have-a-separate-media-server-for-images-mp3s-flvs-etc) has lijnks to explanations for the security aspects.  Forget the "optimization" things until you need it.

---

### Post by monkeybrain20122 on 2015-06-21
> **TheFu said:**
> twitter.com
twittpic.com

Pretty much EVERY site that allows upload from end users does this. It is part of the HTTPS security model and why just using a subdomain is NOT sufficient to avoid the attack vector.  OWASP likely has a fuller explanation.

As we get older, we condense knowledge. I've done that do know to always have a different domain for uploads than viewing and I don't remember all the reasons why. Sorry.

I don't allow upload by end users, the uploads are just outputs from my scripts. The end users submit requests to run scripts through forms.

---

### Post by TheFu on 2015-06-21
> **monkeybrain20122 said:**
> I don't allow upload by end users, the uploads are just outputs from my scripts. The end users submit requests to run scripts through forms.

That will be fine under the same domain then. The "upload" name threw me off. sorry.

---

