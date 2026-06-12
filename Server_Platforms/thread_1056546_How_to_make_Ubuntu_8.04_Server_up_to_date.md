---
title: "How to make Ubuntu 8.04 Server up to date"
date: 2009-01-31
forum: Server Platforms
---

### Post by HolyJoe on 2009-01-31
I had a Ubuntu 8.04 Server it works well, but how to update it, such as patching security packages. My Ubuntu Server had installed gdm.

thanks.

---

### Post by unixeducation on 2009-01-31
From a shell prompt:

```

sudo apt-update
sudo apt-get upgrade --show-upgraded

```

Of course, if you want to upgrade the distribution, you update your sources in /etc/apt/sources.list to reflect the new version, and then:

```

sudo apt-get update
sudo apt-get dist-upgrade

```

---

### Post by HolyJoe on 2009-01-31
> **unixeducation said:**
> From a shell prompt:

```

sudo apt-update
sudo apt-get upgrade --show-upgraded

```

Of course, if you want to upgrade the distribution, you update your sources in /etc/apt/sources.list to reflect the new version, and then:

```

sudo apt-get update
sudo apt-get dist-upgrade

```

Yeah,That's great!

Thank you for your help.

---

