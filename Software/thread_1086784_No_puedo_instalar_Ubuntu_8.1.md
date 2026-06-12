---
title: "No puedo instalar Ubuntu 8.1"
date: 2009-03-04
forum: Software
---

### Post by javdie on 2009-03-04
He aqui mi primer pregunta en el foro:
Tengo una laptop ACER Aspire 5315. Estoy intentando instalar Ubuntu, pero cada vez que booteo con el CD, en cuanto selecciono la opcion de instlar, se cuelga la maquina y no pasa de ahi. He probado de usarla opcion de liveCD, pero da el mismo resultado. Si inicio la instalacion con el Wubi desde Windows, parece correr correctamente, y al menos hasta llegar al 5% no tiro errores, pero no deseo Ubuntu como un programa mas de Windows, sino que lo quiero instalar en una particion dedicada.
Leyendo un poco encontre que quizas Ubuntu no reconozca la controladora de disco, o el disco mimso... pero, revice la informacion tecnica al respecto, y la marca y modelo de mi disco/controladora deberia funcionar con ubuntu.
¿me podran dar una mano con esto?

            desde ya, muchas grcias!

---

### Post by luks911 on 2009-03-04
Bienvenido.
Le pongo unas fichas a un problema con el CD. Usá la opción Verificar el CD en busca de defectos, del menú inicial. O directamente probá con otro disco, preferentemente grabado a baja velocidad. 
Ah, cuando se cuelga, ¿te muestra algún mensaje o error?
Contá cómo fue. Saludos

---

### Post by javdie on 2009-03-04
No aparece cartel alguno, solo no avanza nisiquiera a la barra donde deberia comenzar a cargar algun archivo. Le doy enter a Instalar, probar o verificar CD y es todo.. no sale de ahi, no muestra nada, es mas.. hasta deja de girar el CD en mi lectora.
Vere de volver a grabar el disco y te cuento como me fue... lo raro es que sobre Windows lo lee correctamente y logro verificar lso datos... sobre el instalador de Ubuntu... nada :(
Desde ya, muchisimas gracias por tu pronta respuesta

---

### Post by javdie on 2009-03-06
Te cuento que el problema estaba enla configuracion del SETUP de las notebooks que vienen preparadas para WinVista. Las controladoras de disco pueden configurarce tanto como SATA como... bue, de otro modo, cuya sigla ahora no recuerdo. Son solo dos modos, asi que si alguien lo busca, no tardare en encontrarlo. El tema es que si el setup lo tienes configurado para vista, ubunto no arrancara ya que no detecta disco alguno.
Me paso lo mismo al instalar XP, pero lo habia solucionado con un parche para el instalador de windows... un parche para windows, que original :P

         Ya tengo ubuntu instalado... y por fin he podido dejar atras a Windows.

---

### Post by luks911 on 2009-03-06
Buenísimo. Y podemos seguir culpando a window$, ja.
No dejés de consultar por cualquier duda. Y gracias por la info.

Saludos

---

### Post by dmela2012 on 2009-03-13
Yo tengo la misma notebook, instale bien, pero internet no me funciona, ni con wifi, y con cable de red. por favor ayuda!!!

---

### Post by luks911 on 2009-03-13
> **dmela2012 said:**
> Yo tengo la misma notebook, instale bien, pero internet no me funciona, ni con wifi, y con cable de red. por favor ayuda!!!

¿El problema es sólo con el wifi o también con cable?
¿Cómo es la conexión a internet? ¿Hay un modem con el que tenés que marcar la conexión desde la máquina o tenés un router que se conecta solo?
Además, abrí una terminal (Aplicaciones > Accesorios > Terminal) y ejecutá ```
lspci
``` el resultado pegalo acá para poder confirmar cuál es la placa wifi.

---

