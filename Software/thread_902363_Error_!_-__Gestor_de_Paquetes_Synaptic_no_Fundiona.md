---
title: "Error ! -  Gestor de Paquetes Synaptic no Fundiona"
date: 2008-08-27
forum: Software
---

### Post by Marcos Repezza on 2008-08-27
Hola tengo el siguiente error... cada vez que voy a Sistemas>AdministracioN>Gestor de Paquetes Synaptic me larga el Siguiente error:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

lo mismo me pasa cuando quiero compilar algun programa o actualizar el sistema...
tengo la Version Ubuntu 7.10 por favor si alguien puede ayudarme soy nuevo en esto. Gracuas

---

### Post by SLA_leandrin on 2008-08-27
Bueno Marcos, la solución es fácil.

Abrite una consola y tipeá

```
sudo dpkg --configure -a
```

Eso debería solucionarte el problema. Avisá cualquier cosa.

Saludos!

---

### Post by Marcos Repezza on 2008-08-27
Gracias amigo si soluciono el error... eso es porque puse un theme y luego elimine el paquete no?

---

### Post by SLA_leandrin on 2008-08-27
Generalmente esto se debe a que mientras estabas instalando algo se interrumpió por alguna causa la instalación, o se desconectó de internet...

---

### Post by Marcos Repezza on 2008-08-28
si eso paso! gracias nuevamente

---

