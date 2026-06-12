---
title: "screen - Cannot open your terminal '/dev/pts/6' - please check"
date: 2013-04-25
forum: Server Platforms
---

### Post by Lars Noodén on 2013-04-25
I'm checking multiuser mode in screen and getting an error when I try to connect with the second user:  

*Cannot open your terminal '/dev/pts/6' - please check*

screen is SUID.  /var/run/screen is 755

The first user's .screenrc contains these lines:
```

multiuser on
acladd *user2*

```

I start the screen session for user1:

```

screen -S test

```

and then from user2, I try to connect:
```

screen -x user1/test

```

And that's where the error occurs.  Multiple sites around the web show that to be the method to run screen with more than one user. e.g. [http://www.noah.org/wiki/Screen_notes#Multiuser_sessions_--_shared_screens](http://www.noah.org/wiki/Screen_notes#Multiuser_sessions_--_shared_screens)

I could have sworn this used to work in Ubuntu before.  What's missing?

---

### Post by SlugSlug on 2013-05-01
Not sure it's the same as my issue Lars, but I have to run
```
 script /dev/null
```

before I can resume the screen

---

