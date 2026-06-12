---
title: "Tip actualizacion Kubuntu 10.10 a 11.04 32 bits con plasmoid CWP 1.5.1"
date: 2011-05-07
forum: Software
---

### Post by guillermolisi on 2011-05-07
Al actualizar con Kpackagekit de Kubuntu10.10 a 11.04 una de las maquinas que suelo utilizar veo que el proceso aborto por problemas en los paquetes a gestionar.

Reinicio la maquina suponiendo que el problema estaba relacionado con Internet y que podria finalizar el upgrade luego de un obligado "sudo dpkg --configure -a" y me encuentro con la pantalla de incio (Plymouth) y un mensaje que dice "The disk drive for / is not ready yet or not present" con tres opciones: Esperar, Saltear (Skip) o ir al shell de mantenimiento (M).

Que paso aqui !?

Revisada la estructura del root filesystem con "e2fsck -cfD" de la particion que se monta en / y viendo que estaba todo bien, comienzo mi busqueda en Google sobre el tema encontrando muchos casos similares pero tambien con soluciones diversas para cada uno.

Luego de invertir varias horas buscando, leyendo y probando sin lograr una solucion, inicio con la opcion "M" para ir al shell de mantenimiento en modo monousuario, veo que la salida de "sudo dpkg --configure -a" me indica contenido inesperado en una linea del archivo /var/lib/dpkg/status.

La linea erronea correspondia al paquete del Customizable Weather Program (CWP) plasmoid. Sinteticamente la variable Priority estaba mal asignada. Tenia el valor "low" cuando deberia decir "optional".

Edite el archivo mencionado, modifique el valor de la variable y volvi a correr "sudo dpkg --configure -a" con buen resultado ya que finalizo instalando todos los paquetes que ya habian bajado.

Reinicie y volvio todo a la normalidad salvo que cuando quise terminar de actualizar otros paquetes, esta vez con Synaptic, me encuentro con elmismo error en la misma linea pero del archivo /var/lib/dpkg/available.

Volvi a editar y modificar el valor erroneo por el correcto y asi pude terminar una actualizacion completa quedando la maquina en excelentes condiciones y con un funcionamiento superior al que tenia con la 10.10

Hay [un thread sobre este asunto en KubuntuForums]("http://kubuntuforums.net/forums/index.php?topic=3116526.0"), por si quieren mas detalles.

---

