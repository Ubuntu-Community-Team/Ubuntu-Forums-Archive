---
title: "PHP5/Apache - 500 internal server error"
date: 2012-03-07
forum: Server Platforms
---

### Post by H3110 on 2012-03-07
Hey All,

I have noticed this problem accross the web however I am not satisfied with the solution, essentially the solution is to edit the apache config and add the following:

```
php_flag display_errors On
```

However, on production servers errors SHOULDN'T be thrown, but in the unlikely event thus is the case, I DO NOT want to display any errors, but I also do not want a 500 page thrown, instead a blank white screen would suffice.

Anyone have a better solution for such environment?

Thanks.

---

### Post by nothingspecial on 2012-03-08
*Thread moved to **Server Platforms**.*

---

