---
title: "No puedo apagar, ni cerrar sesión!!"
date: 2010-05-25
forum: Software
---

### Post by dam1977 on 2010-05-25
Acá estoy de  nuevo. Por alguna extraña razón que escapa a mi torpe entendimiento desde ayer no puedo cerrar sesión, ni apagar la máquina. Estuve buscando pero no encuentro modo!!! (Bueno, el único modo es usar la opción cambiar de usuario, y cuando aparece la pantallita, cliquear abajo en apagar). Si alguien tiene idea agradecería....

---

### Post by dam1977 on 2010-07-01
Lo curioso es que a veces sucede y a veces no. Y no acierto a descubrir qué cosa hago para que se produzca ese fallo. Y me pasa tanto en casa como en el trabajo. El problema es que estoy promoviendo con bastante exito el cambio de todas las PCs de la empresa a Ubuntu y necesito solucionarlo. En fin, sigo buscando....

---

### Post by emiliano_raso on 2010-07-01
Encontraste algun tipo de patron o vinculo comun en los momentos en que sucede y en los que no?

A mi me pasó que habia instalado KDE sobre Gnome (sin desinstalar Gnome) y si ponia que utilizara KDM en vez de GDM, en Gnome no me aparecian los botones de Apagar, Reiniciar, etc...

Probá lo siguiente:
- Abri una consola.
- Tirá el comando
```
sudo dpkg-reconfigure gdm
```
- Elegí GDM y apretá ENTER.

---

