---
title: "passwordless ssh login"
date: 2008-08-27
forum: Server Platforms
---

### Post by etechship on 2008-08-27
I used this page:
[http://kerneltrap.org/node/8178](http://kerneltrap.org/node/8178)

I have two servers, one considered local and the other remote. I have follow the above directions, but when I execute the ssh command, it still asks me for a password. When I change the permissions for the key on the local machine to, say 777, it throws an error, and then it asks for a password. I have played around with different permissions for that file, and I have not gotten anything to work so far. The permission is set at 777 for the .pub file in the .ssh/auth* in the remote server. The remote server is a Hostgator web hosting account (so I don't have root on it).

thanks
dave

---

### Post by jerome1232 on 2008-08-27
That's probably why, loose permisions will make it not use the pubkey, on my server I had to chmod the public key as 700, known_hosts as 600, and the home directory of my user as 700.

Hope that helps.

edit: I was actually a bit off on the permissions my last post is correct

---

### Post by etechship on 2008-08-27
What do you mean by known_hosts? Where would I set that?

thanks
dave

---

### Post by jerome1232 on 2008-08-27
That one probably won't be present unless the server has ssh'd out to another computer and I don't believe it matters.

Did that not work for you then?

I'm assuming you placed the public key in ~/.ssh/authorized_keys on the server correct? I guess I should check that guide you linked out to see what you have done.

edit: That all looks correct to sum it up

we have desktop, and server
on desktop you generated a key as outlined on that guide
you copied the public key over to the server and placed it in the file ~/.ssh/authorized_keys

on the server
chmoded ~/.ssh/authorized_keys as 600
chmoded ~/.ssh as 700
and if both of those don't fix it chmod ~/ as 700

---

### Post by Dr Small on 2008-08-27
Have you read this?
[http://php.8ez.com/drsmall/blog/?p=218](http://php.8ez.com/drsmall/blog/?p=218)

---

### Post by etechship on 2008-08-28
When I type:
ssh-copy-id -i ~/.ssh/id_dsa.pub -p 2222 *username*@*server*

It throws this error:
/usr/bin/ssh-copy-id: ERROR: No identities found


thanks
dave

---

### Post by jerome1232 on 2008-08-28
```
cat ~/.ssh/id_dsa.pub | ssh username@server -p 2222 "cat >>.ssh/authorized_keys"
```

---

