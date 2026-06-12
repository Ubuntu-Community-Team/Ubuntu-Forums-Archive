---
title: "URL lowercase vs UPPERCASE"
date: 2010-03-27
forum: Server Platforms
---

### Post by Bob_G7 on 2010-03-27
Is there a file I can edit so when I go to a local URL in firefox I don't have to use uppercase/lowercase to view the page.

Examples:

The way it is now:
[http://localhost/phpBB3](http://localhost/phpBB3)

What I'm hoping for:
[http://localhost/phpbb3](http://localhost/phpbb3) or [http://localhost/phpBB3](http://localhost/phpBB3)

Thanks in advance

---

### Post by CharlesA on 2010-03-27
You'd probably have to tweak something in apache, but I don't know what.

Does it really matter? I think you can set up redirect to point to /phpBB3 if someone types in /phpbb3.

---

### Post by Jekshadow on 2010-03-28
> **CharlesA said:**
> You'd probably have to tweak something in apache, but I don't know what.

Rename the PHPBB folder?

---

### Post by terazen on 2010-03-29
```
sudo a2enmod speling
```

---

### Post by Maheriano on 2010-03-29
Did you just misspell spelling? For real?

Just use mod-rewrite.

---

### Post by terazen on 2010-03-29
> **Maheriano said:**
> Did you just misspell spelling? For real?

No I didn't.

/etc/apache2/mods-available/speling.load

---

### Post by HermanAB on 2010-03-29
Mod speling is an Apachie joak, but iet werks as ekspekted!

---

