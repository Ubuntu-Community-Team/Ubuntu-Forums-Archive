---
title: "apache issue"
date: 2009-08-11
forum: Server Platforms
---

### Post by Soley on 2009-08-11
So I'm having an issue with my apache server. I had it working exactly how I wanted it. Now, for some reason whenever I enter either my IP, it appends ":8080" to it. So, for example, if I enter:
```
192.168.1.4
```

then I hit enter, what comes up is:

```
192.168.1.4:8080
```

However when I type in "localhost", it asks if I want to save a .bin file. 

Any ideas?

Also I just opened said .bin file & the only thing in it was the "@" character without the quotations.

---

### Post by Soley on 2009-08-11
Ok, so I'm thinking that it isn't apache. I just ran sudo aptitude remove apache, then tried entering the IP and it's still doing it.

I'm really confused & out of ideas now.

---

### Post by R.Bucky on 2009-08-11
there is another service operating on port 8080 that is fairly common - can't think of it though... anyone else.

---

