---
title: "Strange apache default setting"
date: 2009-06-26
forum: Server Platforms
---

### Post by acroporas on 2009-06-26
I am running Ubuntu Desktop 9.04 amd64 with apache2, php, and mysql installed.

I have come across some strange behaviour with the default apache settings.  Can someone tell me what setting is causing this and how to turn it off.  I'm sure it is really simple but I have been searching the net for hours and not found a reference to this behaviour.

The following files exist in the www folder.

testfolder                 (a folder)
testfolder/file1.html      (a file in the testfolder)
testfolder.html            (a file)

folderdoesnotexisit.html   (a file)
testfile.html              (a file)

Now I go to the web browser and type the following addresses which do exactly as I would expect:

These load the directory by the same name:

[http://localhost/testfolder](http://localhost/testfolder)
[http://localhost/testfolder/](http://localhost/testfolder/)

These open the file by the same name:

[http://localhost/testfolder.html](http://localhost/testfolder.html)
[http://localhost/testfolder/file1.html](http://localhost/testfolder/file1.html)
[http://localhost/folderdoesnotexisit.html](http://localhost/folderdoesnotexisit.html)

But the following addresses do weird things.

[http://localhost/folderdoesnotexist](http://localhost/folderdoesnotexist)  (loads folderdoesnotexist.html when it should say not found)
[http://localhost/folderdoesnotexist/](http://localhost/folderdoesnotexist/) ( gives error page with odd warning "The requested URL /folderdoesnotexist.html/")

[http://localhost/folderdoesnotexist/filethatdoesnoteixt.html](http://localhost/folderdoesnotexist/filethatdoesnoteixt.html) ( gives error page with odd warning "The requested URL /folderdoesnotexist**.html**/filethatdoesnotexist.html")

So weird error messages and addresses that should error but don't does not sound like that big of a problem, which is probably why this is the default behaviour.  But it is causing me problems with mod-rewrite so I need to turn this behaviour off.

---

