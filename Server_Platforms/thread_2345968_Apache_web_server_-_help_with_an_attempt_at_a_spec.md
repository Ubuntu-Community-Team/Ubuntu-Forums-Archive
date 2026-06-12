---
title: "Apache web server - help with an attempt at a specific RewriteCond"
date: 2016-12-09
forum: Server Platforms
---

### Post by Doug S on 2016-12-09
Hi all,

Note: in this post substitute HTTP wherever it says ZZZZ. It was the only way I could get the system to accept this post. see [here]("https://ubuntuforums.org/showthread.php?t=2331266&page=30&p=13580829#post13580829").

In the last couple of months my web site has been having two types of bursts of requests. I have been attempting to implement "RewriteCond" towards the goals of: Less bytes delivered; Telling them where to go. One of the two issues (by far the worse offender) I have been successful with:```
# Tell the wp-login followed by root page fetch
# clients where to go.
# Server load is reduced because many many less
# bytes get sent.
# While the identifier string seems unique, there
# may be collateral damage.

RewriteCond %{HTTP_USER_AGENT} rv:40\.0
RewriteRule .* /~doug/rewriterules/foff\.txt [PT]

```However, the other one, never the same IP address,  uses a fake Googlebot user agent, but can be identified as fake because it uses ZZZZ/1.0 and doesn't say that compression is allowed. Example:```
82.81.202.52 - - [08/Dec/2016:16:16:20 -0800] "GET / ZZZZ/1.0" 200 10000 "-" "Mozilla/5.0 (compatible; Googlebot/2.1; +http://www.google.com/bot.html)"
```For reference, a real googlebot request:```
66.249.79.182 - - [06/Dec/2016:02:27:36 -0800] "GET / ZZZZ/1.1" 200 3731 "-" "Mozilla/5.0 (compatible; Googlebot/2.1; +http://www.google.com/bot.html)"
```Notice the compressed delivery (many less bytes) and ZZZZ/1.1.  This is what I have tried so far:```
# (Attempt to) identify fake Googlebot user agents,
# and then tell them where to go.
# Server load is reduced because many many less
# bytes get sent.

RewriteCond %{HTTP_USER_AGENT} Googlebot
# Doesn't work:
# RewriteCond %{REQUEST_VERSION} 1\.0
# Doesn't work:
# RewriteCond %{REQUEST_URI} HTTP/1\.0
# Doesn't work:
# RewriteCond %{QUERY_STRING} HTTP/1\.0
# Untested: Something like the lack of:
# RewriteCond %{HTTP:Accept-Encoding} gzip
# Doesn't work:
# RewriteCond %{REQUEST_PROTOCOL} HTTP/1\.0
RewriteCond %{THE_REQUEST} HTTP/1\.0

