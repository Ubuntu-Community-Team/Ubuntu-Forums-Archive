---
title: "Apache - default image directory"
date: 2011-01-10
forum: Server Platforms
---

### Post by AlbuquerqueApache on 2011-01-10
IS the default image directory /var/www ? 

I have set up my index.html (within the same directory) to reference a .jpg within the same direcotry but it doesn't show. ;S 

I have <img src="picture.jpg" alt="" width="400" length="200" /> 

I'm kind of at a loss. 

When I pull up my webpage it doesnt show BUT if I navigate to [http://server/picture.jpg](http://server/picture.jpg) , it shows the picture! 

its probably my inexperience with apache.

---

### Post by sj1410 on 2011-01-10
theres nothing like a image directory

/var/www/ is the web root directory. it might be a permision problem try the following

```

sudo chmod www-data:www-data /var/www/picture.jpg


```

or also 

```

<img src="/picture.jpg" alt="" width="400" length="200" />

```

---

### Post by CharlesA on 2011-01-11
Also, remember that Linux is case sensitive. :)

Try adding it like this:
```
<img src="./picture.jpg" alt="picture" />
```

---

### Post by AlbuquerqueApache on 2011-01-11
I got it! 


I had <img source= /> not <img src= /> 

:oops:

Thanks anyway!

---

### Post by CharlesA on 2011-01-11
Mistakes happen, it's one of the ways you learn. :)

Don't forget to mark the thread as solved from thread tools.

---

