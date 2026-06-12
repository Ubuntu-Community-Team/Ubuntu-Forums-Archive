---
title: "Sorting books"
date: 2015-07-25
forum: The Cafe
---

### Post by smelheim85 on 2015-07-25
Hello World,

I am trying to find an easy way to sort through a database of books that my LoCo has collected over the years.  I have been able to sort them out and put them into several folders based on their subject topic.  I am trying to find another way then drag and drop.  I have looked at Calibre and it helps to find information about the book like title, publication year, author.  But what I am trying to do is separate books based on subject matter so then anyone that is looking for a book can easily go to that folder and find multiple books on the same subject.

Any ideas or thoughts?

---

### Post by TheFu on 2015-07-25
This is hard unless the filenames contain the tagging for subject that you can key from. Does it?
For example, if the filename has "perl" in it, you could move it to the "Perl" directory using a **find -exec**.  Besides that, I don't know.

That will not help inside Calibre.

---

### Post by Bucky Ball on 2015-07-25
*Thread moved to **The Cafe**.*

One word: [Zotero]("https://www.zotero.org/").

The standalone version would probably suit what you are doing. Create book entries and link the book files. You could then sync Zotero so the database was available on any machine. :)

Have a look, might work for you.

PS: If the book file is a PDF, you can right click the linked PDF in Zotero and get the metadata if it is available. This will fill out the complete reference correctly: publisher, date, author, title, etc. Have a fiddle around and see what you can come up with.

* Just had a look. In Zotero, click 'New Item' in the toolbar> 'Link to file' from the drop-down list> choose your PDF> right click the PDF entry in Zotero> Retrieve metadata for PDF. If it finds the metadata that will correctly complete the reference for you. That way you can print bibliographies of your Zotero library and you don't need to sit for hours filling out book details to do it. :)

PPS: Zotero also has a version that runs inside Firefox and both versions have a plug-in for Libreoffice and Word that lets you plop citations and bibliographies into documents easily.

---

### Post by TheFu on 2015-07-25
Bucky's idea got me thinking ... if the "books" are in a known format, **recoll** can index almost anything so full text search can be used.  I used to work in document management and found that most metadata is crap - not to be trusted.  Full text search is really the only solution - unless the metadata CAN be trusted.

**recoll** is amazing - think "*google for your desktop*", but the indexes do take up storage and it really isn't designed for server use.  For that, something like htdig or e-swish are the old-school tools.

If you clarify the "database of books" ... more solutions might come up. Are these PDF, scans, epub, modi, something else? Do they have DRM or not? and what is the "database" - a text file, mysql DB, Dbase3, paradox? dbm, gdm?

---

### Post by Bucky Ball on 2015-07-25
Right, a database. My mistake. Zotero can also import a heap of different types of databases if you go that way. As TheFu mentions, a lot depends on what kind of database it is. :)

---

