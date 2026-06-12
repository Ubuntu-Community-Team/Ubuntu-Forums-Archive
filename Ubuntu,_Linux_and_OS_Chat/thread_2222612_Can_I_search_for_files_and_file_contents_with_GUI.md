---
title: "Can I search for files and file contents with GUI"
date: 2014-05-07
forum: Ubuntu, Linux and OS Chat
---

### Post by Shota_Akhalaia on 2014-05-07
Hi I have question Can I search text contents in files with ubuntu file manager
e.g. ms windows can search within files contents, I can find some word in office files, can I do something like that in ubuntu?
thnx and sorry for my English

---

### Post by TheFu on 2014-05-07
**recoll** - the most amazing search engine.

---

### Post by LastDino on 2014-05-07
> **TheFu said:**
> **recoll** - the most amazing search engine.

I'll further that question, is it possible to search in files other than office documents, lets say ''.sh''?

---

### Post by TheFu on 2014-05-07
recoll if a GUI is required. It has very powerful indexing and near-instance search results. Think of this locate for file contents. Of course, the index can get large.

If you want quick searches without an index ... er ... can't really help, but **find** and **locate** are the CLI tools for all that assuming you can put together a 1-liner with egrep/grep/whatever search you like.  There must be 1B examples of find + grep on the internet. Checkout command-line-fu.

---

### Post by LastDino on 2014-05-07
> **TheFu said:**
> recoll if a GUI is required. It has very powerful indexing and near-instance search results. Think of this locate for file contents. Of course, the index can get large.

If you want quick searches without an index ... er ... can't really help, but **find** and **locate** are the CLI tools for all that assuming you can put together a 1-liner with egrep/grep/whatever search you like.  There must be 1B examples of find + grep on the internet. Checkout command-line-fu.

Oh, nice suggestion & share, thanks!

---

### Post by ibjsb4 on 2014-05-07
> **TheFu said:**
> recoll if a GUI is required. It has very powerful indexing and near-instance search results. Think of this locate for file contents. Of course, the index can get large.

If you want quick searches without an index ... er ... can't really help, but **find** and **locate** are the CLI tools for all that assuming you can put together a 1-liner with egrep/grep/whatever search you like.  There must be 1B examples of find + grep on the internet. Checkout command-line-fu.

Been on the lookout for an apt like this and its QT.

Nice :) Thanks

---

### Post by buzzingrobot on 2014-05-07
To efficiently search the contents of files, rather than just file names, the contents  must be previously indexed.  Recoll is that kind of tool. It needs to make an initial index, and then the user needs to set up some kind of periodic index updating procedure.

To adjust the appearance of a QT-based app like Recoll in Ubuntu, install and use qt4-config. Try different settings and restart Recoll to see if you like how things look. I'm OK with the GTK+ setting.

---

### Post by saye-187 on 2014-05-07
i think you can do this you can do evrythings whit ubuntu thats the dark side

---

### Post by Shota_Akhalaia on 2014-05-08
Thank you all for replying ;)
I installed recoll and it's very good tool, also I try tracker indexing with desktop search application, but is there some way to integrate those search tools in nautilus file manager

---

### Post by ssam on 2014-05-08
I think the new GNOME Documents does content search.

---

