---
title: "Apache2 - Only allowing certiain filetypes"
date: 2006-10-04
forum: Server Platforms
---

### Post by paul.maddox on 2006-10-04
How can I configure our apache2 servers to only serve the following filetypes, and deny all others with a 404 error?

 *.php
 *.htm
 *.html
 *.css
 *.js
 *.jpg
 *.jpeg
 *.gif
 *.png
 *.svg
 *.pdf

Thanks.

---

### Post by kidders on 2006-10-04
Hi there,

That's a very odd request! HTTP response code 404 means "File not found". So you want your server to ***lie*** about what it's got in its directory tree?! I can't help wondering why files you don't want served would be there in the first place :-k hehe.

You *could* try using the rewrite engine to send requests for things that don't have one of the extentions you listed to a URL that doesn't exist. This would have the desired result in many cases, but the redirects wouldn't really be based on the file *types* like you asked :-(

The fact that a file's name ends in ".pdf" doesn't make it a PDF document. So, the fact that ".tar.gz" files wouldn't be served by your server would have no useful effect, since gzipped tarballs could be given any (or no) extention, and still work perfectly.

I've thought about this for a few minutes, and the only reasonable solution that strikes me is to pass all requests through a PHP script, again, with apache's rewrite engine. The script could read a file's magic number, decide what kind of file it is, and on that basis, either dump the file to the requesting browser or fake a HTTP 404 error.

Any help?

---

### Post by paul.maddox on 2006-10-04
Occasionally certain files get left in production server web directories by developers that should not be there.

For example, tar.gz's, VI swap files etc.

I do not want any of these to be accessable publically.

I really do not want to have to pass everything through a PHP wrapper file, this would have speed implications for us. 

Surely there must be a way using either a rewrite rule, or apache's <FilesMatch> directive, but I can't work it out!

---

### Post by kidders on 2006-10-04
Yeah, If you're running a production server, passing everything through a script would be out of the question. Can't your devs simply keep the permissions they assign to private files consistent with the idea that they shouldn't be served, though? Linux kinda depends on the idea that people assign the minimum possible permissions to any given resource, to remain secure, so it's usually not much of an ask.

I wonder if my first suggestion is the way to go then. Your file type restrictions are there to *help* your devs, so they are (hopefully) unlikely to try to circumvent them. Getting the regular expression right might take a little trial and error though!

---

### Post by sonic2000gr on 2006-10-04
You could also install an Apache module called mod_security. This will give you a lot of options to what gets served and what error message will be produced otherwise (plus protection from many common attacks).

---

### Post by paul.maddox on 2006-10-05
Bingo!

We already use mod-security, so it was just a case of working out the rule. 

So far i've got:

# Only allow certain filetypes
SecFilter "\.[^php|htm|html|css|js|jp?g|gif|png|svg|tiff|pdf]" "deny,status:404"

I still need to find out how to only apply the rule to GET requests as currently if you type blah.zip into a text box and submit it through POST it will trigger the rule which I don't want.

---

### Post by paul.maddox on 2006-10-05
Hmm, I thought I had it sussed, but it turns out I'm just not very good at regular expressions!

SecFilter "\.[^(php|html)]" "deny"

I thought that would block all requests that didn't have the extension .php or .html

It doesn't. It blocks any request that doesn't have the letter p or h in the extension :(


I don't suppose anyone has 5mins free to lend me a hand with the correct regular expression?

---

### Post by kidders on 2006-10-05
Hi again,

I don't know much about this extension :-( Are you allowed to specify more than one SecFilter directive? I'm wondering if it's possible to do something like...

Allow .php
Allow .png
Allow .html
...
...
Deny all

(If you know what I mean)

I came across [http://www.howtoforge.com/apache_mod_security](http://www.howtoforge.com/apache_mod_security) -- have you seen it?

---

### Post by sonic2000gr on 2006-10-05
Wikipedia has a nice article on regular expressions [here]("http://en.wikipedia.org/wiki/Regular_expression"). You can have as many SecFilter statements as you wish (but then I guess paul already knows this).
I would like to help you but I don't really know any more regular expressions than you do at the moment :(

---

