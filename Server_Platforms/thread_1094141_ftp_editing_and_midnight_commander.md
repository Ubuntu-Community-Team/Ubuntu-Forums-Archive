---
title: "ftp editing and midnight commander"
date: 2009-03-12
forum: Server Platforms
---

### Post by maclenin on 2009-03-12
I am wondering if there is a way to edit remote files (via ftp) using midnight commander's text editor (e.g. nano)?

I tried to edit an html document - via ftp (using midnight commander and nano) - the changes seemed to take effect - as I made them - and I "saved" the file as I would after any nano edit session - however, when I tried to view the changes, both via the web and when inspecting the file after downloading it to a local machine, I noticed the changes had not been incorporated/saved....

Any thoughts?

How can I edit remote documents via ftp using midnight commander?

Thanks for any suggestions!

---

### Post by hyper_ch on 2009-03-12
if you have ssh access then you used use sshfs to mount the remote filesystem into your local one and then you can easily edit it with sykpe.

---

### Post by windependence on 2009-03-13
Are you remoting in from a PC or a Mac?

-Tim

---

### Post by maclenin on 2009-03-13
Thanks, folks. I am remoting from a PC....

---

