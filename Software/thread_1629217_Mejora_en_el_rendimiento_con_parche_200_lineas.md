---
title: "Mejora en el rendimiento con parche 200 lineas"
date: 2010-11-23
forum: Software
---

### Post by Tosh78 on 2010-11-23
Hola a todos! Estuve viendo en varios sitios diferentes el tema de las 200 lineas de codigo que al parecer generan una mejora importante en el rendimiento y me esta tentando el tema.
Sin embargo me desconcierta ver las diferentes formas de implementarlo y dado que no soy alguien tecnico, me quedo un poco sin saber que forma usar para implementarlo corriendo la menor cantidad de riesgos posible.
Alguien lo ha hecho en Ubuntu 64 bits? Que tal fue la experiencia? 
Alguna sugerencia sobre que forma seguir?

Para el que no sabe de que estoy hablando, aca dejo un link que explica en detalle: [http://ubuntulife.wordpress.com/2010/11/20/el-parche-milagro-de-linux-de-200-lineas-implementado-en-4-lineas-de-bash/]("http://ubuntulife.wordpress.com/2010/11/20/el-parche-milagro-de-linux-de-200-lineas-implementado-en-4-lineas-de-bash/")

---

### Post by juancarlospaco on 2010-11-23
Probalo en una Virtualbox  :)

---

### Post by Tosh78 on 2010-11-23
Fue lo primero que pense, pero yo uso la version de 64 bits y en VirtualBox no puedo usar la de 64, necesitaria usar la de 32, y no creo que sea lo mismo.

---

### Post by alfplayer on 2010-11-23
La modificación con bash no parece riesgosa, podés probarla directamente, sin máquina virtual, con un live cd/usb si no funciona para corregir o revertir los cambios.

> **Tosh78 said:**
> Fue lo primero que pense, pero yo uso la version de 64 bits y en VirtualBox no puedo usar la de 64, necesitaria usar la de 32, y no creo que sea lo mismo.

Se pueden crear *guests* de 64-bit con un *host* de 64-bit.

Para hacer el cambio de rendimiento, el método de bash sería suficiente.

---

### Post by Wiredfixer on 2010-11-24
Voy aplicando el parche. Lo hice manual, esperemos al final del dia como esta, al momento segun yo vi un balanceo en mi memoria y cpu.. pero necesitaria verificar..


Hay un script que lo hace todo, a ver que tal les funciona a los que no han hecho movimientos:

[http://www.webupd8.org/2010/11/script-to-automatically-apply-200-lines.html](http://www.webupd8.org/2010/11/script-to-automatically-apply-200-lines.html)

---

### Post by marcelo_bur on 2010-11-24
> **Wiredfixer said:**
> Voy aplicando el parche. Lo hice manual, esperemos al final del dia como esta, al momento segun yo vi un balanceo en mi memoria y cpu.. pero necesitaria verificar..


Hay un script que lo hace todo, a ver que tal les funciona a los que no han hecho movimientos:

[http://www.webupd8.org/2010/11/script-to-automatically-apply-200-lines.html](http://www.webupd8.org/2010/11/script-to-automatically-apply-200-lines.html)

Hola. Cuidado, en el sitio recalcan que el script es solo para usuarios de la versión de 64-bit
Saludos

---

### Post by Wiredfixer on 2010-11-24
Estoy Usando 64bit, no problem.. :D


Y de hecho se nota una mejora, el CPU me gestiona mejor esto y el consumo de ram bajo en un 10%..

Antes andaba en un 60% en Uso y el Resto de Cache... Ahora ando en 50 y 50 y a veces en 45 y 55.

Tendrian que probarlo a ver que tal.

---

### Post by Tosh78 on 2010-11-25
Buenisimo!! Voy a probar ese script entonces. Muchas gracias por contar que tal te fue.

---

### Post by Wiredfixer on 2010-11-26
Confirmado, la experiencia es bastante alentadora:

Mi Swap esta en 0% de Uso, de 1GB de ram que tengo, uso 480 y el resto esta en espera de uso (cache)

El equipo se siente muy fluido y arranco en menos de un minuto sin compilar el kernel, voy a ver si ajustandolo a mis necesidades le doy mas potencia.

Saludos!

---

### Post by EnriqueK on 2010-11-26
No me queda claro que va a pasar si se ejecuta el script o se li hace manualmente y luego después aparece una actualización del kernel con el parche incorporado, tengo entendido que suele pasar que se actualizan los kernels con parches que corresponden a versiones superiores, lógicamente si la necesidad así lo amerita, este caso puede ser ocurrir tal vez para todos los kernels de las versiones vigentes de Ubuntu.

---

