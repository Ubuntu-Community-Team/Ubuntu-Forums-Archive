---
title: "PHP5 json - off by default"
date: 2007-05-10
forum: Server Platforms
---

### Post by xur17 on 2007-05-10
I am running a server with php5, apache2, fiesty, etc.  I installed celerondude's uploader php script, and I am running into a problem where the script automatically loads json, but it should do it this way:

```
The problem is because your applicaition is including the 'json' module like this:
dl('json.so')

Due to performance and user demands shortly after launch, that module is now integrated into php.

Your application should really do:

if(! @extension_loaded('json')) { dl('json.so'); }

That fragment checks to see if the module's already loaded, and only loads it if it's not.

I see that the code is encoded there though, so if it's third party software you'll have to contact them.
```

Since the script is encoded, is there some way to turn off the loading of json by default?

Thanks!

(If you need part of this clarified, please tell me).

---

