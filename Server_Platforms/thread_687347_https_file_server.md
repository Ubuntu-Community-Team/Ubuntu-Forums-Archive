---
title: "https file server"
date: 2008-02-04
forum: Server Platforms
---

### Post by Tribus on 2008-02-04
I am looking for a file server, preferably over https, but can not find a suitable solution.
It need so support multiple users with different access.
Any ideas would be appreciated.
thanks in advance

---

### Post by Dr Small on 2008-02-04
I setup XAMPP and ProFTPd and it works for all my needs as a fileserver :)

---

### Post by Tribus on 2008-02-04
> **Dr Small said:**
> I setup XAMPP and ProFTPd and it works for all my needs as a fileserver :)

I have considered  that, but you need a client for ftp/ftps/sftp and the whole point of a file server over https is to avoid the need of a client. 
thanks anyway!

---

### Post by flashm on 2008-02-04
Why not try apache? That's what the rest of the world seems to use!

---

### Post by linuxtechie on 2008-02-04
how about python based? Works out of box if python is implemented as following:

Search for SimpleHTTPServer, even python's document is easy and can be done with in 2 minutes :popcorn:

---

### Post by Tribus on 2008-02-04
Apache is great but I need the possibility to upload files.

---

### Post by cdenley on 2008-02-04
You can upload files with apache. You can create a really simple php script, or if you need a progress bar, I recommend uber uploader.

---

### Post by Tribus on 2008-02-05
I will try it out! 
thanks allot everyone :)

---