RewriteRule .* /~doug/rewriterules/googlefoff\.txt [PT]
```I do not yet know if the last one works or not, as I haven't had a hit yet. I have been having trouble finding documentation or examples for things like "REQUEST_VERSION".  Nor, have I been able to figure out how to do a compression based rule examining the "Accept-Encoding" portion of the request, or even the lack of any "Accept-Encoding" segment.

Does anybody have any suggestions?

---

### Post by Graham_Willis on 2016-12-10
Test message as the attempt to send the reply was unsuccessful.

---

### Post by Graham_Willis on 2016-12-10
On the end of the post you'll find the information how not to wait for a hit but generate one on your own.

Try SERVER_PROTOCOL:

[https://httpd.apache.org/docs/2.4/expr.html](https://httpd.apache.org/docs/2.4/expr.html) : 

> 
**SERVER_PROTOCOL** The protocol used by the request


I don't know if this variable displays the version of the protocol and not only if it's ZZZZ or ZZZZS. It seems to be the case - [https://www.experts-exchange.com/questions/21616020/Apache-Question-Can-I-block-ZZZZ-1-0-requests-using-http-conf-or-htaccess.html](https://www.experts-exchange.com/questions/21616020/Apache-Question-Can-I-block-ZZZZ-1-0-requests-using-http-conf-or-htaccess.html) :

> 
RewriteEngine on
RewriteCond %{SERVER_PROTOCOL} ^ZZZZ/1\.0$
RewriteRule ^.* -  [F]


but I haven't verified that.

**Another thing worth trying - possibly it will suit your needs best**:

[http://httpd.apache.org/docs/current/mod/mod_rewrite.html](http://httpd.apache.org/docs/current/mod/mod_rewrite.html) :

> 
**THE_REQUEST**
The full ZZZZ request line sent by the browser to the server (e.g., "GET /index.html ZZZZ/1.1"). This does not include any additional headers sent by the browser. This value has not been unescaped (decoded), unlike most other variables below.


[https://geekflare.com/apache-web-server-hardening-security/#45-Disable-HTTP-10-Protocol]("https://geekflare.com/apache-web-server-hardening-security/#45-Disable-ZZZZ-10-Protocol") :

> 
RewriteEngine On
RewriteCond %{THE_REQUEST} !ZZZZ/1.1$
RewriteRule .* - [F]


Another thing I suppose can be used: 

[https://httpd.apache.org/docs/2.4/mod/mod_setenvif.html](https://httpd.apache.org/docs/2.4/mod/mod_setenvif.html) :

> 
**Request_Protocol** - the name and version of the protocol with which the request was made (e.g., "ZZZZ/0.9", "ZZZZ/1.1", etc.)


[https://www.experts-exchange.com/questions/21616020/Apache-Question-Can-I-block-ZZZZ-1-0-requests-using-http-conf-or-htaccess.html](https://www.experts-exchange.com/questions/21616020/Apache-Question-Can-I-block-ZZZZ-1-0-requests-using-http-conf-or-htaccess.html) : 

> 
SetEnvIf Request_Protocol ZZZZ/0.9 too_low_proto
SetEnvIf Request_Protocol ZZZZ/1.0 too_low_proto
Deny from env=too_low_proto


Is it your server or do you have your site on a shared hosting or something? ModSecurity has the option to enforce a specific ZZZZ protocol version, but I believe you have to be the administrator of your server and I don't know if it's possible to achieve such a conjunction of conditions that you desire (if it is, it's probably hard) - so it's more like aside note:

[https://github.com/SpiderLabs/ModSecurity/wiki/Reference-Manual#REQUEST_PROTOCOL](https://github.com/SpiderLabs/ModSecurity/wiki/Reference-Manual#REQUEST_PROTOCOL) :

> 
**REQUEST_PROTOCOL**

This variable holds the request protocol version information.

SecRule REQUEST_PROTOCOL "!^ZZZZ/(0\.9|1\.0|1\.1)$" "id:51"


Also worth noting that mod_policy is coming:

[https://httpd.apache.org/docs/trunk/mod/mod_policy.html](https://httpd.apache.org/docs/trunk/mod/mod_policy.html) :

> 
**POLICY_VERSION** : Enforce a minimum ZZZZ version within a request
When a request is encountered with an ZZZZ version number less than the required minimum version, the request is rejected. The following version numbers are recognised:
ZZZZ/1.1
ZZZZ/1.0
ZZZZ/0.9
 

As about waiting for the hit - you can telnet to the port 80 and talk with server directly indicating ZZZZ/1.0 version. You'll find on google more details how to do that. But there are ready tools which allows you to define the headers and talk to WWW server in more convenient way (just some clicks). You can also write a little shell script for that.

If you need more detailed instructions, write.

---

### Post by Doug S on 2016-12-10
Thanks for the reply.

> **Graham_Willis said:**
> Is it your server or do you have your site on a shared hosting or something?It is my server. An Ubuntu 16.04 server.

> **Graham_Willis said:**
> As about waiting for the hit - you can telnet to the port 80 and talk with server directly indicating ZZZZ/1.0 version. You'll find on google more details how to do that. But there are ready tools which allows you to define the headers and talk to WWW server in more convenient way (just some clicks). You can also write a little shell script for that.It is late here, I'll try it tomorrow. It hasn't been an issue until tonight, as hits were pretty frequent before. I've had a burst of the first issue all evening, the one I am dealing with fine.

---

### Post by Graham_Willis on 2016-12-10
**Doug_S: note that I edited my message, so take another look at it (THE_REQUEST method added).**

I confirm that there are problems when there is the string "HTTP" in a post, it says something like "you don't have access to /newphp on this server". Second, if one is in edit mode and paste a link then you'll immediately find curson at the end of your message. I suppose that the application is to be blamed for that and not the server, but something should really be done with both the issues, it's extremely annoying, especially on a technical forum. Perhaps it isn't the place where it should be written, but sorry, I really don't have more patience after fighting with forum just to send the message.

---

### Post by Doug S on 2016-12-10
Graham, thanks very much for your reply.

There is an ongoing thread (almost 5 months now) about posting issues, and I added a comment that you had the same issue with (spaces added) H T T P / 1 . 0 (or 1) in a post. See EDIT 2 [here]("https://ubuntuforums.org/showthread.php?t=2331266&page=30&p=13580829#post13580829").

I did find a couple of the references you gave, and thanks for them and the others. I also realize some of the mistakes I was making, i.e. using REQUEST_URL and QUERY_STRING was clearly wrong, and perhaps I should have reduced my original post to eliminate some noise. I'll try SERVER_PROTOCOL.

As for waiting for a hit: This is odd, but not inconsistent with this stuff.  Before last night, I never had to wait for more than a couple of hours for a hit. Oh, wait, darn it, I missed two hits. The current THE_REQUEST method seems to be working (also verified via examining the raw packets with wireshark):
```
doug@DOUG-64:~$ [COLOR="#FF0000"]grep Google access.log | grep "H T T P / 1 \ . 0"[/COLOR]
107.5.126.22 - - [09/Dec/2016:07:56:08 -0800] "GET / H T T P / 1 . 0" 200 10000 "-" "Mozilla/5.0 (compatible; Googlebot/2.1; +http://www.google.com/bot.html)"
107.5.126.22 - - [09/Dec/2016:07:56:09 -0800] "GET / H T T P / 1 . 0" 200 10000 "-" "Mozilla/5.0 (compatible; Googlebot/2.1; +http://www.google.com/bot.html)"
107.5.126.22 - - [09/Dec/2016:07:56:11 -0800] "GET / H T T P / 1 . 0" 200 10000 "-" "Mozilla/5.0 (compatible; Googlebot/2.1; +http://www.google.com/bot.html)"
107.5.126.22 - - [09/Dec/2016:07:56:15 -0800] "GET / H T T P / 1 . 0" 200 10000 "-" "Mozilla/5.0 (compatible; Googlebot/2.1; +http://www.google.com/bot.html)"
107.5.126.22 - - [09/Dec/2016:07:56:23 -0800] "GET / H T T P / 1 . 0" 200 10000 "-" "Mozilla/5.0 (compatible; Googlebot/2.1; +http://www.google.com/bot.html)"
107.5.126.22 - - [09/Dec/2016:07:56:42 -0800] "GET / H T T P / 1 . 0" 200 10000 "-" "Mozilla/5.0 (compatible; Googlebot/2.1; +http://www.google.com/bot.html)"
... made the change from the last failed attempt ...
96.241.39.2 - - [09/Dec/2016:09:29:10 -0800] "GET / H T T P / 1 . 0" 200 323 "-" "Mozilla/5.0 (compatible; Googlebot/2.1; +http://www.google.com/bot.html)"
124.13.5.75 - - [09/Dec/2016:19:04:24 -0800] "GET / H T T P / 1 . 0" 200 323 "-" "Mozilla/5.0 (compatible; Googlebot/2.1; +http://www.google.com/bot.html)"

