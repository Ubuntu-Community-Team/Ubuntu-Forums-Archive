---
title: "Ubuntu One API move/rename problem"
date: 2011-12-28
forum: Ubuntu One (CLOSED)
---

### Post by Gelembjuk on 2011-12-28
Hello,

I tried to post this question on [http://askubuntu.com](http://askubuntu.com), but noone responds.

I wanted to use Ubuntu One API to move files from one folder to another. I used method from there [https://one.ubuntu.com/developer/files/store_files/cloud/](https://one.ubuntu.com/developer/files/store_files/cloud/)

PUT /api/file_storage/v1/~/path/to/volume/path/to/node 
{"node_path": new path} 

When i execute this API call it returns "success" response. HTTP code is 200 and response body is full Node Representation. But it is not not new node. old node is returned and file is not moved. it stays in old place.

What can be wrong there?

---

