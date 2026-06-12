---
title: "Dominio de Windows con  Likewise-open pero no tengo internet"
date: 2008-09-11
forum: Software
---

### Post by arysar on 2008-09-11
Instalé hardy heron desktop primero instale ntlmaps para acceder a internet detras del firewall ISA, anduvo lo más bien, instalé likewise-open, puedo ingresar con los usuarios del dominio pero no me funciona el firefox, no me sale ni la pantalla de bienvenida, quise agregar una impresora de la red, me pide contraseña, le ingreso la contraseña pero no me deja me vuelve a pedir la contraseña del usuario. Algo debe estar mal...

Gracias!

---

### Post by likeWiseGuy on 2008-09-25
> **arysar said:**
> Instalé hardy heron desktop primero instale ntlmaps para acceder a internet detras del firewall ISA, anduvo lo más bien, instalé likewise-open, puedo ingresar con los usuarios del dominio pero no me funciona el firefox, no me sale ni la pantalla de bienvenida, quise agregar una impresora de la red, me pide contraseña, le ingreso la contraseña pero no me deja me vuelve a pedir la contraseña del usuario. Algo debe estar mal...

Gracias!

Hola arysar,

No estoy seguro que el problema que tienes con Firefox tiene que ver con likewise-open. Probastes salir del dominio con likewise-open? Si salis "domainjoin-cli leave" y todavía tienes problemas con Firefox, parece que los problemas son con la red o firewall.

Si necesitas mas ayuda, mándame un mensaje y veo si puedo ayudar.

---

### Post by arysar on 2008-09-26
Hola Facundo, gracias por contestarme.

El asunto es así, tengo un usuario local con privilegios para sudo, instalo NTLMAPS para acceder al proxy ISA que tengo instalado en el dominio, internet anda muy bien, instalo likewise-open del repositorio de ubunto, es la version 4.0.5, me uno al dominio, hasta ahi todo bien, luego me logueo con un usuario del Dominio AD, eso anda perfecto, pero no tengo más internet, si ingreso con el usuario local sigo teniendo internet perfecto, con el usuario de AD no. Ingresar con el usuario de AD es distinto que con el usuario local, algo de esto debe estar interfiriendo NTLMAP para autenticarse con el ISA.


Leonardo

---

### Post by arysar on 2008-09-26
Hola, ya funcionó lo de internet, me faltaba configurar el proxy para ese usuario, ahora me falta lo de las impresoras, pero creo que tiene que ver con la integración de samba con likewise, voy a seguir la guia sobre ese tema.

---

### Post by likeWiseGuy on 2008-09-30
> **arysar said:**
> Hola, ya funcionó lo de internet, me faltaba configurar el proxy para ese usuario, ahora me falta lo de las impresoras, pero creo que tiene que ver con la integración de samba con likewise, voy a seguir la guia sobre ese tema.

Leonardo,

Gracias por avisar de la integración de likewise-open. Me parecía que faltaba la configuración del proxy con el usuario. 

Para configurar las impresoras, si, vas a tener que configurar samba. Seguramente que eso sera fácil.

Si necesitas mas ayudo, por favor avísame. Voy a tratar de ayudar lo mas posible que pueda.

Gracias!

---

