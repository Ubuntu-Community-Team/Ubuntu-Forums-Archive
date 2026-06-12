---
title: "how to grab users list in ubuntu??"
date: 2006-07-24
forum: Server Platforms
---

### Post by ragdemai on 2006-07-24
as title.

Thnakx

---

### Post by simonn on 2006-07-25
```

$ cat /etc/passwd | cut -f 1 -d ":" -

```

Would be one way.

---

### Post by ragdemai on 2006-07-25
> **simonn said:**
> ```

$ cat /etc/passwd | cut -f 1 -d ":" -

```

Would be one way.

Thankx simonn

It work well,but is that any command can call out only user with user group.

---

### Post by simonn on 2006-07-25
There are probably better ways, but off the top of my head...

Replace [group] with the group you want to list members of.

```

cat /etc/group | sed 's/\(.*\):.*:.*:\(.*\)/\1 \2/' | awk '{if($1 == "[group]") print $2}'

```

---

### Post by fnjordy on 2006-07-25
Using getent over cat would be an improvement as it would pull in users and groups from NIS and LDAP as per nsswitch.conf

```

$ getent passwd *| ...*
$ getent group *| ...*

```

---

### Post by simonn on 2006-07-25
Hey, you learn something new every day - cheers fnjordy.

Try:

```

getent group [group] | cut -f 4 -d ":" -

```

---

### Post by ragdemai on 2006-07-25
> **simonn said:**
> Hey, you learn something new every day - cheers fnjordy.

Try:

```

getent group [group] | cut -f 4 -d ":" -

```

sorry i know what heppen on ubuntu i tried the command as you teach me but it came out blank line.

---

### Post by lamego on 2006-07-25
ragdemai,
the command that you are trying lists the users from a given group.
You are expected to replace [group] with the group name you want to list.

---

