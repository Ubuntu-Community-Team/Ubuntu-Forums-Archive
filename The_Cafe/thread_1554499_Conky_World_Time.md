---
title: "Conky World Time"
date: 2010-08-16
forum: The Cafe
---

### Post by mpierce on 2010-08-16
I've searched and haven't found what I'm looking for.
Is there a conky script that has been written that can display 2-4 world timezones?

---

### Post by rollin on 2010-08-17
You could just use the "tztime" command. Eg:

```
${tztime America/New_York  %H:%M}
```

For an inventory of names check here [http://en.wikipedia.org/wiki/List_of_zoneinfo_timezones](http://en.wikipedia.org/wiki/List_of_zoneinfo_timezones)

---

### Post by mpierce on 2010-08-18
Thank you...
That's the trick!

---

### Post by rollin on 2010-08-18
Your most welcome ;)

---

