---
title: "Apache Form variables"
date: 2016-05-24
forum: Server Platforms
---

### Post by Jake_Simmons on 2016-05-24
Hi, all! 
I wasn't entirely sure where to put this question, so excuse me if it is in the wrong place!

I am having a bit of fun with apache, and was experimenting with some PHP, and was unsure how to parse a variable into a command... here is the code, that (hopefully) makes more sense:

[HTML]<html><title>Submission</title><body bgcolor="blue"><h1 align="center">Submission Received</h1>Thank You, <?php echo $_GET["name"]; ?><br><?php$Name=$_GET["name"];shell_exec('echo $Name >> /WWW-DATA/COCINFO/Names');?></body></html>[/HTML]


If anyone knows how I can get the Name variable into the shell_exec command, so I can echo it, it would be much appreciated. I am not **too ** concerned about security, as this is not an important server, or frequently visited, and any way to do this would be great!

---

### Post by SeijiSensei on 2016-05-24
Change the single quotes in 'echo $Name'  to double quotes.  Strings in single quotes are interpreted literally; strings in double quotes will be interpreted after substituting for variables.  This is the same as Unix/Linux.

---

### Post by Jake_Simmons on 2016-05-25
Thank you so much, this is awesome, and works perfectly!

---

