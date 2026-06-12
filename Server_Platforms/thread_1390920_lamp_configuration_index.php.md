---
title: "lamp configuration index.php"
date: 2010-01-26
forum: Server Platforms
---

### Post by howlingmadhowie on 2010-01-26
hi everybody. following problem.

when i direct my browser to [http://localhost](http://localhost), apache delivers /documentroot/index.php, but when i go to http://<my ip address> i have to explicitly call index.php, otherwise apache doesn't find it.

it's probably a simple configuration setting somewhere...

anyone know the answer? :D

---

### Post by cdenley on 2010-01-26
> **howlingmadhowie said:**
> hi everybody. following problem.

when i direct my browser to [http://localhost](http://localhost), apache delivers /documentroot/index.php, but when i go to http://<my ip address> i have to explicitly call index.php, otherwise apache doesn't find it.

it's probably a simple configuration setting somewhere...

anyone know the answer? :D

Are you sure it's not your browser cache?
```

echo "GET / HTTP/1.0\n"|nc 127.0.0.1 80

```

The DirectoryIndex option is defined globally, so unless you have a vhost configuration besides the default defined for localhost, then override this option of the default vhost, I don't think this would happen.

---

### Post by howlingmadhowie on 2010-01-26
> **cdenley said:**
> Are you sure it's not your browser cache?
```

echo "GET / HTTP/1.0\n"|nc 127.0.0.1 80

```

The DirectoryIndex option is defined globally, so unless you have a vhost configuration besides the default defined for localhost, then override this option of the default vhost, I don't think this would happen.

thanks, it was my browser cache :D sometimes i do feel rather dense ...

---

