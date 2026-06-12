---
title: "apache serve different content to firefox and lynx/wget hexadecimal mystery"
date: 2008-03-24
forum: Server Platforms
---

### Post by leohart on 2008-03-24
My webpage (served by Ubuntu with LAMP) works fine when I access it with Firefox, but when I use Lynx, the page is prepended by some hexadecimal number.

The reason I found out is because I used file_get_contents in PHP to fetch a page served by Ubuntu LAMP. 

When I visit this page with Firefox, nothing weird is going on and it is really fast. When I use wget/lynx or file_get_contents(), the page takes 5 times longer and output some junk at the top.

What is going on?

The same site was working perfectly in a Centos installation. I switched over to Ubuntu and now -_-. Please help guys.

---

### Post by mssever on 2008-03-26
> **leohart said:**
> My webpage (served by Ubuntu with LAMP) works fine when I access it with Firefox, but when I use Lynx, the page is prepended by some hexadecimal number.

The reason I found out is because I used file_get_contents in PHP to fetch a page served by Ubuntu LAMP. 

When I visit this page with Firefox, nothing weird is going on and it is really fast. When I use wget/lynx or file_get_contents(), the page takes 5 times longer and output some junk at the top.

What is going on?

The same site was working perfectly in a Centos installation. I switched over to Ubuntu and now -_-. Please help guys.
I don't know about the speed issue, but the number issue might be related to a character set problem. I had a similar problem when I switched from Windows to Ubuntu. Windows text editors (at least the ones I used) like to insert a hidden character (a byte order mark, I believe) at the beginning of each file, which Ubuntu didn't like. The solution was to fiddle with my text editor's character set options until the character became visible; then I deleted it and the problem went away.

It's possible that the speed issue has something to do with the fact that the file that's being sent (with the gibberish at the beginning) isn't a valid HTML file. But that's just a wild guess.

---

### Post by leohart on 2008-03-26
Hi mssever. Thanks for the response. I found out last night that the numbers in front of the output HTML is actually caused by HTTP/1.1 Transfer-Encoding:chunked mode. For clients that do not understand chunked mode, the number is output as if it is actually just HTML.

PHP file_get_contents() function does not understand HTTP/1.1 so that is what caused the problem.

I still cannot find the fix because for some reason, Apache insisting on sending HTTP/1.1 response despite php requesting in HTTP/1.0. I tried to set some environment variables but it doesn't work out either.

I wonder if anyone has had some experience in this matter.

---

### Post by mssever on 2008-03-26
Hmm... That's odd that file_get_contents() doesn't understand HTTP/1.1. In my opinion, anything that understands HTTP/1.0 but not HTTP/1.1 is broken, because HTTP/1.1 has been around for a long time. Also, some sites (shared hosting, mostly) can't work without HTTP/1.1.

But it's also odd that Apache isn't downgrading. Have you looked through the Apache manual?

---

### Post by leohart on 2008-03-26
I believe that it should support HTTP/1.1. However, according to these pages, fopen (which is used by file_get_contents()) doesn't support HTTP/1.1
[http://us2.php.net/fopen](http://us2.php.net/fopen)
[http://us2.php.net/manual/en/wrappers.http.php](http://us2.php.net/manual/en/wrappers.http.php)

I looked into the Apache manual and there are several environment variables, most notably, force-response-1.0 and downgrade-1.0 that might be able to help. However, my effort so far trying to tinker with those options do not turn out well :(

---

### Post by mssever on 2008-03-26
> **leohart said:**
> I believe that it should support HTTP/1.1. However, according to these pages, fopen (which is used by file_get_contents()) doesn't support HTTP/1.1
[http://us2.php.net/fopen](http://us2.php.net/fopen)
[http://us2.php.net/manual/en/wrappers.http.php](http://us2.php.net/manual/en/wrappers.http.php)

I looked into the Apache manual and there are several environment variables, most notably, force-response-1.0 and downgrade-1.0 that might be able to help. However, my effort so far trying to tinker with those options do not turn out well :(

Where are you setting the environment variables? They have to be set in--or inherited by--Apache's parent process.

I just looked through my /etc/apache2/apache2.conf and saw the BrowserMatch directive. I wonder if that would work.

---

### Post by leohart on 2008-03-26
I tried the Browser Match directive as well. In Browser Match directive, it specifies that if the user-agent is MSIE4\.0b; then it will serve the page in HTTP/1.0 no matter what.

I tried supplying this user-agent to wget but the result is still the same. Chunked encoding doesn't work. I can't help but wondering, how come if I use wget on any site (let's say Google.com), I don't encounter this problem but if I use it on my site which is Apache2 on Ubuntu served by Textpattern CMS, then the problem persists. Am I missing something?

---

### Post by mssever on 2008-03-26
> **leohart said:**
> I tried the Browser Match directive as well. In Browser Match directive, it specifies that if the user-agent is MSIE4\.0b; then it will serve the page in HTTP/1.0 no matter what.

I tried supplying this user-agent to wget but the result is still the same. Chunked encoding doesn't work. I can't help but wondering, how come if I use wget on any site (let's say Google.com), I don't encounter this problem but if I use it on my site which is Apache2 on Ubuntu served by Textpattern CMS, then the problem persists. Am I missing something?

What happens if you set BrowserMatch to Wget? In other words, match the User-Agent header.

I'm also wondering if your CMS might be interfering with what you're trying to do.

EDIT: After reading the wget man page, I infer that you can avoid chunked encoding by setting a proper Content-Length header on the file you're trying to download.

---

