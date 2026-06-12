---
title: "Flushing the DNS"
date: 2010-05-26
forum: Security
---

### Post by elidoperezmd on 2010-05-26
hi all...

Im trying to flush the dns, after doing some reading online im entering:

sudo `/etc/init.d/nscd restart`

and the terminal responds: 

bash: /etc/init.d/nscd: No such file or directory

what am i doing wrong?

thanks for the help, im using linx

---

### Post by CharlesA on 2010-05-26
Linux doesn't cache dns names by default.

You would need to install nscd.

Why do you need to flush the dns?

More info [here]("http://www.pctipsbox.com/howto-clearflush-dns-cache-in-ubuntu/").

---

### Post by elidoperezmd on 2010-05-26
tryning to keep some privacy, you can never be to carefull

---

### Post by CharlesA on 2010-05-26
So flushing the dns cache (which Ubuntu doesn't use by default) will allow you more "privacy" ?

Hrm, ok.

---

### Post by elidoperezmd on 2010-05-26
> **CharlesA said:**
> So flushing the dns cache (which Ubuntu doesn't use by default) will allow you more "privacy" ?

Hrm, ok.

[http://lifehacker.com/5395267/how-to-really-browse-without-leaving-a-trace](http://lifehacker.com/5395267/how-to-really-browse-without-leaving-a-trace)

if im mistaken please give me some advice

---

### Post by CharlesA on 2010-05-26
Caching DNS resolutions is mostly a Windows thing. Ubuntu can do it, but you would need to install the nscd daemon (it is not installed by default) or be running your own DNS server.

If you are really worried about it just restart networking:

```
sudo /etc/init.d/networking restart
```

---

### Post by elidoperezmd on 2010-05-26
> **CharlesA said:**
> Caching DNS resolutions is mostly a Windows thing. Ubuntu can do it, but you would need to install the nscd daemon (it is not installed by default) or be running your own DNS server.

If you are really worried about it just restart networking:

```
sudo /etc/init.d/networking restart
```

will that do the trick?

---

### Post by CharlesA on 2010-05-26
There is no cache to clear, all that does it just restart the networking service.

---

### Post by elidoperezmd on 2010-05-27
> **CharlesA said:**
> Caching DNS resolutions is mostly a Windows thing. Ubuntu can do it, but you would need to install the nscd daemon (it is not installed by default) or be running your own DNS server.

If you are really worried about it just restart networking:

```
sudo /etc/init.d/networking restart
```

any ways to make this command run on its own from time to time???

---

### Post by CharlesA on 2010-05-27
You could stick it in a cronjob.

---

