---
title: "Privoxy dropped from USC?"
date: 2012-04-23
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by vasa1 on 2012-04-23
Is it correct that Privoxy is not being offered via the Ubuntu Software Center?

---

### Post by sanderj on 2012-04-23
> **vasa1 said:**
> Is it correct that Privoxy is not being offered via the Ubuntu Software Center?

Which Ubuntu version? On my Ubuntu 11.10, Ubuntu Software Center does show privoxy ...

---

### Post by vasa1 on 2012-04-23
> **sanderj said:**
> Which Ubuntu version? On my Ubuntu 11.10, Ubuntu Software Center does show privoxy ...

I'm sorry for not being clear. With _12.04_.

Even more sorry! I see it now!

---

### Post by sanderj on 2012-04-23
> **vasa1 said:**
> I'm sorry for not being clear. With _12.04_.

Well, privoxy is listed for 12.04: [http://packages.ubuntu.com/precise/privoxy](http://packages.ubuntu.com/precise/privoxy)

It's part of 'universe', so have you enabled that? Check with 

```
grep -i universe /etc/apt/*

```

And what is the result of:

```
sudo apt-get install privoxy

```

---

