---
title: "CoverGloobus y JARP"
date: 2010-05-14
forum: Software
---

### Post by harryscode on 2010-05-14
Instalé CoverGloobus desde ppa y tambien JARP del amigo mama21mama.. supuestamente todo en orden, pero al momento de querer ejecutarlos, no pasa nada. Me estará faltando algo para que funcionen, alguna libreria, la instalación de Lucid la hice desde cero, manteniendo el home intacto de karmic. Viendo el monitor del sistema, ni siquiera estan corriendo los programas mencionados.
Alguno tiene una idea de como arreglarlo o que puede ser. 
Gracias

---

### Post by harryscode on 2010-05-15
Bueno.. solucionado el problema de JARP, borre la carpeta .JARP de /home/diego que venia de Karmic, y volvì a instalar JARP y ahora funciona, me imagino que CoverGloobus debe ser algo parecido el problema. El unico inconveniente es que no veo una carpeta similar de CoverGloobus en el /home, salvo que tenga otro nombre, en ese caso el que conozca cual puede ser, más que agradecido si me puede dar una mano. 
Gracias.

---

### Post by leonardomdq on 2010-05-15
Hola harry, con Covergloobus te aconsejo que hagas lo mismo, borra las carpetas que tengas en:
```
 /usr/share/
```Y en 

```
/home/tuusuario/.config/
```Luego reinstala desde PPA Covergloobus y listo. Cualquier cosa avisa.

Saludos

---

### Post by harryscode on 2010-05-15
> **leonardomdq said:**
> Hola harry, con Covergloobus te aconsejo que hagas lo mismo, borra las carpetas que tengas en:
```
 /usr/share/
```Y en 

```
/home/tuusuario/.config/
```Luego reinstala desde PPA Covergloobus y listo. Cualquier cosa avisa.

Saludos
De lujo Leo.. funcionò perfecto. Muchas gracias por la ayuda:)

---

