---
title: "list of installed programs"
date: 2012-01-05
forum: System76 Support
---

### Post by benj23673 on 2012-01-05
How can I see a list of programs I installed already on lubuntu?

---

### Post by Lars Noodén on 2012-01-05
You could look in Synaptic.  Or you could get the full list, including dependencies, like this:

```

dpkg --get-selections | awk '$2 = "install" { print $1 }'

```

I don't know of a good way to get just the programs you added to the base.

---

### Post by Rodney9 on 2012-01-05
I would like to know how to find what was originally installed in Lubuntu 11.10

Rodney

---

### Post by Lars Noodén on 2012-01-05
This might do it:

```

apt-cache --recurse depends lubuntu-desktop| awk '$1="Depends:" {print $2}'|sort -u|less

```

Or if you want just the top layer:

```

apt-cache depends lubuntu-desktop | grep "Depends:"

```

---

