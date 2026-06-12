---
title: "Apache Rewite rule set issue - false triggering"
date: 2013-09-14
forum: Server Platforms
---

### Post by Doug S on 2013-09-14
Hi Everybody,

I have never used mod-rewrite and Rewrite rules before, and I am stuck in a couple of spots.

Background / Context: For many many months now, there have been several tens of accesses per day to a certain page on my web site with a forged referrer. The source IP addresses do not repeat, or if they do, not often. The page is never fully downloaded, meaning the figures and other context are never fetched. The forged referrer URL is actually the root page for my own site, and that page does NOT contain a link to the page in question. I have no clue as to the purpose for doing this nor what purpose it could possibly serve, other than maybe content linked from elsewhere. Anyway, I decided to try to block delivery for this use case.

I have one scenario sort of working, however it is also blocking legitimate attempts to access the page. Here is the rule set (I have added zzz to my domain name, just to throw off bots):```
doug@doug-64:~/public_html$ cat .htaccess
RewriteEngine on
RewriteCond %{REQUEST_URI} /~doug/strange_get.html
RewriteCond %{HTTP_REFERER} http://www.smythieszzz.com/
RewriteRule .* - [G]
```And here are some access attempts, where the ones from the internal IP address are legitimate:```
198.50.236.156 - - [14/Sep/2013:06:17:57 -0700] "GET [COLOR=#ff0000]/~doug/strange_get.html[/COLOR] HTTP/1.1" [COLOR=#ff0000]410[/COLOR] 584 "[COLOR=#ff0000]http://www.smythieszzz.com/[/COLOR]" "Mozilla/5.0 (iPad; CPU OS 5_1_1 like Mac OS X) AppleWebKit/534.46 (KHTML, like Gecko) Version/5.1 Mobile/9B206 Safari/7534.48.3"
108.163.221.46 - - [14/Sep/2013:06:41:30 -0700] "GET [COLOR=#ff0000]/~doug/strange_get.html[/COLOR] HTTP/1.0" [COLOR=#ff0000]410[/COLOR] 584 "[COLOR=#ff0000]http://www.smythieszzz.com/[/COLOR]" "Mozilla/5.0 (iPad; CPU OS 5_1_1 like Mac OS X) AppleWebKit/534.46 (KHTML, like Gecko) Version/5.1 Mobile/9B206 Safari/7534.48.3"
192.168.111.101 - - [14/Sep/2013:07:16:41 -0700] "GET [COLOR=#ff0000]/~doug/strange_get.html[/COLOR] HTTP/1.1" [COLOR=#ff0000]410[/COLOR] 583 "[COLOR=#ff0000]http://www.smythieszzz.com/~doug/index.html[/COLOR]" "Mozilla/5.0 (Windows NT 6.0; rv:23.0) Gecko/20100101 Firefox/23.0"
192.168.111.101 - - [14/Sep/2013:07:20:23 -0700] "GET [COLOR=#ff0000]/~doug/strange_get.html[/COLOR] HTTP/1.1" [COLOR=#ff0000]410[/COLOR] 584 "[COLOR=#ff0000]http://www.smythieszzz.com/~doug/[/COLOR]" "Mozilla/5.0 (Windows NT 6.0; rv:23.0) Gecko/20100101 Firefox/23.0"
37.59.68.212 - - [14/Sep/2013:07:23:11 -0700] "GET [COLOR=#ff0000]/~doug/strange_get.html[/COLOR] HTTP/1.0" [COLOR=#ff0000]410[/COLOR] 584 "[COLOR=#ff0000]http://www.smythieszzz.com/[/COLOR]" "Mozilla/5.0 (iPad; CPU OS 5_1_1 like Mac OS X) AppleWebKit/534.46 (KHTML, like Gecko) Version/5.1 Mobile/9B206 Safari/7534.48.3"
37.59.68.212 - - [14/Sep/2013:07:25:08 -0700] "GET [COLOR=#ff0000]/~doug/strange_get.html[/COLOR] HTTP/1.0" [COLOR=#ff0000]410[/COLOR] 584 "[COLOR=#ff0000]http://www.smythieszzz.com/[/COLOR]" "Mozilla/5.0 (iPad; CPU OS 5_1_1 like Mac OS X) AppleWebKit/534.46 (KHTML, like Gecko) Version/5.1 Mobile/9B206 Safari/7534.48.3"
```The rule appears to be triggering if the referrer contains "http://www.smythieszzz.com" in any larger context, but I want it to trigger only on exactly that context, nothing more. It is unclear to me how to modify the syntax to fix it. The other possibility is that perhaps the conditions rules have an implied "OR", but in my readings I thought one had to specify "OR", so I assumed (perhaps incorrectly) it was an implied "AND".

