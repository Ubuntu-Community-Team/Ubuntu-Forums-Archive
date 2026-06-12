---
title: "Managing very large files uploads"
date: 2012-12-17
forum: Server Platforms
---

### Post by technimage on 2012-12-17
Hello everyone,

We are managing a college campus server which allows students to upload and download files. We called it a "ftp" but it only used (until now) the http protocol and was running on a computer running Windows. Students just access a website and the upload (along with the database filling) is easily done with php.
We have today purchased a new computer which will be able to hold much more data but which also uses Ubuntu. We want to switch to the ftp protocol because uploads always fail when the file is larger than 1.5GB and we believe this is because of the limitations of the http protocol. Is that correct?

If switching to ftp is a good solution, will using the "ftp library" of php be enough to handle the uploads and downloads? We fear that because we use php on the website, the different actions will go through apache, and thus will first use the http protocol (and the upload will fail as it did before).

If I'm not clear, please ask me for more information. Any help, remark or alternative solution will be highly appreciated ! Thanks a lot and have a great day ):P

---

### Post by coffeecat on 2012-12-17
*Thread moved to **Server Platforms**.*

@technimage, welcome to the forum. I've moved this from Programming Talk because the Server forum is probably a more appropriate place for you to get the help you need. Good luck.

---

### Post by technimage on 2012-12-18
Alright, that works for me, sorry about that! I'm pretty new to all this and I was a bit confused with the multiple categories.

---

### Post by Grenage on 2012-12-18
I'm not aware of any size limit when using HTTP, and imagine any such limit would be software-applied.

---

### Post by technimage on 2012-12-18
After looking this up, it indeed seems that the limitation is browser related and that most browsers should be able to upload 2GB files but none can go past the 4GB limitation. However, Google Chrome is supposed to handle files up to 4GB but it fails when trying to upload files >2GB. I have no idea why (no error, it will just ignore the upload).
I have of course removed any php related limitation...

I would really like to allow large uploads within the web browser without going through an external (probably Java *sigh*) application but it seems to me that if I want to upload files larger than 4GB, I will have no choice right?
Thanks a lot for your answer !

---

### Post by Grenage on 2012-12-18
Does it need to be web-based?  Is an FTP client impractical for your purposes?

---

### Post by technimage on 2012-12-18
I would very much like to avoid external applications yes but if I have no choice, I guess using an applet built in the browser would be a second-best option. 

I'm thinking either Java, Silverlight or Flash based. Even though I dislike most of these, I'm thinking flash would be the best for "standard" users because they usually have Flash always enabled and won't be bothered with "You need to install X to use Y" or "Will you allow X to use Y" messages.
My main imperative is to make the process as easy and straightforward as possible for the users...

---

### Post by Lars Noodén on 2012-12-18
Flash in general is going away and for right now it locks out your iThing users.  Silverlight is already dead and would lock out your Linux users, probably Mac users would also be affected.  That leaves Java.

What about SFTP?  There are clients built into the various Linux file managers like Nautilus and Thunar.  Packages like WinSCP are available for legacy systems.  The advantage with SFTP is that its widely supported, has no size limits and, unlike FTP, is secure.

---

### Post by slickymaster on 2012-12-18
HTTP protocol has no limitations, but most HTTP servers have default upload limits out-of-the-box:

**IIS6** uses *MaxRequestEntityAllowed* (default is 4GB) and *AspMaxRequestEntityAllowed* (default is 200000 bytes) in metabase.xml.
[B]
IIS7[/B] uses *maxRequestEntityAllowed: appcmd set config /section:asp /maxRequestEntityAllowed:int* (default is 200000 bytes)

**Apache** uses *LimitRequestBody* (default is 2GB)

---

### Post by technimage on 2012-12-18
I understood everything in the first paragraph : let's say that java is the least-worst option.

However, I'm not sure I got everything in what you said next... My only imperative is that users must be able to upload and download from any operating systems and within any modern internet browser. Are you saying that I would be able to allow this just using SFTP? If so, I'm all for it but please explain to me a little bit more what you say :p

---

### Post by sandyd on 2012-12-18
> **technimage said:**
> I understood everything in the first paragraph : let's say that java is the least-worst option.

However, I'm not sure I got everything in what you said next... My only imperative is that users must be able to upload and download from any operating systems and within any modern internet browser. Are you saying that I would be able to allow this just using SFTP? If so, I'm all for it but please explain to me a little bit more what you say :p

use a java ftp client
there are a few around, but no names come to mind atm

---

### Post by SeijiSensei on 2012-12-18
PHP has a file uploading limit as well.  The default is small:

```
upload_max_filesize = 2M
```

It's in /etc/php5/apache2/php.ini.

You might consider setting up a [WebDAV]("http://httpd.apache.org/docs/2.2/mod/mod_dav.html") share.  That looks like a desktop folder to the enduser.  Size limits are handled with [LimitXMLRequestBody](http://httpd.apache.org/docs/2.2/mod/core.html#limitxmlrequestbody)  A value of zero disables limit checking.  You also need to control permissions carefully so that users cannot see, or worse delete, each others files unless that is considered acceptable.

---

### Post by CharlesA on 2012-12-18
> **sandyd said:**
> use a java ftp client
there are a few around, but no names come to mind atm

+1, even though I loathe Java for the amount of security holes it has.

---

### Post by technimage on 2012-12-19
Thanks for the feedback !

I'm actually going for a solution which uses Plupload, a Javascript API which will allow the chunking of files. So that the files won't eat all the memory of the uploader's computer, I will be using a Java applet. I'll let you know if that works, I found this solution here :
[URL="Thanks for the feedback !

I'm actually going for a solution which uses Plupload, a Javascript API which will allow the chunking of files. So that the files won't eat all the memory of the uploader's computer, I will be using a Java applet. I'll let you know if that works, I found this solution here :
http://dev.wavemaker.com/forums/?q=node/8882#comment-31377"]http://dev.wavemaker.com/forums/?q=node/8882#comment-31377[/URL]

---

