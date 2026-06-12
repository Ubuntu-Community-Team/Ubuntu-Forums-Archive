---
title: "Squirrelmail translation problem"
date: 2006-07-03
forum: Server Platforms
---

### Post by kson on 2006-07-03
I´m trying to view my webmail in swedish but the only thing that gets translated is the help page. I´ve added sv_SE as the default language in squirrelmail-configure and the settings page shows "svenska" as language but the rest is english. I tried to change to spanish but nothing changes except the help page.

I have no idea what to do.

Please help
/Martin

---

### Post by kson on 2006-07-15
Please help anyone?

---

### Post by compbrain on 2006-07-16
The squirrelmail documentation is probably the best resource:
[http://www.squirrelmail.org/wiki/LanguageTranslation](http://www.squirrelmail.org/wiki/LanguageTranslation)

---

### Post by kson on 2006-07-16
> **compbrain said:**
> The squirrelmail documentation is probably the best resource:
[http://www.squirrelmail.org/wiki/LanguageTranslation](http://www.squirrelmail.org/wiki/LanguageTranslation)

Thanks for the tip but I´ve checked that already and I couldn´t find anything useful. They talk about server issues but the help page is viewed in the right language but not the rest of the site. I wonder if it has something to do with utf?

---

### Post by kson on 2006-07-16
They talk about charsets here:
[http://www.squirrelmail.org/wiki/SupportedCharsets](http://www.squirrelmail.org/wiki/SupportedCharsets)
But I cant understand if they support utf or not. The setup.php for  sv_SE in squirrelmail looks like this: 
```

$languages['sv_SE']['NAME']    = 'Swedish';
$languages['sv_SE']['ALTNAME'] = 'Svenska';
$languages['sv_SE']['CHARSET'] = 'iso-8859-1';
$languages['sv_SE']['LOCALE']  = array('sv_SE.ISO8859-1','sv_SE.ISO-8859-1','sv_SE');
$languages['sv']['ALIAS'] = 'sv_SE';
```

But ubuntu have no locale called sv_SE.ISO-8859-1 just sv_SE.utf8 can that be the problem???

Is squirrelmail translations working for someone else?

---

### Post by kson on 2006-07-19
Can someone that uses squirrelmail from the dapperpackage check if their translations are working?

---

### Post by Yogarine on 2006-08-29
I have the same problem.

I installed squirrelmail and squirremail-locales, but changing the language, either in the default configuration or in the personal configuration doesn't help. All the text stays in English.

However... The help *does* show up in the localized language.

---

### Post by kson on 2006-08-29
> **Yogarine said:**
> I have the same problem.

I installed squirrelmail and squirremail-locales, but changing the language, either in the default configuration or in the personal configuration doesn't help. All the text stays in English.

However... The help *does* show up in the localized language.

At last someone with the same problem, good its not my setup thats wrong. I have no idea how to fix it :(

---

### Post by Yogarine on 2006-08-29
I solved it.

The problem is that Ubuntu only has the UTF-8 locales configured by default. You need to add the ISO-8859-1 locale for your language as well.

Just edit /var/lib/locales/supported.d/local and then add your local with the ISO-8859-1 codeset. Kson, for you it should look like this:

```
sv_SE.UTF-8 UTF-8
sv_SE.ISO-8859-1 ISO-8859-1
en_US.UTF-8 UTF-8
```

After that run 'sudo dpkg-reconfigure locales' to update the locales and all should work fine.

---

### Post by kson on 2006-08-29
YES! I worked! I knew it was something with the locales but I thought I had to install it someway. Never knew it was that easy.

Thanks alot!

---

### Post by Ansman on 2008-01-21
> **Yogarine said:**
> I solved it.

The problem is that Ubuntu only has the UTF-8 locales configured by default. You need to add the ISO-8859-1 locale for your language as well.

Just edit /var/lib/locales/supported.d/local and then add your local with the ISO-8859-1 codeset. Kson, for you it should look like this:

```
sv_SE.UTF-8 UTF-8
sv_SE.ISO-8859-1 ISO-8859-1
en_US.UTF-8 UTF-8
```

After that run 'sudo dpkg-reconfigure locales' to update the locales and all should work fine.
OMFG, i love you!
Been looking for hours before i saw your post =)

---

