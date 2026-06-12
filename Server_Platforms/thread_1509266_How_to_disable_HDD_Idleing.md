---
title: "How to disable HDD Idleing?"
date: 2010-06-14
forum: Server Platforms
---

### Post by sikander3786 on 2010-06-14
Hi buddies.

I have samba server running on Ubuntu Lucid Desktop. It has two HDDs. I want that system up and running 24 X 7 but at night if there are no users, the 2nd HDD goes into idle mode and it doesn't come up without restart.

Ubuntu's Power Management Console has no options to configure HDD Idle Mode.

How to disable disk idle?

Please help.

Regards.

---

### Post by sikander3786 on 2010-06-14
Is this the correct command to disable HDD standby?

```

sudo hdparm -S 0 /dev/sda

```

---

### Post by sikander3786 on 2010-06-25
Bump...

And solved by myself. LOL

The above mentioned command works.

---

### Post by koenn on 2010-06-25
> **sikander3786 said:**
> Is this the correct command to disable HDD standby?

```

sudo hdparm -S 0 /dev/sda

```
I've seen reports that it works. 

:)

---

### Post by sikander3786 on 2010-06-26
> **koenn said:**
> I've seen reports that it works. 

:)

You might have seen reports but nobody confirmed me that it works before I myself tried it and had to wait 12 hours to check out the results.

Anyhow thanks for reconfirmation.

---

