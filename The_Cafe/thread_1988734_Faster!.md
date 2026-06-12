---
title: "Faster!"
date: 2012-05-28
forum: The Cafe
---

### Post by vasa1 on 2012-05-28
Any tips on speeding up page loading/navigation in your favorite browser? If possible, please provide the context and source ...

I came across this:
```

Scrolling on website xyz is very slow

    Go to Tools > Extensions
    Enable 'User Addons' if it's not yet enabled
    Create a text file .local/share/midori/styles/scrollfix.user.css
    Put this into the file: * {-webkit-box-shadow: none !important;}

```
Source: [http://wiki.xfce.org/midori/faq](http://wiki.xfce.org/midori/faq)

For gecko, just drop the "-webkit-".

---

