---
title: "How to create a new file with content using Ubuntu One API and PHP"
date: 2011-07-29
forum: Ubuntu One (CLOSED)
---

### Post by paglia96 on 2011-07-29
I'm having some problems when i try to create a new file with some content (or overwrite the content of an existing one) using [Ubuntu One API]("https://one.ubuntu.com/developer/files/store_files/cloud/") and PHP.

I can easily create and empty file or folder using:

[B]PUT /api/file_storage/v1/~/path/to/volume/path/to/node
[/B]
but i don't understand ho to use this specification:

> PUT /api/file_storage/v1/ + <directory.content_path> + '/' + filename.ext, or /api/file_storage/v1/ + <file.content_path>

PUT a new file, with content, in one action, or overwrite content of an existing file.
The body of the PUT request is the content of the file.
Note that you cannot PUT a new file with content and alter its attributes at the same time.
Note also that content_paths may not be rooted under the API root, and may change without warning, so they must be read from the API and not hardcoded.
(Note caveat above about CONTENT_ROOT being temporarily different.)
I don't post the whole code but only the line which doesn't work:

[PHP]$api_url = 'https://one.ubuntu.com/api/file_storage/v1/';
$filecontentent = "content of the txt file";

$oauth->fetch($api_url.'~/UbuntuOne.'.$filecontentent.'/try.txt', OAUTH_HTTP_METHOD_PUT);[/PHP]
I don't understand how to structure the syntax. Can you help me?

---

### Post by duanedesign on 2011-08-04
Did you get an answer on this? I believe you posted on askubuntu.com?

thank you,
duanedesign

---

### Post by paglia96 on 2011-08-16
Thanks, yes i've asked it on askubuntu and i've solved

---

