---
title: "anyone good with web hosting?"
date: 2009-03-26
forum: The Cafe
---

### Post by SonnHalter on 2009-03-26
okay. I designed my website. all code is done. but.... when i'm uploading this file to my host my media (flash and images) won't show up because it located on my computer. 

does anyone know how to transfer these files online so they will show up online?

---

### Post by beercz on 2009-03-26
> **SonnHalter said:**
> okay. I designed my website. all code is done. but.... when i'm uploading this file to my host my media (flash and images) won't show up because it located on my computer. 

does anyone know how to transfer these files online so they will show up online?
In your code, what is the path to the images and flash movies?

---

### Post by sydbat on 2009-03-26
> **SonnHalter said:**
> okay. I designed my website. all code is done. but.... when i'm uploading this file to my host my media (flash and images) won't show up because it located on my computer. 

does anyone know how to transfer these files online so they will show up online?Filezilla. In the repos.

And, as beercz mentions, make sure the file associations are correct when everything is uploaded.

---

### Post by SonnHalter on 2009-03-26
i design on windows.

the files exampled are like c:user/documents/pictures/header.jpg

things liek that. 
i need them online

i'm trying to use filezilla but its not going so good.

---

### Post by ubersolid on 2009-03-26
Your path is ```
<img src="c:user/documents/pictures/header.jpg"
```
That will not work as you have noticed, you are referring to folder that is on your computer, but your code is pointing to that path on the server where you are hosting your page, and that folder does not exist there.
You need to make a folder, say "pictures" on the server, put your "header.jpg" inside that folder and fix your code to say ```
<img src="pictures/header.jpg">
```

That should work.

---

### Post by beercz on 2009-03-26
I don't think this is the right thread for this put here goes ...

In your code where does the <img src .... /> tag point to?

It should be something like <img src="picture1.jpg" .... /> and not <img src="C:\Documents and Settings ...... \picture1.jpg" ... />

I think you may need to learn about relative and absolute paths.

Mods, perhaps this thread should be moved to a more appropriate forum where the OP can get more help.

---

### Post by Coreigh on 2009-03-26
To clarify: in your webpage code do your links look like this:
> file:///this folder/thatfolder/myflashfile.swf
or this:
> C:\this folder\thatfolder\myflashfile.swf

if the DO then you need to learn about relative links.
see this:
[http://www.extropia.com/tutorials/web_design/relative_absolute_links.html](http://www.extropia.com/tutorials/web_design/relative_absolute_links.html)


The other poster is asking if you are having trouble uploading the files and suggesting to use an FTP program, which is a good idea if your host offer FTP access. Other wise just use the upload tool they offer.

EDIT: I see that many people caught this idea before I was able to post.

---

### Post by SonnHalter on 2009-03-26
thx for the path. I already know about paths. I just didn't know where to put the files.

---

### Post by mrsteveman1 on 2009-03-26
What exactly is the problem? You can't get the files to upload to a webserver? Or you don't know how to configure the server to serve the pages?

---

### Post by SonnHalter on 2009-03-26
...its solved now.

---

