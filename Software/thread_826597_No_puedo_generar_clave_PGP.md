---
title: "No puedo generar clave PGP"
date: 2008-06-12
forum: Software
---

### Post by _kAz_ on 2008-06-12
Gente quiero generar una clave PGP para unirme al grupo de Launchpad. Pretendía hacer la fácil siguiendo este tutorial [http://doc.ubuntu-es.org/Cómo_firmar_el_Código_de_Conducta_con_Seahorse](http://doc.ubuntu-es.org/Cómo_firmar_el_Código_de_Conducta_con_Seahorse), pero me sale esto:
```
No se pudo generar la clave PGP

Error general
```

Que hago?

---

### Post by faktorqm on 2008-06-12
Acá dice como se hace

[https://help.ubuntu.com/community/FirmandoElCodigoDeConductaComo](https://help.ubuntu.com/community/FirmandoElCodigoDeConductaComo)

```
gpg --gen-key
```

Salu2!!

---

### Post by _kAz_ on 2008-06-12
> **faktorqm said:**
> Acá dice como se hace

[https://help.ubuntu.com/community/FirmandoElCodigoDeConductaComo](https://help.ubuntu.com/community/FirmandoElCodigoDeConductaComo)

```
gpg --gen-key
```

Salu2!!


```
gpg: no se puede abrir `~/.gnupg/random_seed': Permiso denegado
Es necesario generar muchos bytes aleatorios. Es una buena idea realizar
alguna otra tarea (trabajar en otra ventana/consola, mover el ratón, usar
la red y los discos) durante la generación de números primos. Esto da al
generador de números aleatorios mayor oportunidad de recoger suficiente
entropía.
No hay suficientes bytes aleatorios disponibles. Por favor, haga algún
otro trabajo para que el sistema pueda recolectar más entropía
(se necesitan 275 bytes más).

```

:mad::mad::mad::mad:

**EDIT**
Espere un rato, abri dos mil aplicaciones mas y salió esto:
```
gpg: anillo público de claves no escribible encontrado: eof
Creación de la clave fallida: eof
gpg: nota: el fichero de semillas aleatorias no se ha actualizado
```

---

### Post by faktorqm on 2008-06-12
Seguiste el tutorial desde el principio paso a paso? 
Si no tiene suficiente entropia no te genera la clave, yo no abri ningun programa :P y despues de un tiempo me paso eso :P:P pero bueno, no sabia como trabajaba esa cosa. Despues me entere que no importa que abras muchas cosas, sino que esas cosas que abras hagan algo. (ejemplo, ponerte a comprimir/descomprimir un archivo, abrir el navegador y abrir todos los marcadores al mismo tiempo, poner a renderizar un video, una foto, o generar un paisaje).
Asi generas bytes aleatorios y te crea la clave. Reconozco que es medio caprichoso el coso ese, pero es seguro. Salu2!!

---

### Post by _kAz_ on 2008-06-12
Si, si, lo seguí desde el comienzo. Modifiqué el gpg.conf incluso.

Bueno, me armaré de paciencia y seguiremos intentando a ver que pasa.

---

### Post by _kAz_ on 2008-06-12
No hay caso... esto me esta agarrando de dolobu... Me faltan 45 bytes nomas y no hace nada. Me puse a descomprimir/recomprimir un archivo (todavía lo está haciendo porque era bastante grande), abri todos los marcadores y nada.

---

### Post by euzkoarima on 2008-06-12
Cuando lo hice y me salio que necesitaba más nros aleatorios abri un peli con vlc, y parece que eso le cayó bien. Probá, en una de esas...

Saludos,

---

### Post by _kAz_ on 2008-06-18
> **euzkoarima said:**
> Cuando lo hice y me salio que necesitaba más nros aleatorios abri un peli con vlc, y parece que eso le cayó bien. Probá, en una de esas...

Saludos,

Bueno intenté abriendo 2 películas, parecía que iba bien pero salió esto una vez más. Me parece que ya no es problema de los bytes aleatorios o lo que sea:

```
gpg: anillo público de claves no escribible encontrado: eof
Creación de la clave fallida: eof
gpg: nota: el fichero de semillas aleatorias no se ha actualizado
```

Me pregunto que miércoles será "eof"???

---

### Post by faktorqm on 2008-06-18
eof, significa End Of File (Fin de archivo) pero la verdad que no se por que te esta tirando eso... como estas generando la clave? postea todos los comandos. Salu2!

---

### Post by sdennie on 2008-06-18
> **_kAz_ said:**
> ```
gpg: no se puede abrir `~/.gnupg/random_seed': Permiso denegado

```


Una vez escribiste "sudo gpg --gen-key" (Que no es correcto.  Debes escribir "gpg --gen-key" sin "sudo")?  Creo que el problema es que tenes archivos de root en ~/.gnupg y ahora no podes leerlos.  Para arreglarlo:

```

sudo chown usuario:usuario ~/.gnupg/*

```

Usa el nombre de usuario tuyo en lugar de "usuario".

---

