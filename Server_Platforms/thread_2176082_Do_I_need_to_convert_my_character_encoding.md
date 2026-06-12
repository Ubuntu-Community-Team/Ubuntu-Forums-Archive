---
title: "Do I need to convert my character encoding?"
date: 2013-09-22
forum: Server Platforms
---

### Post by coldraven on 2013-09-22
I maintain a web-site that has been online for about 12 years.
I originally created it using Dreamweaver on Windows but over the years various other editors and now I only run Linux.
Just recently I was using the cPanel editor and it gave me a big list of character formats which completely confused me.
Today, using Nautilus, I had connected via FTP and wanted to edit a file in Gedit. It returned an error saying that it was an unknown character set and it might introduce errors.
So I downloaded the file and used the "file" command which told me that it was ASCII (unextended?)
Then I ran iconv with the -c switch to prevent errors and after that Gedit did not complain.
```
 iconv -c -f ASCII -t UTF-8 news.htm > new_news.htm
```

Some of the web-pages have this in the head
```
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN">
  
<meta http-equiv="Content-Type" content="text/html; charset=windows-1252">
```

Some have this in the head and some have nothing at all.
```
<meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1">
```

So my question is should I convert the files and if so what character set should I use?

---

### Post by SeijiSensei on 2013-09-23
I'd use UTF-8 for everything, but ISO-8859-1 is fine for sites that have only Western languages.  I'd convert anything in the Windows character set.

The server has a default character set configured which is overriden by the <meta> declarations.  Usually it is UTF-8, though the organization of the Ubuntu Apache configuration files makes it hard for me to tell if that is the default.  I'm pretty sure it must be, though, since UTF-8 is the standard character set for Ubuntu and most other Linux distributions from the past few years.   So if there is no <meta> declaration, the server is probably using UTF-8.

---

### Post by coldraven on 2013-09-24
> **SeijiSensei said:**
> I'd use UTF-8 for everything, but ISO-8859-1 is fine for sites that have only Western languages.  I'd convert anything in the Windows character set.

The server has a default character set configured which is overriden by the <meta> declarations.  Usually it is UTF-8, though the organization of the Ubuntu Apache configuration files makes it hard for me to tell if that is the default.  I'm pretty sure it must be, though, since UTF-8 is the standard character set for Ubuntu and most other Linux distributions from the past few years.   So if there is no <meta> declaration, the server is probably using UTF-8.


Thanks, I will have to plod through all the files and convert them. It all seems to work at the moment so it seems like work for nothing but I guess that with mobile devices some problems will occur. As I do not own any I cannot be sure that it is displaying OK.
I was sort of hoping that someone else would take over the web-site and re-write the whole thing :)
I wrote in the days of dial-up so it was all optimised for slow connections, now I'm getting asked to make it more like Facebook :(
Any suggestions welcome!
[http://www.longhopelifeboat.org.uk/museum/index.htm](http://www.longhopelifeboat.org.uk/museum/index.htm)

Thanks again for your time.

---

