---
title: "Mysql &amp; PHP"
date: 2009-10-16
forum: Server Platforms
---

### Post by terazen on 2009-10-16
I am testing a helpdesk site using IRM for our maintenance department and have a problem that's probably easy but I don't work well when frustrated. :P

I get this this in mysql when I run "select contents from tracking where ID=20":
```
Building: Library
Room: 123
Detail of Work: 456
```

However when I view the page in IRM it looks like this:
```
Building: Library Room: 123 Detail of Work: 456
```

The line that puts the contents in the webpage is this:
```
fckeditor("workrequest",$this->WorkRequest);
```

How can I get the different fields to show up on different lines in the webpage the way they do in the mysql database?

---

### Post by ad_267 on 2009-10-16
A web page ignores newlines. You need to add a <br /> to add a new line in html. So you will need to replace all "\n"s with <br />.

Edit: Alternatively, just put it all inside <pre></pre> tags, which will keep the whitespace. [http://www.w3schools.com/tags/tag_pre.asp](http://www.w3schools.com/tags/tag_pre.asp)

---

