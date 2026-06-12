---
title: "[SOLUCIONADO] Problema particiones ext3"
date: 2009-08-16
forum: Software
---

### Post by Kay//J.Tune on 2009-08-16
Luego de mucho googlear y de buscar en los otros topics, decidi postear mi problema.
Tengo un equipo con XP y Ubuntu (hace una semana que me encuentro en ubuntu) y todos mis archivos de musica, videos, etc se encuentran en dos particiones NTFS. Un amigo de la U me comentó que para traspasar sus archivos utilizo una tecnica algo lenta, redimensiono su particion de windows y creo una ext3 y traspasaba archivos de su antigua particion a la ext3, luego volvia  a redimensionar la NTFS asi sucesivamente hasta que traspasaba todos sus archivos. Bueno quise intentarlo asi que, usando gparted, redimensione la particion NTFS, cree la particion ext3, pero.... no puedo copiar ningun archivo o crear alguna carpeta detro de la nueva particion. probe con una ext4 y nada, pense en reiniciar lo hice pero nada. Puedo montar la particion sin problemas y aparece la carpeta lost+found ( lei que si esa carpeta existia era porque la particion existia y estaba montada).
Estoy en Ubuntu 9.04 y todos mis discos duros son IDE.
Ojala me puedan ayudar =D

---

### Post by augias on 2009-08-17
Creo que tienes que revisar los permisos de esta particion. Si haces click derecho sobre el icono de la particion ext3 montada y miras en las propiedades, puedes ver a quien le pertenece esa particion. Si le pertenece a "root", que es lo mas probable, tienes que meterte a la consola como root y cambiar los permisos para que tu usuario de ubuntu pueda escribir y leer. 

Prueba esto. Te logeas como root: 
```
su
```
y das tu contraseña de root (lo puedes establecer en sistema/administracion/usuarios y grupos en tu menu)

```
cd /media
```
que es para entrar a la carpeta /media, donde deberia estar montada tu particion de ext3 (llamemosla "particionext3" pal ejemplo).

y a cambiar los permisos
```
chmod -R 766 particionext3 **para que otros usuarios puedan leer y escribir*
*o si prefieres, escribes*
chmod -R 777 particionext3 **para que otros usuarios puedan leer, escribir y ejecutar*
```

chmod modifica los permisos. -R lo hace recursivo, a todas las subcrpetas y archivos. el numero es el valor que le das, y finalmente va el nombre del directorio en cuestion.

Ojala eso sea lo que arregla tu problema! Un saludo.

---

### Post by Carlos C on 2009-08-17
> **Kay//J.Tune said:**
> Un amigo de la U me comentó que para traspasar sus archivos utilizo una tecnica algo lenta, redimensiono su particion de windows y creo una ext3 y traspasaba archivos de su antigua particion a la ext3, luego volvia  a redimensionar la NTFS asi sucesivamente hasta que traspasaba todos sus archivos. Bueno quise intentarlo asi que, usando gparted, redimensione la particion NTFS, cree la particion ext3, pero.... no puedo copiar ningun archivo o crear alguna carpeta detro de la nueva particion.

Disculpa, pero no entiendo lo que quieres hacer. ¿Deseas compartir archivos entre windows y ubuntu? No veo la necesidad de modificar sucesivamente una partición, me parece peligroso para la integridad de la tabla de particiones. Lo mejor es que tengas una partición FAT32 o NTFS que puedas leer desde ambos sistemas. Si eso es lo que quieres, perdona, pero es que no entendí.
Saludos.

---

### Post by Kay//J.Tune on 2009-08-17
Wahh muchisimas gracias augias,
hice lo que me indicaste y salio todo a la perfeccion  muchisimas gracias =D
Y respondiendo a carlos C, Solamente queria traspasar archivos desde 2 particiones NTFS a una ext3
ya que el 90% del tiempo estare en ubuntu, pero ahora que puedo escribir en ella no hay problema
muchisimas gracias =D:KS

( lo del traspaso sucesivo fue algo que me comento un compañero de la U, tampoco estaba seguro de hacerlo xD)

---

### Post by Carlos C on 2009-08-17
Ok, tema solucionado entonces!

---

