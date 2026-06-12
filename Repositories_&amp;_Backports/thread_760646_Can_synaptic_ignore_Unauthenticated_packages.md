---
title: "Can synaptic ignore Unauthenticated packages?"
date: 2008-04-20
forum: Repositories &amp; Backports
---

### Post by yurenju on 2008-04-20
hi all,

i want to use synaptic to install my package just like gnome-app-install. but my repository is Unauthenticated. apt-get can use this to avoid:
```
apt-get --allow-unauthenticated --force-yes --y install <something>
```

when i use this synaptic paramater:
```
sudo synaptic --hide-main-window --non-interactive \
--set-selections-file="something.txt" \
-o APT::Get::Assume-Yes=true \
-o APT::Get::force-yes=true  -o APT::Get::AllowUnauthenticated=true
```

but it also pop the NOT AUTHENTICATED warning... (see attachment )

does any parameter can do auto install without check authenticated?

---

