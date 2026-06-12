---
title: "Putting a file into a web site."
date: 2010-01-26
forum: Server Platforms
---

### Post by Hopalong on 2010-01-26
I am trying to put files on my website for others to download, but there is evidently something I have missed. The plot so far is as follows:
	Website up and running: Filezilla (3.2.7.2) installed to upload files: obtained from the repositories. (It says there is a later version, 3.3.1, but it isn't there.) File transferred in Filezilla, appears in site directory, as a PDF document, in root directory "public_html". 
	In the "index.html" for the site itself I have put an "<A HREF = "public_html/PCandEX.pdf">, that being the file name, uploaded this to the directory in  the site.
  But reference to this on the site gives a very elderly file that I put there a long time ago. I thought I had deleted this in Filezilla, but apparently not.
  What have I not done??

---

### Post by diesch on 2010-01-27
Most likely you have to use just
```
 <a href="PCandEX.pdf">
```
without the "public_html" in your *index.html*

I guess you have an old *public_html* folder inside your *public_html* folder and the old .pdf is inside this second *public_html* folder.

---

### Post by volkswagner on 2010-01-27
Perhaps it could be a browser cache issue from you previous visit.  Try clearing the cache.

---

### Post by Hopalong on 2010-01-27
Better insight! The problem is not with the index.html content but with the file itself. The site is not using the new one! Using Filezilla, where exactly on the site is the old index.html to be replaced by the new one?

---

