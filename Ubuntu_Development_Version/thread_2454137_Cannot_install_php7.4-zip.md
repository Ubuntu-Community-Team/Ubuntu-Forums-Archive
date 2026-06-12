---
title: "Cannot install php7.4-zip"
date: 2020-11-23
forum: Ubuntu Development Version
---

### Post by deneme100 on 2020-11-23
Hello




I cant install php7.4-zip on ubuntu 21.04, but php & apache is working.


I saw , package is in the web site : [https://packages.ubuntu.com/hirsute/php-zip](https://packages.ubuntu.com/hirsute/php-zip)


Error message : The php7.4-zip package does not exist, but is pointed in another package.

---

### Post by dino99 on 2020-11-23
Why do you want installing a ziped package ?
Either install the gui 'synaptic' , then select 'php7.4' for installation; or do it via a terminal: 'sudo apt-get install php7.4'

---

### Post by deneme100 on 2020-11-23
Hi
I need install zip extension (Zip module for PHP) ,not php main package (it installed), i cant see zip extension package in synaptic.

php need zip extension  : Fatal error: Uncaught Error: Class 'ZipArchive' not found

---

### Post by deadflowr on 2020-11-23
Posts moved to their own thread.

php7.4-zip is in the universe repository.
Make sure that is enabled.

---

### Post by deneme100 on 2020-11-23
> **deadflowr said:**
> Posts moved to their own thread.

php7.4-zip is in the universe repository.
Make sure that is enabled.

Thank you,its ok

---

### Post by deadflowr on 2020-11-23
> **deneme100 said:**
> Thank you,its ok

What's ok?

---

### Post by deneme100 on 2020-11-23
> **deadflowr said:**
> What's ok?

```
sudo add-apt-repository universe
```

and i can see zip extension package (php).

Thanks

---

