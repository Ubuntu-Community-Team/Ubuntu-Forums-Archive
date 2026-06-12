---
title: "MX Records for Mailserver"
date: 2011-11-01
forum: Server Platforms
---

### Post by systemrooterrr on 2011-11-01
Alright, I've been setting up a mailserver (following the ubuntu community postfix guide) and have hit a snag. MX Records.

I understand what they do and I think I have them setup alright on my domain, but doing a sudo dig mx littletechboy.com doesn't show anything past the query. dig mx ltbcomputersolutions.com (the other domain I own and use thier mailservers) works perfectly fine and resolves two of their servers. 

Is there something server side I have to do to get it to work?

In the DNS records, I have ```

A record zone
@                           *my external IP
mail.littletechboy.com      *my external IP

```
Then there is the MX record zone
```

0        *my external IP     mail.littletechboy.com
10       *my external IP     mail.littletechboy.com

```

What am I missing? (I've also waited 48 hours for DNS to update)
Thanks!

---

### Post by SeijiSensei on 2011-11-01
> **systemrooterrr said:**
> Then there is the MX record zone
```

0        *my external IP     mail.littletechboy.com
10       *my external IP     mail.littletechboy.com

```

I don't know what guides you're reading, but that's not the correct syntax for an MX record.  Use this:

```

@       IN   SOA littletechboy.com me.littletechboy.com { 
             stuff
             }

        IN   MX   0 mail.littletechboy.com.

mail    IN   A    ip.of.mail.server


```

---

