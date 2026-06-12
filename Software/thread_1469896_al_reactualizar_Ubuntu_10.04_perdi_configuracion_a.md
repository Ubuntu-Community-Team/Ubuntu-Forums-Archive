---
title: "al reactualizar Ubuntu 10.04 perdi configuracion apache con php"
date: 2010-05-02
forum: Software
---

### Post by papachan on 2010-05-02
Hola !

Me fue bastante bien con el upgrade de ubuntu 10.04. Solo que tenia mi localhost funcionando antes perfectemente, y ahora tengo miles mensajes de error cuando abro el localhost en el browser.

lo primero que hice es un restart del apache server
pero me tira es error
Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName

esto lo habia solucionado antes agregando 127.0.1.1 en los hosts.
pero ahora devuelta. hice un phpinfo() y no lo puede interpretar.

Saben que tengo que hacer?

saludos

Dan

---

### Post by papachan on 2010-05-02
Bueno pude comprobar que ubuntu 10-04 no me traia el modules php4. ahora veo que lo tenia tal vez configurado con php5.

---

### Post by papachan on 2010-05-02
Saben como puedo volver a instalar los modulos de php4 . parecen haber desaparecidos del sinaptic.

---

