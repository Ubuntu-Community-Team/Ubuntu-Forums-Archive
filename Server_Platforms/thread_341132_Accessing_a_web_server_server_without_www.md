---
title: "Accessing a web server server without www"
date: 2007-01-18
forum: Server Platforms
---

### Post by NetworkGuy on 2007-01-18
Hi All,

I've been requested to add a line to our BIND server to allow people to hit it from a web browser without using www. in front of the domain name.   (i.e.  foo.net instead of [www.foo.net](www.foo.net))  

I've searched google but must be looking for the wring search phrase.  Can anyone lead me in the right direction?   

Thanks.

---

### Post by jtc on 2007-01-18
```

@               In      A       1.2.3.4

```

---

### Post by NetworkGuy on 2007-01-18
jtc,

Thanks.   This is a big help.  I was looking all day yesterday and couldn't find this.

---

### Post by NetworkGuy on 2007-01-18
jtc,

Thanks.   This is a big help.  I was looking all day yesterday and couldn't find this.

---

