---
title: "Apache2: autoindexed auth dirs invisible"
date: 2006-10-25
forum: Server Platforms
---

### Post by warci on 2006-10-25
Hello everyone.
I have noticed something strange: i have a directory tree (thanks to auto-indexing) with some dirs that are only accessible trough basic authentication and some have no authentication enabled.
In apache 1.3 you would be able to see all the directories, and when you clicked one wich had security enabled you'd be prompted for a username/pass.
Now in apache 2.0 i can't see the dirs with security on them! The other directories are visible. When i type in the complete url, i do get prompted for a username/pass though ](*,) .
What's going on?

---

### Post by -J- on 2006-10-25
Check out [http://httpd.apache.org/docs/2.2/mod/mod_autoindex.html](http://httpd.apache.org/docs/2.2/mod/mod_autoindex.html)

Specifically the index option:
ShowForbidden
    If specified, Apache will show files normally hidden because the subrequest returned HTTP_UNAUTHORIZED or HTTP_FORBIDDEN

---

### Post by warci on 2006-11-02
thanks, this is exacly what i was looking for... can't believe i missed this in the docs](*,)

---

### Post by twigboy on 2006-11-02
Where do you add the IndexOption ShowForbidden?

---

