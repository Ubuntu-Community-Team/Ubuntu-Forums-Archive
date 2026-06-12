---
title: "accessing a web directory to see the content"
date: 2007-04-14
forum: Server Platforms
---

### Post by reality_hunter on 2007-04-14
Hi all, I do not know too much about Apache and all so please be brief when explaining, 

Goal:  to view content of a directory on the website
Problem: 403 Forbidden message

There is a website with URL something like for example 
"www.ee.utoronto.ca/~chimpi/CP.HTM" 
this site has 10-15 documents listed on the actual page and each one of them is loaded from the directory
"www.ee.utoronto.ca/~chimpi/cp/...."
so for example a pdf called 'test.pdf' is loaded like:
"www.ee.utoronto.ca/~chimpi/cp/test.pdf"

Of all the documents on the actual page it loads from the same "/cp/" directory.
there are lots of other documents in that directory as well that are NOT listed on the website, but can be fetched through the document name exactly. For example there is file call 'test1999.zip' in that directory.  The website has no reference pointing to that file.  However, that document can be accessed by typing the URL
"www.ee.utoronto.ca/~chimpi/cp/test1999.zip" 
so basically you just have to know the filename. The thing is that when try to access "www.ee.utoronto.ca/~chimpi/cp/" to see what other stuff is there  the 403 forbidden no permission error comes up, which sucks.

My question is that how do I view the filenames from that directory??? since all of the stuff has read permission, I am pretty sure I can get the stuff, BUT what if I dont know the file name....can I find out??

I am really lost with this one, any help with this is appreciated~!



to the admins, if this is the wrong forum to post please discard this and delete it....but do point me where to post such topic, thanks

---

### Post by NPALeech on 2007-04-14
Sounds, to me, like the server is setup to prevent exactly what you're trying to do. Just because there are more files in a directory doesn't mean that the owner of those files wants everyone to have access. So, in short, you can't get a listing.

---

### Post by scxtt on 2007-04-14
it's not the files that need read permission for you to get a listing, it's the directory that needs it ... so if the "cp" directory isn't "readable by other", you can't get a listing ...

---

### Post by reality_hunter on 2007-04-14
> **scxtt said:**
> it's not the files that need read permission for you to get a listing, it's the directory that needs it ... so if the "cp" directory isn't "readable by other", you can't get a listing ...

bum](*,) 
all I want to do is run a command like 'dir' like windows or 'ls' to get the file names

lol
anyways, thanks for replying

---

### Post by az on 2007-04-14
In your apache configuration for that site, I beleive that you need to add Indexes to the Options.

---

### Post by reality_hunter on 2007-04-15
> **az said:**
> In your apache configuration for that site, I beleive that you need to add Indexes to the Options.

I am not the one running the server.  Its someone else!

---

