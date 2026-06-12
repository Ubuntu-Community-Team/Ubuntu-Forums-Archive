---
title: "Pantalla negra con Kernel 2.6.27-13 y NVidia 177"
date: 2009-03-03
forum: Software
---

### Post by santiagoward2000 on 2009-03-03
Hola gente,
Vengo con una consulta, a ver si a alguien más le pasó. Tengo una GeForce 8400M. Hoy me salió una actualización de Kernel en Intrepid. La instalé, reinicié la máquina, pero después del Upslash, el monitor se queda en negro, y ni siquiera puedo entrar a una consola con Ctrl+Alt+F1.
Entré con el Kernel anterior, y anda todo perfecto. También entré en el Recovery Mode del Kernel nuevo, reconfiguré el Xorg, saqué los drivers restringidos de NVidia y también, anda bien.
¿Puede ser un nuevo bug? ¿A alguien más le pasó?
Saludos!

---

### Post by albandy on 2009-03-03
El driver que estás usando es de los repositorios o de NVIDIA directamente?

Si es el de los repositorios mal asunto, si es el de NVIDIA tendrás que recompilarlo.

De todas formas puedes pasarle un parámetro al Kernel para que use el framebuffer, simplemente añade a la linea del kernel del menu.lst vga=791

te debería quedar tal que así:
title		Ubuntu 8.10, kernel 2.6.27-11-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=f4d28e38-557d-4dd8-8b8f-60445d43382f ro quiet splash vga=791
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

---

### Post by santiagoward2000 on 2009-03-03
> **albandy said:**
> El driver que estás usando es de los repositorios o de NVIDIA directamente?

Si es el de los repositorios mal asunto, si es el de NVIDIA tendrás que recompilarlo.

De todas formas puedes pasarle un parámetro al Kernel para que use el framebuffer, simplemente añade a la linea del kernel del menu.lst vga=791

te debería quedar tal que así:
title		Ubuntu 8.10, kernel 2.6.27-11-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=f4d28e38-557d-4dd8-8b8f-60445d43382f ro quiet splash vga=791
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

Hola!
Estoy usando el driver de los repositorios. Supongo que tengo que reportarlo como bug, no?
Probé agregar el vga=791, y no ayudó. Solo hizo que el Upslash se vea más chico, pero después sigue quedando todo en negro.

---

### Post by luks911 on 2009-03-03
Recién esta noche actualizo y voy a saber si me pasa. Tengo la misma coniguración pero con una placa 7000M.
¿Probaste instalando el driver 180 de los repositorios?

---

### Post by santiagoward2000 on 2009-03-03
> **luks911 said:**
> Recién esta noche actualizo y voy a saber si me pasa. Tengo la misma coniguración pero con una placa 7000M.
¿Probaste instalando el driver 180 de los repositorios?

Mmm... no. Como el **jockey-gtk** solo me mostraba el 177 y el 173, no sabía que el 180 estaba en los repositorios. ¿El 180 andará con mi placa?

---

### Post by luks911 on 2009-03-03
> **santiagoward2000 said:**
> Mmm... no. Como el **jockey-gtk** solo me mostraba el 177 y el 173, no sabía que el 180 estaba en los repositorios. ¿El 180 andará con mi placa?

Sí, está soportada. El jockey-gtk no te lo muestra porque no tenés instalado el paquete nvidia-180-modaliases que se encarga de chequear la placa que tenés y qué driver le corresponde. Lo sé porque me pasó, aunque desconozco las causas. 
Igual, tanto el 177 como el 180 soportan tu placa. Si querés, antes de instalar el drive 180 instalá nvidia-180-modaliases y vas a ver que el jockey te lo muestra como recomendado.
En el peor de los casos siempre podés volver a instalar 177 sin problemas.

---

### Post by luks911 on 2009-03-03
Dos cosas más: no voy a tener la actualización porque ese kernel está en proposed. Bah, si llega a hacer falta lo instalo para probar. Avisá.
Y la otra: ahora me doy cuenta que para instalar el driver 180 vas a tener que entrar al kernel nuevo en recovery y hacerlo desde terminal

```
sudo aptitude install nvidia-glx-180
```

porque por la vía gráfica lo vas instalar pero con el kernel viejo.

---

### Post by santiagoward2000 on 2009-03-03
> **luks911 said:**
> Dos cosas más: no voy a tener la actualización porque ese kernel está en proposed. Bah, si llega a hacer falta lo instalo para probar. Avisá.
Y la otra: ahora me doy cuenta que para instalar el driver 180 vas a tener que entrar al kernel nuevo en recovery y hacerlo desde terminal

```
sudo aptitude install nvidia-glx-180
```

porque por la vía gráfica lo vas instalar pero con el kernel viejo.

Gracias luks!
El driver 180 anda bien. :D Solved!

---

### Post by luks911 on 2009-03-04
Excelente. 
Lo voy a probar cuando se actualice el kernel porque por ahora tenía algún problema. Qué raro lo drivers de nvidia haciendo lío...

Saludos

---

