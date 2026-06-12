---
title: "Problema al compilar subtitleeditor"
date: 2011-03-14
forum: Software
---

### Post by nemodot on 2011-03-14
Luego de satisfacer todas las dependencias que ./Configure me pedía hice el sudo Checkinstall y luego de todo el proceso falló al final:

```
Creando paquete debian... FAILED!
```

y luego me sale ésto:

```
dpkg-deb: error en el análisis, en archivo «/var/tmp/tmp.KXQHMflcOX/package/DEBIAN/control» línea cercana 12 paquete «subtitleeditor»:
 valor vacío para version
```

y eso es todo lo que me dice. No tengo la menor idea que hacer.
Alguna pista?:confused:

---

### Post by guillermolisi on 2011-03-15
Tres:

Lo instalas desde los repositorios de Ubuntu (creo que tenes que activar Multiverse para que aparezca el paquete). La version disponible para MM es la 0.30-1.1

Que te fijes en el fuente y busques que dice la linea que menciona el mensaje de error.

Que recurras a la pagina del desarrollador y veas si hay alguna nota al respecto.

---

### Post by nemodot on 2011-03-15
De algún modo se ha instalado por que ahora lo puedo ejecutar, sin embargo la última vez que probé el error seguía existiendo. Solved.

---

