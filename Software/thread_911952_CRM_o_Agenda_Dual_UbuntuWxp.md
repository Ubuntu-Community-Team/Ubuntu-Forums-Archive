---
title: "CRM* o Agenda Dual Ubuntu/Wxp"
date: 2008-09-06
forum: Software
---

### Post by FighterPepe on 2008-09-06
CRM* o Agenda Dual Ubuntu/Wxp

Me interesaría un software que pudiera mantener datos en común en una partición NTFS que funcionara desde ambas plataformas.

Basicamente se trata de una agenda para seguimiento de tareas y citas. 
Tomboy se adapta como organizador, pero no controla citas y he localizado que tiene un pie en ambos mundos y los datos en ambos. 

Existe algo así ?

Gracias

*CRM Customer Relationship Management (software de control de relaciones con los clientes)

---

### Post by Hei Ku on 2008-09-06
Por lo que sé, KMail, y toda la suite de KDE PIM son multiplataforma. Pero no tengo idea cómo se instalan en Windows.

---

### Post by FighterPepe on 2008-09-06
Voy a echar un vistacito. Uno de ellos parece un gestor de correo.

Ni uno ni otro están referenciados para funcionar bajo Windows.

---

### Post by Hei Ku on 2008-09-06
La otra opcion es utilizar Thunderbird junto con la extension de calendario, creo que se llama Firebird.

O usar un CRM en toda la regla, pero me parece que lo que estas buscando es algo mas personal, combinacion de agenda y correo nomas.

---

### Post by FighterPepe on 2008-09-06
Yo utilizo un CRM con más de 150.000 registros sólo para windows : Goldmine. 

He localizado Sunbird y estoy en pruebas con él para tareas y citas simples puede valer. 


Una pregunta : ¿ Utilizas máquinas virtuales ?

Sabes si wine, virtual pc o virtual , Virtual Box permiten fijar un disco de datos externo al entorno que crean ?

---

### Post by faktorqm on 2008-09-08
> **FighterPepe said:**
> Yo utilizo un CRM con más de 150.000 registros sólo para windows : Goldmine. 

He localizado Sunbird y estoy en pruebas con él para tareas y citas simples puede valer. 


Una pregunta : ¿ Utilizas máquinas virtuales ?

Sabes si wine, virtual pc o virtual , Virtual Box permiten fijar un disco de datos externo al entorno que crean ?

no uso maquinas virtuales. wine no es una maquina virtual. si permiten "fijar" (¿montar?) una particion externa al entorno que crean...

---

### Post by vk-cdg on 2008-09-08
> **FighterPepe said:**
> CRM* o Agenda Dual Ubuntu/Wxp

Me interesaría un software que pudiera mantener datos en común en una partición NTFS que funcionara desde ambas plataformas.

Basicamente se trata de una agenda para seguimiento de tareas y citas. 
Tomboy se adapta como organizador, pero no controla citas y he localizado que tiene un pie en ambos mundos y los datos en ambos. 

Existe algo así ?

Gracias

*CRM Customer Relationship Management (software de control de relaciones con los clientes)


Yo después de probar y usar varios productos (tanto en casa como en el trabajo) tengo Ubuntu y Windows, finalmente me cambié a Google calendar. Me cansé de tener copias duplicadas, archivos corruptos y cosas visibles desde un lado y no desde otro. No encontré nada que me permita finalmente trabajar desde cualquiera de los dos SO sobre los mismos datos.
Google calendar te envía las alertas por mail sin necesidad de tener la "agenda" abierta.

---

### Post by FighterPepe on 2008-09-08
> **faktorqm said:**
> no uso maquinas virtuales. wine no es una maquina virtual. si permiten "fijar" (¿montar?) una particion externa al entorno que crean...

Es una gran noticia faktorqm. 

Gracias

---

