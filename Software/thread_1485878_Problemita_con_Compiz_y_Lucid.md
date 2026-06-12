---
title: "Problemita con Compiz y Lucid"
date: 2010-05-17
forum: Software
---

### Post by SSNova on 2010-05-17
Hola A todos

  Hace poco hice una instalación desde cero de Lucid y al reistalar todo los programas, noté que en el CCSM de compiz no figura la capa de widget. Estuve googleando un rato pero no logré encontrar ninguna solución. Alguien tuvo este problema o tiene alguna solución?. Gracias por adelantado

---

### Post by eliux on 2010-05-18
Hola, dentro de los repositorios synaptics busca compiz plugins o add-ons no me acuerdo bien, y te agrega mas efecto y si no me confundo aparecen los widgets, tenes instalado el compiz control manager???
 
Un consejo pasa los servidores repositorios de argentina a servidor global (si es que sos de argentina) luego abrite un terminal y ejecuta 
 
sudo apt-get update
 
Despues de esto busca dentro de los paquetes synaptics lo que te dije anteriormente, espero que te ayude!
 
 
Encontre esto tambien,
te agrega muchos plugs no oficiales, no los probe y no se si andan bien.
 
sudo aptitude install compiz-fusion-plugins-unofficial
 
fuente: [http://tuxpepino.wordpress.com/2007/07/09/mas-plugins-para-compiz-fusion/](http://tuxpepino.wordpress.com/2007/07/09/mas-plugins-para-compiz-fusion/)
 
Y hay una distro llamada COMFUSION basada en ubuntu, tiene todos los efectos de beryl, compiz e infusion, muy buena distro y desquiciada de efectos! si queres podes probarla [http://comfusion.es/descargas/](http://comfusion.es/descargas/)

---

### Post by SSNova on 2010-05-21
Muchas gracias eliux, ahora tengo todo funcionando. Saludos

---

### Post by eliux on 2010-05-26
Una cosita mas que me olvide de decirte, dentro de synaptics buscas compiz y busca uno que dice compiz-fusion-plugins-extra los instalas, dentro de administracion-->compiz manager vas donde dice add-ons (es una avioncito de papel) y le das a activar y listo, no se si eso lo puse antes saludos!

---

