---
title: "Date Bug in Conky???"
date: 2008-12-30
forum: The Cafe
---

### Post by Bungo Pony on 2008-12-30
Is anybody else's Conky showing a date of December 30, 2009?

---

### Post by yabbadabbadont on 2008-12-30
It's a feature...  ;)

It's displaying the state your machine *will have* on that date.  :D

Edit: Nice wallpaper by the way.

---

### Post by WiFi Ed on 2008-12-30
> **Bungo Pony said:**
> Is anybody else's Conky showing a date of December 30, 2009?

It's the year variable in your script. Use %Y instead of %G.

See this page for more info on time/date variables:
[http://us2.php.net/strftime]("http://us2.php.net/strftime")

---

### Post by Bungo Pony on 2008-12-31
> Use %Y instead of %G.

That fixed it. Thanks for the tip :)

---

