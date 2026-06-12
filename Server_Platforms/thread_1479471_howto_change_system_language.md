---
title: "howto change system language?"
date: 2010-05-10
forum: Server Platforms
---

### Post by smo0th on 2010-05-10
Hi, I'm running a Lucid server, the system default language is english and I would like to add support for spanish and make spanish the default language, I installed the language pack by using ```
sudo apt-get install language-pack-es
``` but cannot find how to set the default language :(

---

### Post by arrrghhh on 2010-05-10
I believe it's just this:

```
Change default language for the console:

       1. Edit /home/USERNAME/.bash_profile
       2. Add the line export LANG=de (example given for German)
```

LANG=es in your case ;)

---

### Post by smo0th on 2010-05-10
ok good, I did the following:
```

export LANG=es_MX
export LANGUAGE=es_MX
sudo dpkg-reconfigure locales
echo "export LANG=es_MX" >> /home/user/.profile

```

So far it looks like it worked, thanks for the help! :)

---

### Post by arrrghhh on 2010-05-10
Nvm, *insert foot-in-mouth now*

Glad I could help!

---

