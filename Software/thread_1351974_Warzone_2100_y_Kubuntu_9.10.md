---
title: "Warzone 2100 y Kubuntu 9.10"
date: 2009-12-11
forum: Software
---

### Post by Javierkaiser on 2009-12-11
Hola gente, como va?
Bueno, estos dias me decidi e instale el Kubuntu 9.10. 
Todo joya hasta ahi. Quise instalar el Warzone 2100, la version beta que solo viene en codigo fuente, y al querer compilarla siguiendo la guia, me dice que el comando ./configure no existe (no existe fichero o directorio). 
Busque un poco en la web pero no encontre nada util, alguna sugerencia?


Y otra cosa rara ke me paso, es ke despues de instalar Kubuntu, el sonido en windows (estoy usando dual boot por ahora) dejo de funcionar, rarisimo. (placa de sonido: SB Audigy).

Saludos.

---

### Post by guillermolisi on 2009-12-11
> **Javierkaiser said:**
> Hola gente, como va?
Bueno, estos dias me decidi e instale el Kubuntu 9.10. 
Todo joya hasta ahi. Quise instalar el Warzone 2100, la version beta que solo viene en codigo fuente, y al querer compilarla siguiendo la guia, me dice que el comando ./configure no existe (no existe fichero o directorio). 
Busque un poco en la web pero no encontre nada util, alguna sugerencia?


Y otra cosa rara ke me paso, es ke despues de instalar Kubuntu, el sonido en windows (estoy usando dual boot por ahora) dejo de funcionar, rarisimo. (placa de sonido: SB Audigy).

Saludos.
Javier

Por favor abri otro thread, en Hardware, por el tema de la placa de sonido asi se mantienen dos hilos especificos, uno para cada problema.

Gracias

---

### Post by aledruetta on 2009-12-11
> **Javierkaiser said:**
> Hola gente, como va?
Bueno, estos dias me decidi e instale el Kubuntu 9.10. 
Todo joya hasta ahi. Quise instalar el Warzone 2100, la version beta que solo viene en codigo fuente, y al querer compilarla siguiendo la guia, me dice que el comando ./configure no existe (no existe fichero o directorio). 
Busque un poco en la web pero no encontre nada util, alguna sugerencia?

Saludos.

¿Será que te falta instalar las herramientas de compilación?

```
sudo aptitude install build-essential
sudo aptitude install linux-headers-`uname -r`
```

¿O será que falta el fichero "configure"?

---

### Post by Javierkaiser on 2009-12-12
Gracias por los comentarios.
Estuve viendo un poco mejor... y parece ke el archivo se habia bajado mal, y le faltaban algunas partes :-?

---

