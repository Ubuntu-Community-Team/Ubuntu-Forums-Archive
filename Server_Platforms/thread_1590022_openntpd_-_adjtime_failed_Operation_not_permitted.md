---
title: "openntpd - adjtime failed: Operation not permitted"
date: 2010-10-07
forum: Server Platforms
---

### Post by stevek1977 on 2010-10-07
Not sure if something is wonky with openntpd or not, but figured I would come here for some assistance.

On Ubuntu 9.04, in syslog I see the following error:

```
adjtime failed: Operation not permitted
```On Ubuntu 8.04.4 LTS I do not get the same error.  

Running ntpdate command on the command line I get a similar error.

```
root@computer:/etc/# ntpdate -v pool.ntp.org
 7 Oct 05:47:40 ntpdate[7784]: ntpdate 4.2.4p4@1.1520-o Fri Dec  4 18:11:47 UTC 2009 (1)
 7 Oct 05:47:41 ntpdate[7784]: Can't adjust the time of day: Operation not permitted

```


Any suggestions?

---

### Post by lordkons on 2012-04-11
Buenas...

Siento revivir un hilo tan viejo, pero llegue aqui desde el buscador y creo que alguien mas llegara.

Para solucionar este problema, hacer lo siguiente:

apt-get install ntp ntp-doc

Y ya podremos ejecutar el comando correctamente. Yo uso esta linea:

ntpdate -u hora.roa.es

Un saludo

---