```**Note: Spaces used above instead of ZZZZ substitution.**

Because it would also make the solution for the first  issue more robust, I would really like to make a decision based on the presence of the Accept-Encoding segment. Psudocode:
```
after previous condition check
If the client does not supply Accept-Encoding
then they are bad, send them short nasty txt message
endif

```I'll keep working on that.

---

### Post by Doug S on 2016-12-27
> **Doug S said:**
> Because it would also make the solution for the first  issue more robust, I would really like to make a decision based on the presence of the Accept-Encoding segment. Psudocode:
```
after previous condition check
If the client does not supply Accept-Encoding
then they are bad, send them short nasty txt message
endif

```I'll keep working on that.I do not know how to test for Accept-Encoding being non-existent or a NULL string or whatever, but testing against some content seems to work. This is what I am running at the moment (Note: in order to enable posting to actually work a space has been added to "HT TP/1.0". I used ZZZZ and a bunch of spaces previously, but one space seems to be enough):```
...
RewriteRule .* /~doug/rewriterules/banned\.txt [PT]

# Tell the wp-login followed by root page fetch
# clients where to go.
# Server load is reduced because many many less
# bytes get sent.
# While the identifier string seems unique, there
# may be collateral damage.
# They have no Accept Encoding
RewriteCond %{HTTP_USER_AGENT} rv:40\.0
RewriteCond %{HTTP:Accept-Encoding} !gzip
RewriteRule .* /~doug/rewriterules/foff\.txt [PT]

# (Attempt to) identify fake Googlebot user agents,
# and then tell them where to go.
# Server load is reduced because many many less
# bytes get sent.

# 1: Experiment, use googlefoff1.txt (different length)
RewriteCond %{HTTP_USER_AGENT} Googlebot
# Doesn't work: ?
# RewriteCond %{REQUEST_VERSION} HT TP/1\.0
# Doesn't work: URI has been parsed out of the request
# RewriteCond %{REQUEST_URI} HT TP/1\.0
# Doesn't work: I misunderstood. Clearly wrong.
# RewriteCond %{QUERY_STRING} HT TP/1\.0
# Doesn't work: As far as I can determine, this should work.
RewriteCond %{REQUEST_PROTOCOL} HT TP/1\.0
RewriteRule .* /~doug/rewriterules/googlefoff1\.txt [PT]

# 2: this works
RewriteCond %{HTTP_USER_AGENT} Googlebot
RewriteCond %{HTTP:Accept-Encoding} !gzip
RewriteRule .* /~doug/rewriterules/googlefoff\.txt [PT]

# 3: this works. (Commented out, because 2 works and it is
# superior. HT TP/1.1 has been observed, albeit rarely.)
# RewriteCond %{HTTP_USER_AGENT} Googlebot
# RewriteCond %{THE_REQUEST} HT TP/1\.0
# RewriteRule .* /~doug/rewriterules/googlefoff\.txt [PT]

# The next rule
```I set this one to solved shortly. While I still have stuff to figure out, it seems to working good enough for now.

---

