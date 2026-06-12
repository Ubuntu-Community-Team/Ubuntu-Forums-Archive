---
title: "Ni Evolution ni Thunderbird reciben o envían mails despues de pasar de 10.04 a 12.04"
date: 2012-09-07
forum: Software
---

### Post by guillejcopello on 2012-09-07
Hola, tengo un problema con mi mail.
El sábado pegué el salto desde Ubuntu 10.04 a 12.04. Después de la superactualización, Evolution, que venía funcionando perfectamente, no recibe ni manda los mails. No funciona ni para mi cuenta del trabajo (pop) ni la de hotmail. 
Chequeé la configuración de estas cuentas en Evolution y son las que corresponden.
Desinstalé Evolution y lo volví a instalar y nada.
Probé con Thunderbird y sucede lo mismo.
Probé con netcat la apertura de puertos y están abiertos:

qai@qai:~$ nc -z -v huemul.ffyb.uba.ar 110
Connection to huemul.ffyb.uba.ar 110 port [tcp/pop3] succeeded!
qai@qai:~$ nc -z -v huemul.ffyb.uba.ar 25
Connection to huemul.ffyb.uba.ar 25 port [tcp/smtp] succeeded!

Probé entrando desde la terminal:
qai@qai:~$ evolution
Migrating cached data
  mv /home/qai/.evolution/cache/tmp /home/qai/.cache/evolution/tmp
  FAILED: Directory not empty
  rmdir /home/qai/.evolution/cache
  FAILED: Directory not empty (contents follows)
          tmp
Migrating config data
Migrating local user data
  rmdir /home/qai/.evolution/tasks
  FAILED: Directory not empty (contents follows)
          local
  rmdir /home/qai/.evolution/memos
  FAILED: Directory not empty (contents follows)
          local
  rmdir /home/qai/.evolution/cache
  FAILED: Directory not empty (contents follows)
          tmp
  rmdir /home/qai/.evolution/calendar
  FAILED: Directory not empty (contents follows)
          local
  rmdir /home/qai/.evolution/addressbook
  FAILED: Directory not empty (contents follows)
          local

No se si esto les dice algo.
¿Alguien tiene idea qué puedo probar?
Saludos y gracias

Guille

---

