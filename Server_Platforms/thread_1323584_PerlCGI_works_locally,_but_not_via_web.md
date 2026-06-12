---
title: "Perl/CGI works locally, but not via web"
date: 2009-11-11
forum: Server Platforms
---

### Post by rebeltaz on 2009-11-11
I don't know if this is the right place to ask this, but I think i am just doing something wrong Linux-wise... 

I installed a program on my Linux-Apache web server called Perlfect. It's a two part search engine written in Perl. The first script indexes your site and the second script manages the actual search requests. 

I have run the indexer.pl script successfully locally to index the site, so I assume that Perl is installed correctly. I tried to run the search.pl script through a Firefox web browser and I get a 404 File Not Found error. I created a test.cgi script and ran it locally just fine. Again, over the web a 404 error. The test.cgi script is:

```
#!/usr/bin/perl

print "Content-type: text/plain\n\nHet werkt!\n";
```

I have ensured that the file permissions are set with chmod 755 on both the Perlfect scripts as well as my test script and I have CGI Scripts enabled in ISPConfig. I cannot figure out why they won't work remotely. Does anyone have any ideas? I will happily supply any information that you need. Thanks in advance....

Oh... the search.pl path is:
[http://www.RobotsAndComputers.com/cgi-bin/perlfect/search/search.pl](http://www.RobotsAndComputers.com/cgi-bin/perlfect/search/search.pl)

and the test.cgi script is:
[http://www.RobotsAndComputers.com/cgi-bin/test.cgi](http://www.RobotsAndComputers.com/cgi-bin/test.cgi)

---

### Post by mrsteveman1 on 2009-11-11
So you're serving it with Apache2?

Can you post your vhost config?

---

