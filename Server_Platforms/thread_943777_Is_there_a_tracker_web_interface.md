---
title: "Is there a tracker web interface?"
date: 2008-10-10
forum: Server Platforms
---

### Post by marcosdsanchez on 2008-10-10
Hey all, I want to use tracker as an indexing engine in a server.
I want to know if there's any web interface for that as I need people to connect to that server to find results.

I'm currently using swish-e which has a web interface written in perl.

Any advise?

Cheers,

Marcos

---

### Post by tarvtarv on 2008-10-14
[SIZE="4"][/SIZE]Hi Marcos I did a quick search for Swish on the forums and read your post I just installed SWISH and was wondering; 
How to get it up and running/? I want to crawl and index the web based on a topical filter Can you run me through the setup for swish PLease?

---

### Post by marcosdsanchez on 2008-10-14
Hey tarvtarv,

Installation of swish-e is easy on Ubuntu.
Just do 

```
sudo apt-get install swish-e
```

Then, you have to create a configuration file for example: 

```
   # Index this directory an any subdirectories
   IndexDir /home/marcos/workspace/distros
   IndexFile /home/marcos/workspace/indexador/application/data/index/index.swish-e 
   IndexOnly .pdf .doc .xls .html .htm 
   FileFilter .pdf 	   /usr/bin/pdftotext  "'%p' -" 
   IndexContents TXT .pdf 
   FileFilter .doc /usr/bin/catdoc "-s8859-1 -d8859-1 '%p'"
   IndexContents TXT .doc
   FileFilterMatch .xls /usr/bin/xlhtml "'%p'"
   IndexContents HTML .html .xls 
```

This configuration file will index xls, html, pdf, htm and doc files in /home/marcos/workspace/distros (and subdirectories) and will create index files in /home/marcos/workspace/indexador/application/data/index/index.swish-e

(note that you'll also need catdoc, xlhtml and pdftotext installed to work properly)

If you want to create an index you have to do: 
```
swish-e -c [PATH-TO-YOUR-CONFIG-FILE]
```
If you want to search 
```
swish-e -f [PATH-TO-YOUR-INDEXES-FILE] -w SEARCHWORD
```

The [swish-e page]("http://swish-e.org") is well documented. Please go there for further information.
You might need [the Spider part]("http://swish-e.org/docs/swish-config.html#directives_for_the_http_access_method_only")

Cheers, 

Marcos

---

### Post by worjak on 2008-11-23
I'm looking for a solution like that too. Will also try out Swish-e. Does any one know of other alternatives ie. indexing and searching files with web interface.

Cheers Jakob

---

