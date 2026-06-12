---
title: "Preventing garbled text when downloading gzipped files"
date: 2012-08-07
forum: Server Platforms
---

### Post by aqnato on 2012-08-07
Our website has text files that are compressed in either the zipped (*.zip) or gzipped (*.gz) format. For a long time, there had been no problems downloading these compressed text files and are ok once uncompressed. Recently, however, the gzipped files become garbled (showing ASCII characters instead of text so it may have been downloaded as binary) instead of plain text. I have checked the apache2.conf file and "DefaultType text/plain" has already been placed instead of application/octet-stream (see below). I don't want to touch .htaccess yet. Any suggestions?

 #
  # DefaultType is the default MIME type the server will use for a document
  # if it cannot otherwise determine one, such as from filename extensions.
  # If your server contains mostly text or HTML documents, "text/plain" is
  # a good value.  If most of your content is binary, such as applications
  # or images, you may want to use "application/octet-stream" instead to
  # keep browsers from trying to display binary files as though they are
  # text.
  #
  DefaultType text/plain

---

