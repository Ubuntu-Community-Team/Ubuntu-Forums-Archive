---
title: "Apache newbie"
date: 2007-01-23
forum: Server Platforms
---

### Post by crabhunter on 2007-01-23
Hi,
I have just installed Apache2 on ubuntu 6.10
It seems to be working because if I goto [http://localhost/](http://localhost/)
I get a message from the apache server saying index of /
My question is, where do I put my index.html file so it shows in my browser?
Thanks.
Mike

---

### Post by jtc on 2007-01-23
Asuming you've done a normal Ubuntu-install of apache2 your DocumentRoot would be /var/www/

That's where I belive you want to place your index-file.

---

### Post by crabhunter on 2007-01-23
OK I found that but i need root priviliges to paste any file in there,I'm rearly not into all this sudo copy file here consol stuff.How do you log in as root?I used to use suse and you could log in as root but ubuntu wont let me.
Mike

---

### Post by jtc on 2007-01-23
In Ubuntu, by default, you don't have a root account to log into. Besides, if you'r talking about logging into Gnome as root, that's definatly not something you want to do.

I'm gussing you'll be the only one having a webbpage in /var/www/? In that case I'd say the best thing to do would be to simply give your user ownership of that directory.

Run this line in the terminal.

```
sudo chown yourusername:yourgroup /var/www/
```

By default in Ubunut your group has the same name as your username.

---

### Post by crabhunter on 2007-01-23
Sorted,nice one mate.

---

