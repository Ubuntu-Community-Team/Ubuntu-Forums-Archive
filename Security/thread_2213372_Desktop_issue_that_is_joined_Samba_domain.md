---
title: "Desktop issue that is joined Samba domain"
date: 2014-03-26
forum: Security
---

### Post by TheHesser on 2014-03-26
Earlier I posted a message about adding a Linux desktop to a Samba domain.
Now I have logged in and another person after me and there is a list building up of people who have logged in.

Is there a way to delete that list or keep it short? 
How long will this list me because I have 30 colleagues and I don't want anyone from the outside have a list of people that they can try and hack or try to fish for passwords.

Blessings,
Hendrik

---

### Post by ant2ne on 2014-03-26
And what is the path and name of this list?

---

### Post by lingpanda on 2014-03-26
I believe its with the following command.

```
sudo /usr/lib/lightdm/lightdm-set-defaults --hide-users true
```

---

