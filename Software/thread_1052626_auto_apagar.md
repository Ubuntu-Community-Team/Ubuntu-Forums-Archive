---
title: "auto apagar"
date: 2009-01-27
forum: Software
---

### Post by tsueseres on 2009-01-27
hay algun programa que pague automaticamente el equipo a una hora determinada?

---

### Post by sdennie on 2009-01-27
Si, se puede.  Por exemplo, a apagar la maquina todos los dias as 20:30 podes:

```

sudo crontab -e

```

Y el crontab debe tener:

```

30 20 * * * /sbin/shutdown -h now

```

Si solo queres apagarla una vez, fijate el manpage de "at":

```

man at

```

---

### Post by sartrejp on 2009-01-29
También tenés gshutdown en los repositorios.

---

