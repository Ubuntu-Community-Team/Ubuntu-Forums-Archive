---
title: "Can't use mysqli() with php5"
date: 2011-04-10
forum: Server Platforms
---

### Post by barisurum on 2011-04-10
Hello;

When try to do a database query with php5 and mysql. I encounter this error:

```
Fatal error: Call to undefined function mysqli()
```

while phpinfo() says mysqli support is enabled? What's wrong in this picture?

---

### Post by barisurum on 2011-04-10
So... The stupid book I'm learning php/mysql with, erroneously wrote mysqli() as it is a function! But its not, its a class! And I had to crawl tons of webpages to understand it. 

The result: Solved it with adding a "new" to the line that instantiates a mysqli **object**.

---

