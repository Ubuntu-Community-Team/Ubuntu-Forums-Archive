---
title: "problema al iniciar cups"
date: 2009-08-07
forum: Software
---

### Post by marqz on 2009-08-07
hola ubunteros! tengo un problema para iniciar cups en mi ubuntu jaunty..

el problema está en cuando lo quiero iniciar desde terminal mediante :

```
$ sudo /etc/init.d/cups start
 * Starting Common Unix Printing System: cupsd                                  cupsd: Child exited with status 1!
                                                                        [fail]

```

y cuando quiero ver el archivo de error me sale esto:

```
I [07/Aug/2009:13:22:51 -0300] Listening to 0.0.0.0:631 (IPv4)
I [07/Aug/2009:13:22:51 -0300] Listening to :::631 (IPv6)
I [07/Aug/2009:13:22:51 -0300] Listening to /var/run/cups/cups.sock (Domain)
W [07/Aug/2009:13:22:51 -0300] "AuthClass System" is deprecated; consider using "Require user @SYSTEM" on line 21.
E [07/Aug/2009:13:22:51 -0300] Unknown Location directive SystemGroup on line 22.
I [07/Aug/2009:13:24:21 -0300] Listening to 0.0.0.0:631 (IPv4)
I [07/Aug/2009:13:24:21 -0300] Listening to :::631 (IPv6)
I [07/Aug/2009:13:24:21 -0300] Listening to /var/run/cups/cups.sock (Domain)
W [07/Aug/2009:13:24:21 -0300] "AuthClass System" is deprecated; consider using "Require user @SYSTEM" on line 21.
E [07/Aug/2009:13:24:21 -0300] Unknown Location directive SystemGroup on line 22.
I [07/Aug/2009:13:24:23 -0300] Listening to 0.0.0.0:631 (IPv4)
I [07/Aug/2009:13:24:23 -0300] Listening to :::631 (IPv6)
I [07/Aug/2009:13:24:23 -0300] Listening to /var/run/cups/cups.sock (Domain)
W [07/Aug/2009:13:24:23 -0300] "AuthClass System" is deprecated; consider using "Require user @SYSTEM" on line 21.
E [07/Aug/2009:13:24:23 -0300] Unknown Location directive SystemGroup on line 22.
```

estuve buscando por todos lados soluciones en google y nada :(

espero que me ayuden muchisimas gracias.. saludos!

---

### Post by cmarchesin on 2009-09-21
Has podido hacer andar el cups en tu instalación ? Lo instalé hace unos dias para dejar funcional la red que tengo en donde hay un equipo con winXP y no tuve problemas para hacer arrancar el servicio (de echo se inició solo, no tuve que iniciarlo manualmente). Podemos isntalar el soft con los pasos que he seguido yo y ver que quede funcionando. Comentame en que estado esta el tema. Saludos. Catriel

---

