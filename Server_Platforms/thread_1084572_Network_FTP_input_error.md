---
title: "Network FTP input error"
date: 2009-03-02
forum: Server Platforms
---

### Post by any.linux12 on 2009-03-02
Hi!

Everytime I send something to my network FTP (NAS) it gives me an input error. It's not very critical because the files get copy but it's very boring to have errors and have to say SKIP or Skip all everytime. And it's also hard to explain to my boss why that error even if the copy works.

---

### Post by JeppeM on 2009-03-02
Hey,

We need some more information about this before we can figure out what happens. Could you please provide us with the following information:

What OS does the ftp server run (ubuntu server? 8.04/8.10 etc)?
What program are you using to server the ftp (proftp, vsftpd)?
What is the error you get in the client when you try to upload? - Just saying "input error" doesnt get us far :)
Does the logs on the server tell you anything? Try doing "tail -n 50 /var/log/messages" after you've gotten the error and post that...

---

### Post by any.linux12 on 2009-03-02
> **JeppeM said:**
> Hey,

We need some more information about this before we can figure out what happens. Could you please provide us with the following information:

What OS does the ftp server run (ubuntu server? 8.04/8.10 etc)?
What program are you using to server the ftp (proftp, vsftpd)?
What is the error you get in the client when you try to upload? - Just saying "input error" doesnt get us far :)
Does the logs on the server tell you anything? Try doing "tail -n 50 /var/log/messages" after you've gotten the error and post that...

It's not a ftp server is a NAS a Lacie-2big network with 1000GB in raid 1. And I'm not using any program it's just mounted with a script that I did with curlftpfs

And I was trying to send you some print screens but I can't lol I have to restore my Laptop, maybe that's the problem.

There is also another error. When I try to delete a tree it says operation not permitted and I have to delete all files inside the folder and just that I can delete the files.

So it's a input/output error during copy and a operation not permitted during deleting

Very bad. Thnks

---

