---
title: "Apache and Perl"
date: 2006-07-15
forum: Server Platforms
---

### Post by hitime on 2006-07-15
I'm trying to write some simplitic perl scripts (CGI) on my Sun Ultra 5. I just installed the latest version of Ubuntu, modified the virtualhost file so I can execute perl scripts, but yet all I get in the apache log is:

[Sat Jul 15 17:10:13 2006] [error] [client 71.241.177.91] Premature end of script headers: test1.cgi
[Sat Jul 15 17:11:50 2006] [error] [client 71.241.177.91] Premature end of script headers: test1.cgi
[Sat Jul 15 17:13:05 2006] [error] [client 71.241.177.91] Premature end of script headers: test1.cgi
[Sat Jul 15 17:13:16 2006] [error] [client 71.241.177.91] Premature end of script headers: test1.cgi


I have even tried just a basic script like:

hitime@ultra5:/var/www/test$ cat test1.cgi
#!/usr/bin/perl

print "<html><head></head><body>";
print "test";
print "</html></body>";
hitime@ultra5:/var/www/test$


and I still get:

[Sat Jul 15 17:13:16 2006] [error] [client 71.241.177.91] Premature end of script headers: test1.cgi

If someone can tell me if I'm missing a switch on the shebang line or maybe I have something miss configured I would greatly appreciate it...


hitime

---

### Post by muaddib on 2006-07-15
Hi,
> [Sat Jul 15 17:13:16 2006] [error] [client 71.241.177.91] Premature end of script headers: test1.cgi

The server may be looking for a header such as:
```
Content-Type:text
```
or
```
Content-Type:text/html
```
Which I think needs an extra blank line after it.
For example, try this program:
```

#!/usr/bin/perl
print "Content-Type:text\n\n";
print "Hello World!\n";

```

I hope this works for you.
-Muad'dib

---

