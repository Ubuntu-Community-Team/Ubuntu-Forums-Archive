---
title: "How to know if UFW deny by default"
date: 2009-08-19
forum: Security
---

### Post by jocampo on 2009-08-19
I think UFW denies by default unless you change it. I also reinforce it on my server using

```
sudo ufw default deny
```

After implementing some rules of my own, of course.

My question is, when I check active rules using

```
sudo ufw status
```

My active rules are listed, but Ubuntu does not say if "deny default" is there. Is this a normal behavior, do we have another command or flag which can list that?

Thanks in advance,

Jose.

---

### Post by Nepherte on 2009-08-19
> **jocampo said:**
> I think UFW denies by default unless you change it. I also reinforce it on my server using

```
sudo ufw default deny
```

Prior some rules of my own, of course.

If you first enter your rules and then issue a default deny, the rules you entered are removed.
> **jocampo said:**
> My question is, when I check active rules using

```
sudo ufw status
```

My active rules are listed, but Ubuntu does not say if "deny default" is there. Is this a normal behavior, do we have another command or flag which can list that?

Thanks in advance,

Jose.
It is normal behavior that ufw status doesn't list it, although it would clarify a lot if it did.

---

### Post by jocampo on 2009-08-19
> **Nepherte said:**
> 
It is normal behavior that ufw status doesn't list it, although it would clarify a lot if it did.

Thank you very much, that clarifies my question and is what I suspected. I appreciate your help.

> **Nepherte said:**
> If you first enter your rules and then issue a default deny, the rules you entered are removed.


Sorry, but not true. 

In fact, that's the safest way to do it. You specify what you want to be open or allowed 1st and at the end ... "default deny" and later, "ufw enable". Check this out, from my server

```
sudo ufw status

Status: active

To                         Action  From
--                         ------  ----
22                         ALLOW   Anywhere
80                         ALLOW   Anywhere

```

means, my rules are there, not removed ...

---

### Post by kevdog on 2009-08-19
If you just type iptables -L at the command line (this is what ufw works with anyway), you can see the current rule set with the default policies.

---

### Post by bodhi.zazen on 2009-08-19
+1

---

