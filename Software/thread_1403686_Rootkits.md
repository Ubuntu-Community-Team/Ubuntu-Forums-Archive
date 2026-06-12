---
title: "Rootkits?"
date: 2010-02-10
forum: Software
---

### Post by aledruetta on 2010-02-10
Hola Comunidad!

Hice un escan de mi disco rígido con rkhunter, un aplicativo para detectar rootkits. El log del rkhunter me tiró lo siguiente:

```
alejandro@alejandro-laptop:~$ sudo cat /var/log/rkhunter.log | grep Warning
[17:31:05] /usr/sbin/unhide                                  [ Warning ]
[17:31:05] Warning: The file '/usr/sbin/unhide' exists on the system, but it is not present in the rkhunter.dat file.
[17:31:05] /usr/sbin/unhide-linux26                          [ Warning ]
[17:31:05] Warning: The file '/usr/sbin/unhide-linux26' exists on the system, but it is not present in the rkhunter.dat file.
[17:32:45]   Checking /dev for suspicious file types         [ Warning ]
[17:32:45] Warning: Suspicious file types found in /dev:
[17:32:45]   Checking for hidden files and directories       [ Warning ]
[17:32:46] Warning: Hidden directory found: /etc/.java
[17:32:46] Warning: Hidden directory found: /dev/.udev
[17:32:46] Warning: Hidden directory found: /dev/.initramfs
```

El problema es que a partir de ahí no sé qué tengo que hacer...
¿Alguien sabe?

---

### Post by Wiley_Linux on 2010-02-10
Hola aledruetta,

Yo tambien uso rkhunter y me tengo exactamente los mismos Warning. Yo diria que son solo Falsos positivos y no hay nada de que preocuparse. Hay algunos que estan reconocidos como tal. Echale un vistazo a este link:

[http://www.rootkit.nl/articles/rootkit_hunter_howto_false_positives.html](http://www.rootkit.nl/articles/rootkit_hunter_howto_false_positives.html)

Si todavia tienes dudas siempre te puedes poner en contacto con rkhunter en [http://www.rootkit.nl/contact/](http://www.rootkit.nl/contact/) y a ver que te dicen ellos.

Un saludo

---

### Post by doas777 on 2010-02-10
those are common messages. you are fine.

---

### Post by aledruetta on 2010-02-10
> **Wiley_Linux said:**
> Hola aledruetta,

Yo tambien uso rkhunter y me tengo exactamente los mismos Warning. Yo diria que son solo Falsos positivos y no hay nada de que preocuparse. Hay algunos que estan reconocidos como tal. Echale un vistazo a este link:

[http://www.rootkit.nl/articles/rootkit_hunter_howto_false_positives.html](http://www.rootkit.nl/articles/rootkit_hunter_howto_false_positives.html)

Si todavia tienes dudas siempre te puedes poner en contacto con rkhunter en [http://www.rootkit.nl/contact/](http://www.rootkit.nl/contact/) y a ver que te dicen ellos.

Un saludo

Ah, bueno, gracias. Me quedo más tranquilo.
Espero darme cuenta cuando no sea una falsa alarma.
Saludos!

---

### Post by aledruetta on 2010-02-10
> **doas777 said:**
> those are common messages. you are fine.

Thank you! (¿será que se escribe así?)

---

