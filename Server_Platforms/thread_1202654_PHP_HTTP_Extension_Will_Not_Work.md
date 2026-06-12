---
title: "PHP HTTP Extension Will Not Work"
date: 2009-07-02
forum: Server Platforms
---

### Post by guywithcable on 2009-07-02
Hello All,

I have an Ubuntu 9.04 Server and I can't get the HttpRequest class to work.

I've followed all the instruction here:
[http://us3.php.net/manual/en/http.install.php](http://us3.php.net/manual/en/http.install.php)

and I still get this error:
**Fatal error**:  Class 'HttpRequest' not found in **/var/www/firstnet/firstnetaccess.php** on line [B]65

[/B]The odd thing is... it works on my Ubuntu Desktop test machine, after following the same instructions. :-k

Any help is greatly appreciated. :)

---

### Post by guywithcable on 2009-07-03
Am I the only PHP programmer on this forum? Anyone have any advice?

---

### Post by matt79 on 2009-07-03
What are you trying to do exactly? I clicked on the link but fail to see what you are trying to accomplish.

---

### Post by guywithcable on 2009-07-03
I'm using the HttpRequest class to make requests to a server and display the response (reformatted) to the user. It's so our sales staff doesn't have to bother logging in to our financial site all the time just to get a status.

The problem is that PHP doesn't think the class exists, even though the extension is installed.

---

### Post by matt79 on 2009-07-03
try adding 

extension = php_http.dll
to your php.ini

you might have to restart.

You might also find more info here: [http://ubuntuforums.org/showthread.php?t=494283](http://ubuntuforums.org/showthread.php?t=494283)

---

### Post by guywithcable on 2009-07-03
> **matt79 said:**
> try adding 

extension = php_http.dll
to your php.ini

you might have to restart.

You might also find more info here: [http://ubuntuforums.org/showthread.php?t=494283](http://ubuntuforums.org/showthread.php?t=494283)

DLL? But, I'm using Linux...

I've already added "extension=http.so" to my php.ini and restarted. It worked in my Desktop test machine, but not the server.

---

### Post by guywithcable on 2009-07-03
And I've already added the php5-curl package. That didn't help either. :(

---

### Post by matt79 on 2009-07-03
O sorry. That is all the ideas I have. But I guess you could try and copy the php.ini file from the test computer to the server. Again you might have to restart. ( I would make a backup copy of the one on the server first)

---

### Post by guywithcable on 2009-07-03
> **matt79 said:**
> O sorry. That is all the ideas I have. But I guess you could try and copy the php.ini file from the test computer to the server. Again you might have to restart. ( I would make a backup copy of the one on the server first)

That's a good idea. I'll try that and let you know if it works.

---

### Post by guywithcable on 2009-07-03
> **matt79 said:**
> O sorry. That is all the ideas I have. But I guess you could try and copy the php.ini file from the test computer to the server. Again you might have to restart. ( I would make a backup copy of the one on the server first)

YAY! IT WORKED! Thank you matt79, you rock! I have no idea what the problem was. :-k But, whatever. :D

---

### Post by guywithcable on 2009-07-03
I could literally kill myself right now...

```
hunter@mifos:/etc/php5/apache2$ diff -iwB php.ini php.ini.bak 
270c270
< memory_limit = 64M      ; Maximum amount of memory a script may consume (16MB)
---
> memory_limit = 32M      ; Maximum amount of memory a script may consume (16MB)
615c615
< extension=http.so
---
> axtension=http.so
```

---

