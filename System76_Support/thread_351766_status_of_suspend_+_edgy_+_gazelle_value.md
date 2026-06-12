---
title: "status of suspend + edgy + gazelle value"
date: 2007-02-02
forum: System76 Support
---

### Post by rgoldber on 2007-02-02
Curious about the status of suspend + edgy + gazelle value?  Last I heard it was working with feisty's kernel.  Any progress on this front?

Thanks,
Ryan

---

### Post by crichell on 2007-02-02
give this shot

```
sudo rm sudo rm /var/lib/dhcp3/*
```

Also post your /etc/default/acpi-support file.

---

### Post by fmarier on 2007-02-02
> **crichell said:**
> give this shot

```
sudo rm sudo rm /var/lib/dhcp3/*
```


You probably meant:

```
sudo rm /var/lib/dhcp3/*
```

---

### Post by crichell on 2007-02-02
thanks - that's right

---

