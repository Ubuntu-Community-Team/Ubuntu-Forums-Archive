---
title: "Problema con wine."
date: 2010-07-12
forum: Software
---

### Post by Misuri9 on 2010-07-12
Buenas, es la primera vez que entro como usuario al foro y no se si esto esta en su sitio así que sino es así moverlo por favor.

Bueno, el problema es que estuve metiéndole mano al portátil y trastee con los archivos, conclusión, no me funciona wine.

He estado mirando varios post y hilos en otro foros pero no consigo ponerlo bien, querría saber como desinstalarlo completamente y volver a ponerlo(no se que repositorios son ni nada)

Utilizo ubuntu 10.4.

Gracias por la ayuda, este foro siempre me ha servido de mucho aunque nunca me habia hecho falta comentar;)

---

### Post by alfplayer on 2010-07-14
Se puede hacer purgando el paquete con la opción --purge de apt-get y después volviendo a instalarlo.

---

### Post by emiliano_raso on 2010-07-16
1) Abri una consola llendo a Aplicaciones/Accesorios/Terminal
2) En la consola escribí el siguiente comando:
```
sudo aptitude remove wine && sudo aptitude purge wine
```
3) Mandale ENTER y decile que si a todo lo que te pregunte.

Listo. Con eso lo desinstalas completito completito.
Cuando lo instales de nuevo, seguramente tengas en el menu las mismas cosas que tenias antes, porque eso se almacena en una carpeta en tu HOME que ese comando no la borra (al igual que en Windows se guardan las configuraciones de cada sesion en Documents and Settings).

Espero que te sirva. Saludos.

---

