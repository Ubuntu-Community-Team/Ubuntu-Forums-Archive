---
title: "Problemas luego de actualizar a Ubuntu 9.04"
date: 2009-06-05
forum: Software
---

### Post by biale on 2009-06-05
Aquí va el primero de dos posts, esta vez lamentando molestando a los foristas.  Ya describo el problema...

Se trata de una computadora de escritorio que pasó por actualizaciones sucesivas desde Ubuntu GG a HH y luego a II sin mayores problemas. Tiene tres usuarios definidos para producción con ajustes distintos y dos para pruebas. Sin cosas raras, lo único que podía traer conflictos es el paquete kdebase.

Y hace una semana intente actualizar a 9.04 JJ – afortunadamente -  en un área de prueba. La actualización terminó bien y luego de algunas pruebas todo parecía estar funcionando bien, salvo en algún detalle que voy a describir al final del post. 

Cuando ya estaba por dar el ok definitivo y pasar al nuevo 9.04 JJ, los líos se presentaron bastante rápido: pareciera que “algo” se reconfiguró y allí comenzaron los problemas. Al ingresar con uno de los usuarios intempestivamente Dolphin comenzó a reemplazar a Nautilus al intentar acceder a “Lugares”. Algunos reboot después, los tres usuarios estaban con dolphin para todo. Por el reemplazo no se visualizaba el área de escritorio, solo los paneles. Y no arrancaba en forma automática compiz/ emerald, ni la aceleración gráfica, tampoco los screenlets, etc.

Usando Google encontré algunas ideas, pero no funcionaron. Probablemente se aplican a otras versiones de Gnome?  Rastree el disco buscando lo que dijera “dolphin” y “nautilus” pero no encontré nada util.

Lo único que parece dar resultado es borrar en forma bastante completa las configuraciones de los  usuarios. Pero, por un lado sería bastante tedioso volverlos a configurar y por otro lado no tengo seguridad de que de nuevo se produzca la maldita “reconfiguración retardada”.

Luego de pelear bastante, mi encrucijada es...

1-  En la misma área de pruebas volver a realizar el proceso de actualización, siempre intentando salvar las configuraciones de Gnome. Antes de actualizar esta vez desinstalaría kdebase y lo repondría posteriormente. Pero la verdad es que tampoco siento mucha seguridad de que las cosas sigan un curso distinto.

2- Realizar una instalación “fresh” de 9.04 respetando el /home, o sea las áreas de datos actuales y las configuraciones de usuario. Tendría que rehacer los usuarios y bancarme algunos toques de configuración. Probablemente pelear contra algún problemita nuevo que aparezca ¿Network Manager? El punto reside en que si el problema también se encuentra radicado en las configuraciones de usuario y de nuevo no las procesa bien, el proceso a la larga volvería a repetirse.

PD. Los pequeños problemas que había encontrado antes del desatre en principio eran tres. (1) Aptoncd desde los repos no funcionaba y a su vez el .deb de parche tenía dependencias imposibles de resolver por las versiones de Pyton. (2) La interface gráfica users-admin tampoco funcionaba. (3) Algunos errores loggeados durante el login de usuario que si aporta los puedo obtener.

Por supuesto que cualquier experiencia o idea es bienvenida y agradecida de antemano.

---

### Post by juancarlospaco on 2009-06-05
> **biale said:**
> 
2- Realizar una instalación “fresh” de 9.04 respetando el /home, o sea las áreas de datos actuales y las configuraciones de usuario. Tendría que rehacer los usuarios y bancarme algunos toques de configuración. Probablemente pelear contra algún problemita nuevo que aparezca ¿Network Manager? El punto reside en que si el problema también se encuentra radicado en las configuraciones de usuario y de nuevo no las procesa bien, el proceso a la larga volvería a repetirse.


**+1**
*Vos mismo tenes la Solucion* :D
NO tendrias que volver a rehacer los users si conservas el /home

---

### Post by Hei Ku on 2009-06-05
Mi pregunta sería por qué tenés dolphin, si usás Ubuntu, y no Kubuntu.

---

### Post by biale on 2009-06-05
juancarlospaco: ahora que lo decís, y al momento parece ser la mejor opción, si es que queda otra.

Hei Ku: en realidad Dolphin vino de yapa al instalar kdebase 3.5 sobre Ubuntu. Comence instalado sobre Gnome las típicas aplicaciones KDE de a una. Como tenía nostalgia de konqueror luego lo añadí a través de kdebase y el conjunto comenzó a funcionar mejor, o sea que faltaban paquetes. Pensé en borrar a dolphin, pero parece que no se lo puede retirar en forma separada. 

Para ambos, y de nuevo, muchas gracias por contestar.

---

