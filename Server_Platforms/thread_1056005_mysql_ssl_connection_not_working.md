---
title: "mysql ssl connection not working"
date: 2009-01-31
forum: Server Platforms
---

### Post by LonelyStar on 2009-01-31
Hi,

I have installed mysql on my server and want to secure it for access over the intern.

I added the ssl-cert and ssl-key options to my.cnf.

Now I connect from within the server:
```

mysql -u username -p --ssl-cipher=DHE-RSA-AES256-SHA --host=myhost.com

```
Now, typing \s;, I get:
```

SSL:			Cipher in use is DHE-RSA-AES256-SHA

```
Great! If I do not provide the -ssl-cipher parameter but only the --ssl parameter, ssl is not enabled, strange but ok.

The problem: from a remote host (my desktop pc) with exactly the same paramters, it does not work. SSL is not enabled.

Every howto/tutorial I find about this tells me to provide the --ssl-ca parameter. But I want to access the database from everywhere and not always copy the ca file.

What could be wrong, what can I do?

Thanks!
Nathan

---

