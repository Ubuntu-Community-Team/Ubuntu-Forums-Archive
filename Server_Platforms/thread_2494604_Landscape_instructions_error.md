---
title: "Landscape instructions error"
date: 2024-01-21
forum: Server Platforms
---

### Post by b3nw on 2024-01-21
Not sure where to post this, but on [https://ubuntu.com/landscape/install](https://ubuntu.com/landscape/install)

> Set your hostname using variables

Replace landscape.yourdomain.com with the FQDN pointing to your server, and set the HOSTNAME and DOMAIN variables based on the FQDN.

HOSTNAME=landscape
DOMAIN=yourdomain.com
FQDN=$HOST_NAME.$DOMAIN
sudo hostnamectl set-hostname "$FQDN"

The FQDN variable is HOST_NAME but the previous variable is HOSTNAME. Guessing this is some type of typo?

---

