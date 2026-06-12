---
title: "Converting all my del.icio.us bookmarks to private"
date: 2006-04-30
forum: The Cafe
---

### Post by hanzj on 2006-04-30
2 questions:

1. Is there a quick way to convert all by del.icio.us bookmarks to private? 


2. I have a "Post to del.icio.us" bookmarklet (javascript button) on my browser. Can we modify that bookmarklet in such a way that clicking on it would automatically have the "Save as Private" checkbox checked?

---

### Post by hanzj on 2006-05-03
So I got a bit of help with Question Number 2.

The official javascript command from delicious is 
```
javascript:location.href='http://del.icio.us/post?v=4;url='+encodeURIComponent(location.href)+';title='+encodeURIComponent(document.title)
```

This is what he said:
I don't know javascript enough, so I can't give you the complete fix, 
but if you add " ;private='true' " (without the double quotes, but with 
the simple ones...) to the post URL, it works.
Example:
- clicking the "post" bookmarklet on the Google page will take you to 
the following URL: 
http://del.icio.us/siband.info?url=http%3A%2F%2Fwww.google.com%2F;title=Google;v=4

- add " ;private='true' " to it: 
http://del.icio.us/siband.info?url=http%3A%2F%2Fwww.google.com%2F;title=Google;v=4;private='true'
- voilà!

Now, as I said, I don't know javascript enough to escape the quotes in 
the bookmarklet, so I couldn't get it to work.
Someone can probably help here.


I've tried with \' or two quotes (''), but it didn't work:
```
javascript:location.href='http://del.icio.us/post?v=4;private=\'true\';url='+encodeURIComponent(location.href)+';title='+encodeURIComponent(document.title)

```
CODE]javascript:location.href='http://del.icio.us/post?v=4;private=''true'';url='+encodeURIComponent(location.href)+';title='+encodeURIComponent(document.title)[/CODE]

--------

I don't understand what was said, but if you have some insight, please feel free to share.

---

