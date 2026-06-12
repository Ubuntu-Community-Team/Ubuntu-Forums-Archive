---
title: "linking directory listing from index file"
date: 2007-06-02
forum: Server Platforms
---

### Post by djtecha on 2007-06-02
So I have a webserver up and running, but I would like to have an opening page simply explaing the rules and what-not, but I can't figure out how to make a link in the index file to go to the directoy listing. so it shows up as a bunch of files.

---

### Post by MJN on 2007-06-04
I'm not sure if there is a way to force an auto-index in the presence of a valid index file.
 
Unless I have misunderstood, how about just moving your files to another (sub)directory and having no index file in it? Hence you'd just need to link to that directory/ and you'd get the list of files.
 
Altenative options might be to use the HeaderName directive ([http://httpd.apache.org/docs/2.0/mod/mod_autoindex.html#headername](http://httpd.apache.org/docs/2.0/mod/mod_autoindex.html#headername)) to insert text at the beginning of an autoindex, or perhaps to use server-side includes to show a directory listing (ls output suitably parsed and hyperlinked) within another page?
 
Mathew

---

