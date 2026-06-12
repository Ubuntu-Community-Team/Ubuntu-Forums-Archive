---
title: "Nixnote 1.3 dependency not satisfiable libssl(&gt;=0.9.8)"
date: 2012-09-13
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by donniezazen on 2012-09-13
Hello,

I am unable to properly install Nixnote 1.3. It says dependency not satisfiable libssl(>=0.9.8). I have both libssl0.9.8 and libssl1.0.0 installed. I have tried creating a link suggested on [AskUbuntu](http://askubuntu.com/questions/77256/i-want-to-install-libssl-0-9-8) as below. Any help would be appreciated.

```
sudo ln -s /usr/lib/x86_64-linux-gnu/libssl.so**.1.0.0** /usr/lib/libssl.so.0.9.8
```

Thanks.

---

### Post by mc4man on 2012-09-13
maybe post a query here
[http://sourceforge.net/apps/phpbb/nevernote/index.php](http://sourceforge.net/apps/phpbb/nevernote/index.php)

should note that the actual package name is [COLOR="Blue"]libssl0.9.8[/COLOR], not libssl so likely the control file of the .deb is wrong

Depends: openjdk-6-jre | clipped, [COLOR="Red"]libssl[/COLOR] (>=0.9.8)

should be 
Depends: openjdk-6-jre | clipped, libssl0.9.8 (>=0.9.8)

---

### Post by donniezazen on 2012-09-13
> **mc4man said:**
> maybe post a query here
[http://sourceforge.net/apps/phpbb/nevernote/index.php](http://sourceforge.net/apps/phpbb/nevernote/index.php)

should note that the actual package name is [COLOR="Blue"]libssl0.9.8[/COLOR], not libssl so likely the control file of the .deb is wrong

Depends: openjdk-6-jre | clipped, [COLOR="Red"]libssl[/COLOR] (>=0.9.8)

should be 
Depends: openjdk-6-jre | clipped, libssl0.9.8 (>=0.9.8)

That might be a problem I have Oracle Java 7 installed.

---

### Post by mc4man on 2012-09-13
I see you may be a bit confused, look at screen - the .deb has a dependency of a non existent package "libssl", that's why the install fails

---

### Post by donniezazen on 2012-09-13
Thanks mc4man. Got it solved.

[https://sourceforge.net/apps/phpbb/nevernote/viewtopic.php?f=3&t=270&p=1111#p1111](https://sourceforge.net/apps/phpbb/nevernote/viewtopic.php?f=3&t=270&p=1111#p1111)

---

