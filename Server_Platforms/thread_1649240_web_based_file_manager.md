---
title: "web based file manager"
date: 2010-12-19
forum: Server Platforms
---

### Post by boondocks on 2010-12-19
We have over 600 documents, mostly PDFs.
These documents were available internally.
But now we want to make them accessible via the web for about 8 people.
With user id, password protection and the appropriate security ... of course.
So users can create folders, upload and download files.
Can you recommend a web based file manager system that can be installed on a Ubuntu server?
Something that is has been around for a while, reliable, mature and can be used by non-technical people.

---

### Post by brettg on 2010-12-20
Assuming you just want read only access then all you need is Apache with directory listing enabled and user auth using a simple  .htaccess file.

---

### Post by boondocks on 2010-12-20
> **brettg said:**
> Assuming you just want read only access then all you need is Apache with directory listing enabled and user auth using a simple  .htaccess file.

Yes, we can do that with Apache.
But the users should be able to upload files too.
And create folders.

---

### Post by HermanAB on 2010-12-20
Howdy,

There are quite a few of these WebDAV things.  KnowledgeTree is probably the best of the lot while MS Sharepoint is one of the worst.  

You can get a pre-installed virtual machine here:
[http://bitnami.org/stack/knowledgetree](http://bitnami.org/stack/knowledgetree)

---

### Post by SeijiSensei on 2010-12-20
Just use [mod_dav](http://httpd.apache.org/docs/2.2/mod/mod_dav.html) to create a WebDAV share in Apache.  You can enforce authentication with Apache's usual basic authentication procedures.

---

### Post by R.Bucky on 2010-12-20
This script works well [http://www.osfilemanager.com/]("http://www.osfilemanager.com/")

---

### Post by Vegan on 2010-12-20
It would be 100x safer to write a form in PHP to authenticate users credentials.

Then when authenticated, the listing of files can be presented easily.

This type of setup is standard fare for PHP.

---

### Post by arrrghhh on 2010-12-20
ajaXplorer is a pretty good one as well...

---

