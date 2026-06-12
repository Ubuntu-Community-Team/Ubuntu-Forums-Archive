---
title: "Apache"
date: 2009-03-05
forum: Server Platforms
---

### Post by vidgpersonrsw on 2009-03-05
On my website the URL is always the same as the first page visited.

For ex: Let's say I go to [www.example.com/test](www.example.com/test)
no matter where i navigate throughout the site the URL bar will ALWAYS say [www.example.com/test](www.example.com/test)

Anyway I can change this?

---

### Post by LegendofTom on 2009-03-06
Probably need to tell apache where to direct you first. I think this is in one of the apache config files.

---

### Post by vidgpersonrsw on 2009-03-06
I am new server admin, so I don't really understand what you mean by "direct me first."

---

### Post by drubin on 2009-03-06
> **vidgpersonrsw said:**
> On my website the URL is always the same as the first page visited.

For ex: Let's say I go to [www.example.com/test](www.example.com/test)
no matter where i navigate throughout the site the URL bar will ALWAYS say [www.example.com/test](www.example.com/test)

Anyway I can change this?

This doesn't seem like an Apache config issue but more of a html issue.

Are you sure your site has the <title> tags in the <head> 

ie 
[HTML]<html>
<head>
<title>This will change the title</title>
</head>
<body>Testing</body>
</html>[/HTML]

---

### Post by vidgpersonrsw on 2009-03-06
I have multiple sites on the server (wordpress blog, wiki, etc.) and they all do the same thing. I am not sure I made myself clear enough. The thing in the title bar changes fine but the URL ([www.whatever.com](www.whatever.com)) in the ADDRESS BAR doesn't change.

It would be like typing in ubuntuforums.org, and no matter where you navigated to on the site it would still have ubuntuforums.org

---

### Post by drubin on 2009-03-07
Does this only happen with websites on your server? Or does it happen with all websites.

I think this might be a web browser thing What browser are you using?

---

### Post by vidgpersonrsw on 2009-03-07
> **drubin said:**
> Does this only happen with websites on your server? Or does it happen with all websites.

I think this might be a web browser thing What browser are you using?

It's a server thing, trust me. My server is the only one that it does it with.

---

### Post by mrsteveman1 on 2009-03-07
Are there any errors in the logs? They are in /var/log/apache2 usually

---

### Post by drubin on 2009-03-08
> **vidgpersonrsw said:**
> It's a server thing, trust me. My server is the only one that it does it with.

Sorry but this is very hard to believe it is a server thing. Since the problem you are experiencing is a client side issue.

Just from that statement I noticed you saying it is only my server but this might not be the case it might also be the code that sits on your server.

Could you at least post your vhost site config and possibly your apache config.

---

