---
title: "webDAV:  Unable to PUT content"
date: 2009-07-30
forum: Server Platforms
---

### Post by Summitt Dweller on 2009-07-30
I've configured webDAV on a Ubuntu 9.04 server running Apache2.  Created a /source alias for my document root and set FileType to plain/text so that from this alias DAV gives me source code, not rendered content.  I have no Limit directives at all.  Works great...with one exception.  I can upload and download _existing _files just fine but when I try to upload a completely new file or directory it fails and my Apache logs show "Unable to PUT content... [403, #0].  

I thought the problem was with an errant .htaccess file (leftover from shared hosting) but I removed that and still can't upload.  All the target directories are owned by www-data:www-data and the directory permissions are wide open.  

Any idea what might be keeping me from uploading?  :confused:

---

### Post by Summitt Dweller on 2009-08-02
Found the answer here [http://www.favias.org/post/webdav-meet-drupal](http://www.favias.org/post/webdav-meet-drupal).  Big thanks to Michael for posting his solution (and to Google for finding it).

---

