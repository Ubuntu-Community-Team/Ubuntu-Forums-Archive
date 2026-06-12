---
title: "Xubuntu muy lento (mas que un Win XP)"
date: 2010-08-18
forum: Software
---

### Post by labestiadelsur on 2010-08-18
Hola a todos. Tengo una compu AMD k6 con 380mb de Ram (mas o menos) que me trajeron para laburar con windows XP. Le instalé el Xubuntu desde Windows (con el wubi.exe) y andaba terriblemente lenta. Le instalé el entorno XLDE y no mejoró demasiado... En el monitor de recursos del sistema, el "historico del CPU" está siempre casi al 100% y el "historico de memoria e intercambio" no sube del 30%. la red anda bárbaro (descarga a 100kb contra 10kb con WWinXP). Les tiro estos datos como para dar pistas... me resisto a seguir con el XP!
En la pestaña que aparecen las aplicaciones, las ordeno por consumo de recursos del cpu y el que usa 45% es el gnome-system-monitor; luego puede aparecer el mozilla con 5% y el resto 1% o 0%.
Si alguien tiene claro qué cuerno pasa por favor... AYUDENME!! Gracias!

---

### Post by xangua on 2010-08-18
pistas¿ si no estamos jugando a las adivinanzas :S

si va lento hasta lubuntu seguramente es tu tarjeta grácifa, cuál es¿

y no se si aquí acepten ayudar pero también puedes probar los foros de [http://www.ubuntu-es.org/](http://www.ubuntu-es.org/)

---

### Post by harryscode on 2010-08-18
> **labestiadelsur said:**
> Hola a todos. Tengo una compu AMD k6 con 380mb de Ram (mas o menos) que me trajeron para laburar con windows XP. Le instalé el Xubuntu desde Windows (con el wubi.exe) y andaba terriblemente lenta. Le instalé el entorno XLDE y no mejoró demasiado... En el monitor de recursos del sistema, el "historico del CPU" está siempre casi al 100% y el "historico de memoria e intercambio" no sube del 30%. la red anda bárbaro (descarga a 100kb contra 10kb con WWinXP). Les tiro estos datos como para dar pistas... me resisto a seguir con el XP!
En la pestaña que aparecen las aplicaciones, las ordeno por consumo de recursos del cpu y el que usa 45% es el gnome-system-monitor; luego puede aparecer el mozilla con 5% y el resto 1% o 0%.
Si alguien tiene claro qué cuerno pasa por favor... AYUDENME!! Gracias!
Como te comentaron tendrías que dar más datos tecnicos para poder ayudar. Pero el uso alto del gnome-system-monitor siempre lo sufri en una pc con una tarjeta gráfica de 32mb, si haces el ejercicio de ver otra pestaña que no sea el gráfico de uso del cpu, seguramente vas a ver que cae el uso del mismo. Además habría que ver en que situaciones "anda lenta".. depende de que programas estas haciendo correr, por ejemplo, si queres usar Open Office, seguramente va a estar lento, igual si ves aplicaciones con flash en internet ..

---

### Post by biale on 2010-08-18
Para mi gusto un poco alto el swap. Lo seguiría con el comando "top" y la idea es que casi siempre muestre "0K used", porque donde empieza a barrer la performance se degrada mucho. La luz del HDD también es un indicador rápido del funcionamiento.

Además, con la máquina "en vacio", solo el escritorio, el uso de CPU debe caer muy cerca de cero. Si no es así hay que investigar donde esta el consumo espureo.

---

### Post by guillermolisi on 2010-08-18
Que placa de video estas usando ?

Otro tema para verificar con el comando top: cual es el proceso/servicio que realiza semejante consumo de procesador (sera Xorg ?).

---

### Post by Wiredfixer on 2010-08-19
La otra que podrias verificar es el estado de tu hardware..

El disco duro que tal anda? si hace uso de swap y el disco anda mal, puede que la cosa no le ayude mucho.

Tambien asegurate de que el procesador no este muy caliente, la optimizacion del hardware es escencial, detallitos..

---

### Post by Andyvec on 2010-08-21
Hola

Te voy a dar un consejo, no uses Xubuntu. Este sistema operativo suele ser más lento que el mismo Ubuntu, además utiliza más memoria para funcionar.

Acá hay algunas comparativas interesantes, algo viejas pero las venatjas ahora son incluso más grandes: [http://www.webupd8.org/2009/09/lubuntu-keeps-his-promise-fastest.html]("http://www.webupd8.org/2009/09/lubuntu-keeps-his-promise-fastest.html")

Se que empezó como un proyecto para computadoras antiguas, pero realmente se descarriló y hoy en día utiliza más recursos que el propio Ubuntu.

Si tu idea es tener Ubuntu en una máquina viejita, lo mejor es instalar Lubuntu, la gente de este proyecto si está haciendo las cosas bien, es sistema es muy completo, realmente consumo pocos recursos y cada vez tiene más usuarios.

Saludos

---

