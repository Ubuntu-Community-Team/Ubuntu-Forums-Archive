---
title: "Hide files with vsftpd"
date: 2010-11-09
forum: Server Platforms
---

### Post by durians on 2010-11-09
I have a server with Ubuntu 10.04 LTS as OS and I'm trying to set up an FTP-server on it. The base install was pretty simple, but I have a small annoyance. I have 2 sub-directories /pub/Downloads and /pub/Uploads and I want users to see all files in Downloads, but only be able to see the files in Uploads that they know the name of.
According to the manual I should be able to use 'hide_file', but it seems like I'm missing something or maybe I need to rebuild it? I've tried:

hide_file={/pub/Uploads/*} 

but it still shows the files. However, if I do:

hide_file={/pub/Uploads/*, .*}

it will hides files that start with a '.'. Or if I do:

hide_file={/pub/Uploads/*, *.zip}

it will hide ZIP-files. But it seems to be impossible to hide all files in a directory.

---