Part 2:
What I really want to do is substitute the reply with a text file:```
doug@doug-64:~/public_html$ cat forged.txt
Your request HTTP_REFERER is forged. Please go away.
```And the rule set I have, which doesn't seem to work at all:```
doug@doug-64:~/public_html$ cat .htaccess.doug2
RewriteEngine on
RewriteCond %{HTTP_REFERER} http://www.smythieszzz.com/
RewriteRule ^/strange_get\.html /~doug/forged.txt [PT]
```which gives:```
78.157.211.101 - - [14/Sep/2013:08:05:02 -0700] "GET [COLOR=#ff0000]/~doug/strange_get.html[/COLOR] HTTP/1.0" [COLOR=#ff0000]200[/COLOR] 7413 "[COLOR=#ff0000]http://www.smythieszzz.com/[/COLOR]" "Mozilla/5.0 (iPad; CPU OS 5_1_1 like Mac OS X) AppleWebKit/534.46 (KHTML, like Gecko) Version/5.1 Mobile/9B206 Safari/7534.48.3"
```Any help appreciated.

---

### Post by Doug S on 2013-09-17
I made this change:```
doug@doug-64:~/public_html$ cat .htaccess
RewriteEngine on
RewriteCond %{HTTP_REFERER} http://www\.smythieszzz\.com/
[COLOR=#ff0000]RewriteCond %{HTTP_REFERER} !doug[/COLOR]
RewriteCond %{REQUEST_URI} /~doug/strange_get\.html
RewriteRule .* - [G]
```And it seems to work as I was wanting:```
192.168.111.101 - - [17/Sep/2013:09:35:19 -0700] "GET /~doug/strange_get.html HTTP/1.1" [COLOR=#ff0000]200 [/COLOR]7412 "[COLOR=#ff0000]http://www.smythieszzz.com/~doug/index.html[/COLOR]" "Mozilla/5.0 (Windows NT 6.0; rv:23.0) Gecko/20100101 Firefox/23.0"
190.79.39.164 - - [17/Sep/2013:09:36:33 -0700] "GET /~doug/strange_get.html HTTP/1.0" [COLOR=#ff0000]410[/COLOR] 521 "[COLOR=#ff0000]http://www.smythieszzz.com/[/COLOR]" "Mozilla/5.0 (iPod; CPU iPhone OS 6_1_3 like Mac OS X) AppleWebKit/536.26 (KHTML, like Gecko) Version/6.0 Mobile/10B329 Safari/8536.25"
```I suspect I can do similar for my part 2 issue, perhaps not elegant but functional. I'll report back when I have tried it.

---

### Post by hawkmage on 2013-09-17
One thing to keep in mind is that the Condition pattern in the RewriteCond directive can be a Perl compatible regular expression.  So if you only want HTTP_REFERER to start with "http://www.smythieszzz.com/" then you can use the condition pattern of: ^[http://www\.smythieszzz\.com/](http://www\.smythieszzz\.com/).  The ^ is an regular expression symbol to ancor the match at the beginning of the string.  If you use both http and https you can use this pattern:  https?://www\.smythieszzz\.com/.  The ? indicates the preceding character is optional in the match.

---

### Post by Doug S on 2013-09-17
For my part 2 issue, I did this:```
doug@doug-64:~/public_html$ cat .htaccess
RewriteEngine on
RewriteCond %{HTTP_REFERER} http://www\.smythieszzz\.com/
RewriteCond %{HTTP_REFERER} !doug
RewriteCond %{REQUEST_URI} /~doug/strange_get\.html
RewriteRule .* /~doug/forged\.txt [PT]
```and it seems to be working (where 411 bytes returned would be the short text file and 7413 bytes returned would be the original content, compressed):```
99.59.130.154 - - [17/Sep/2013:12:27:15 -0700] "GET /~doug/strange_get.html HTTP/1.1" [COLOR=#ff0000]200[/COLOR] [COLOR=#ff0000]411[/COLOR] "[COLOR=#ff0000]http://www.smythieszzz.com/[/COLOR]" "Mozilla/5.0 (iPhone; CPU iPhone OS 6_1_4 like Mac OS X) AppleWebKit/536.26 (KHTML, like Gecko) Version/6.0 Mobile/10B350 Safari/8536.25"
198.143.144.180 - - [17/Sep/2013:12:33:58 -0700] "GET /~doug/strange_get.html HTTP/1.1" [COLOR=#ff0000]200 411[/COLOR] "[COLOR=#ff0000]http://www.smythieszzz.com/"[/COLOR] "Mozilla/5.0 (iPhone; CPU iPhone OS 6_1_4 like Mac OS X) AppleWebKit/536.26 (KHTML, like Gecko) Version/6.0 Mobile/10B350 Safari/8536.25"
78.23.223.114 - - [17/Sep/2013:13:34:58 -0700] "GET /~doug/strange_get.html HTTP/1.1" [COLOR=#ff0000]200 7413[/COLOR] "[COLOR=#ff0000]-[/COLOR]" "Mozilla/5.0 (X11; Ubuntu; Linux i686; rv:20.0) Gecko/20100101 Firefox/20.0"
78.23.223.114 - - [17/Sep/2013:13:34:59 -0700] "GET /~doug/strange_get_files/image009.jpg HTTP/1.1" 200 26629 "http://www.smythieszzz.com/~doug/strange_get.html" "Mozilla/5.0 (X11; Ubuntu; Linux i686; rv:20.0) Gecko/20100101 Firefox/20.0"
78.23.223.114 - - [17/Sep/2013:13:34:58 -0700] "GET /~doug/strange_get_files/image001.jpg HTTP/1.1" 200 48416 "http://www.smythieszzz.com/~doug/strange_get.html" "Mozilla/5.0 (X11; Ubuntu; Linux i686; rv:20.0) Gecko/20100101 Firefox/20.0"
78.23.223.114 - - [17/Sep/2013:13:34:59 -0700] "GET /~doug/strange_get_files/image008.jpg HTTP/1.1" 200 51409 "http://www.smythieszzz.com/~doug/strange_get.html" "Mozilla/5.0 (X11; Ubuntu; Linux i686; rv:20.0) Gecko/20100101 Firefox/20.0"
```@hawkimage: What I haven't figured out is if there is a one line way to do the referrer condition using regular expression stuff.
Anyway, I'll set this to "solved", and change the content of forged.txt to what I really want it to say.

---

