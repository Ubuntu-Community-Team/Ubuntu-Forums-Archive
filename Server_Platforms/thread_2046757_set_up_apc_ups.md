---
title: "set up apc ups"
date: 2012-08-23
forum: Server Platforms
---

### Post by jocatoth on 2012-08-23
i could use a little help.  i purchased an APC UPS. i want to get this set up to run on a 8.04.03 headless back up / print server. i am not clear on how to add the apcupsd, apcupsd-cgi and apcupsd-doc files. i would imagine that i use wget but the specifying of the apcupsd package(s) is not clear to me using the command line.

thanks for the help.

---

### Post by koenn on 2012-08-23
```
sudo apt-get install apcupsd apcupsd-cgi apcupsd-doc

```

---

### Post by rubylaser on 2012-08-24
Here's how I set mine up. [http://zackreed.me/articles/40-ups-protect-your-files]("http://zackreed.me/articles/40-ups-protect-your-files")

---

### Post by CharlesA on 2012-08-24
> **rubylaser said:**
> Here's how I set mine up. [http://zackreed.me/articles/40-ups-protect-your-files]("http://zackreed.me/articles/40-ups-protect-your-files")
That is the same setup I have minus Munin.

---

### Post by rubylaser on 2012-08-24
> **CharlesA said:**
> That is the same setup I have minus Munin.

Munin is a nice addition to the whole home server setup.

---

### Post by CharlesA on 2012-08-24
Googled it. Looks pretty handy. :)

---

### Post by jocatoth on 2012-08-24
thanks for the help, this is exactly what i needed. you all saved me several hours of trial and error.

---

