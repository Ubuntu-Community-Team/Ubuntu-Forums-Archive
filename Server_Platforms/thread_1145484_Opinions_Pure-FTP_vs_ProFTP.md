---
title: "Opinions: Pure-FTP vs ProFTP"
date: 2009-05-01
forum: Server Platforms
---

### Post by Dy1anW on 2009-05-01
I was wondering which is better, as they both seem pretty much the same to me.  Which do you use and why?

I'm on Pure-FTP for the simple reason that it was the first how-to I found that involved database authentication, but trying to get TLS/SSL has been a no-go so far; but that's something I want.  I've had friends testing my Pure-FTP server (uploading/downloading) and they mentioned that it's quite fast.  Would it be worthwhile to switch over to Pro?

---

### Post by HermanAB on 2009-05-01
Howdy,

As FTP servers go, it is all the same difference...

If you want real security, then you should use SSH Server, not FTP.

---

### Post by SciFi-Bob on 2009-05-07
I have tried both of them, but I doubt the differences I have experienced would mean anything to you, except maybe the documentation issue.

Both packages has a fairly good documentation an there are some good howto's out there. It may be because I settled on proftpd, that I found more docs on that package, so I won't say that there isn't any decent documentation on pure-ftp also.

If you think performance, then you are off track, because most ftp servers configured correctly will perform equally good. Most of them (hopefully) uses the ftp protocol as it should be used, and then there is really nothing to optimize, except maybe the connection stage, which really has nothing to do with performance. 

And, as HermanAB mentioned, if you really want security, use SSH. On a small file now and then, you won't notice the difference, but if you're serving big files like multimedia and such, then SSH may not be the solution for you.

Anyway, if you want a ftp server, then in my experience, it boils down to two things: 

1. Functionality (Pick the software that fits your needs)
2. Documentation (You need some docs you can understand)

---

### Post by mojorising on 2009-05-07
It's true, most FTP servers are basically the same. 

Have you considered vsftp ([http://vsftpd.beasts.org/)?](http://vsftpd.beasts.org/)?) I've used it in the past and found it to be quite good. I used it as an SFTP server with jailed home directories for more security. 

Other more secure options are using scp and rsync over ssh, which may work for you depending on what you plan to do with this server. 


Mike

---

