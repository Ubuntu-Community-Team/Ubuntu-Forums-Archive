---
title: "Storing notes?"
date: 2010-03-13
forum: The Cafe
---

### Post by lz1dsb on 2010-03-13
Does anybody now a suitable software for storing small notes? I know that there're many, but what I'm looking for is something that can be run on a server and accessed via web. Like Bugzilla for example. My brother has a server with real IP address which I can access from anywhere, so I'm already using Bugzilla to note all the problems and symptoms that I notice on my machine along with the information I found so far, and I can use that info to work on the problem later. This saves me a lot of time, as I don't have to start working on the problem all over again, but start from where I've left it. 
So I'm looking for something similar, but just for storing small notes, being able to arrange them and search them later. I have a notebook where I'm noting interesting Linux commands and cli applications, but it's getting quite uncomfortable because I have to carry that notebook around, plus it's impossible to arrange the information in a convenient way. And using a local application isn't any more convenient either, as I'm using two laptops and few virtual machines, so it's quite a hassle to synchronize all the data. Any ideas?

Cheers,
Boyan

---

### Post by laceration on 2010-03-13
I think I read that you can use the tomboy notes program with ubuntuone.  

I use a program that I wrote myself.  It is small + I think good, but I never made it public because it works w/ php, mysql + a server, which your average user doesn't want to mess with.  If you are interested, I'd be happy to post it here.  It is only about 300 lines of code and 1 db table.  I only use it over a local network so I never added any security features that you may need.

---

### Post by hessiess on 2010-03-13
Personally I just use Vim and a load of text files in my SVN repo.

> 
I use a program that I wrote myself. It is small + I think good, but I never made it public because it works w/ php, mysql + a server, which your average user doesn't want to mess with. If you are interested, I'd be happy to post it here. It is only about 300 lines of code and 1 db table. I only use it over a local network so I never added any security features that you may need.


If you think it would be usable to a wider audience, clean up/comment the code and throw it on sourceforce. You would have to make sure that its not vulnerable to cross site scripting or SQL injection first though, and write some documentation.

---

### Post by koleoptero on 2010-03-13
[Tiddlywiki?]("http://www.tiddlywiki.com/")

---

### Post by laceration on 2010-03-13
> If you think it would be usable to a wider audience
Already explained, I don't.
> You would have to make sure that its not vulnerable to cross site scripting or SQL injection first though
Not necessary. Cross site scripting or SQL injection are dangers from malicious public users.  Since he wants something for private use he would only need to password protect it, if using on a public server.

---

### Post by kellemes on 2010-03-13
> **koleoptero said:**
> [Tiddlywiki?]("http://www.tiddlywiki.com/")

+1

Installed this on my own server, extremely fast (no DB, all in one file) and easy to work with.. no complex server-apps and no buggy client-apps, just one page on the server and you're basically done.

---

### Post by lz1dsb on 2010-03-15
Thanks for all the suggestions. I really appreciate them. This TiddlyWiki looks quite promising. I think I'm going to give it a try.

Cheers,
Boyan

---