### Post by FighterPepe on 2008-09-08
> **vk-cdg said:**
> Yo después de probar y usar varios productos (tanto en casa como en el trabajo) tengo Ubuntu y Windows, finalmente me cambié a Google calendar. Me cansé de tener copias duplicadas, archivos corruptos y cosas visibles desde un lado y no desde otro. No encontré nada que me permita finalmente trabajar desde cualquiera de los dos SO sobre los mismos datos.
Google calendar te envía las alertas por mail sin necesidad de tener la "agenda" abierta.

Leído alto y claro. Es una opción muy a tener en cuenta. 

Una pregunta : cuando tuviste problema era cuando Linux no leía perfectamente las particiones NTFS. Porque ahora yo leo muy bien archivos. Y con ext2ifs leo muy bien desde windows hacia Linux, aunque de forma mucho más limitada. 

La idea era que los datos estuvieran en una partición ntfs leible por ambos sistemas. 

Gracias

---

### Post by vk-cdg on 2008-09-10
No, el problema es que el Lightning guarda los datos dentro del pefril del Thunderbird y a menos que configure un perfil en otra partición, que sea visdo desde windows y linux no camina. 
Hacer esto último no me deja del todo tranquilo ya que mis carpetas locales suman mas de 4Gb de correos de hace casi 9 años, con mas de 10 cuentas de correo (soy webmaster de un club de autos)!

Otros soft que estuvieran para ambas plataformas no encontré, así que finalmente.... me entregué una ves mas a Google.

---

### Post by EnriqueK on 2008-09-11
Con el Sunbird se puede sincronizar perfectamente los datos en ambos sistemas operativos, en realidad es muy simple el asunto, deja la instalación de Xp como base , luego entras al perfil de Sunbird en Ubuntu situado en  la carpeta de usario dentro de la carpeta oculta  .mozilla , navegas hasta encontrar los archivos o carpetas representativos y los borras , seguidamente en ese mismo lugar creas enlaces simbólicos que apunten a esos mismos archivos o carpetas del profile en Xp, de aquí se desprende que si o si la partición de Xp la debes tener montada en todo momento, por esta razón yo prefiero usar las versiones portables tanto de Firefox, Thunderbird y de Sunbird con lo que solo debo mantener montada la partición donde coloqué esos programas portables y aún así puedo mantener sincronizados todos estos programas entre Xp y Ubuntu.
La razón de poner a la instalación de Xp como base o de referencia, es simplemente por que no se puede usar como base la de Ubuntu  por que los enlaces directos de windows no tienen la misma potencia digamos así que los enlaces simbólicos de Linux.

---

### Post by FighterPepe on 2008-09-11
Hay alguna manera, en la entrada en Ubuntu, de que se monte la unidad compartida ?

Muchas gracias

---

### Post by EnriqueK on 2008-09-12
La forma mas simple de lograr montar una partición desde el arranque es usando el programa "Disk Manager", no se encuentra en repositorios , pero lo puedes bajar dede la página del proyecto.
  [http://flomertens.free.fr/disk-manager/download.html](http://flomertens.free.fr/disk-manager/download.html)
Allí no figura un ,deb para Hardy, pero el que figura para Feisty sirve perfectamente.
Por otra parte, no se si entendí, pero estoy casi seguro que Sunbird no permite redirigir su carpeta de archivos a otra partición que podrías hacer común entre ambos sistemas operativos, tal como se puede hacer en Thunderbird, pero eso realmente no es necesario usando enlaces simbólicos en la carpeta de configuración de Sunbird de Ubuntu , tal como lo expliqué antes.
La forma mas imple que se me ocurre que podrías lograr lo que quieres, es instalar **Sunbird portable** , esta versión la podés correr en Ubuntu mediante Wine y así te evitás estar creando enlaces simbólicos y como yapa en cualquier momento la copías a un pendrive y te la llevás a cualquier otro equipo.

---

### Post by FighterPepe on 2008-09-12
Me llevo la información como oro en paño. Todavía soy bastante novato en Linux, pero me pondré a profundizar. 

Muchas gracias

---

