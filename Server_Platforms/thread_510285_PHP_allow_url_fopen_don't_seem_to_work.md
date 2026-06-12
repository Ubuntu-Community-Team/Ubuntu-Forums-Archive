---
title: "PHP allow_url_fopen don't seem to work"
date: 2007-07-26
forum: Server Platforms
---

### Post by Erestar on 2007-07-26
Hello,
  I'm experiencing this issue on several ubuntu work stations and servers running PHP and Apache, both Dapper and Feisty 

The issue is that the URL wrappers for file, fopen, etc only work for sites that are being served by the same server that is making the call.

For instance, from a given server:

[PHP]
file("http://localhost");
[/PHP]

works fine, but

[PHP]
file("http://google.com");
[/PHP]

does not. If there's a PHP file at localhost it parses correctly, indicating that the file is being retrieved through apache and php over http.

Trying to hit an external website (and I've tried several) I receive:

> 
failed to open stream: HTTP request failed!


This doesn't seem to be a PHP issue and, if it is, it's something other than the allow_url_fopen setting. I've also tried spoofing the user agent and that doesn't work either.

Does anyone have a solution for this problem?

---

