---
title: "search for string and to end of file"
date: 2012-08-03
forum: Server Platforms
---

### Post by viddect on 2012-08-03
i am looking for a way to search for a string, in this case a date and then grab everything till the EOF and do some 2nd search for a specific string. I am working with conman and powerman logs.

any ideas would be helpful.

---

### Post by papibe on 2012-08-03
Hi viddect.

Take a look at the command 'grep'. It is very easy to use:
```
grep pattern file
```
Another alternative would be 'awk'.

Let us know how it goes.
Regards.

---

### Post by steeldriver on 2012-08-03
or even sed

```
sed '/*pattern*/,$!d' *file*
```it really all depends what you want to do with the matched text

---

