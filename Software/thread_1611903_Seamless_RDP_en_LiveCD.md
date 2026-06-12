---
title: "Seamless RDP en LiveCD"
date: 2010-11-02
forum: Software
---

### Post by Wiredfixer on 2010-11-02
Al dia de hoy, me encuentro trabajando con SeamlessRDP, de esta manera, puedo ejecutar aplicaciones de Windows via RDP e integrarlas en mi Ubuntu Desktop, tal como lo hace Citrix.

Las configuraciones son simples, en mi Laptop trabajo perfectamente y las configuraciones que requiero las hago a mano, sin embargo, mi meta es crear un LiveCD en el cual se pueda trabajar de esta manera, mi unico problema es que no he podido copiar las configuraciones de Compiz para que las Decoraciones de Ubuntu no salgan en la ventana RDP y solo se vea la aplicacion tal cual se ve en Windows.

En mi Laptop hice esto en CCSM (configurador compiz)

Decoration windows: any & !(class=rdesktop)
Shadow windows: & !(type=Dock) & !(class=rdesktop)

Esto me da lo que necesito, una ventana de windows sin bordes de Ubuntu.

Aun asi, esto no lo puedo lograr en LiveCD y mi idea es que las configuraciones sean automaticas, incluso si decido instalar el LiveCD que las configuraciones sin bordes se conserven o se apliquen sin ir por cada PC metiendo las configuraciones requeridas.

Alguna Idea?

---

