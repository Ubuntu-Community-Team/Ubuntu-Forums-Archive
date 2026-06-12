---
title: "Error al abrir Google Earth"
date: 2009-09-06
forum: Software
---

### Post by ivisdrek on 2009-09-06
Hola a todos, he instalado Google Earth pero al intentar abrirlo me da ciertos errores.

Primero me aparece esto:

No se ha creado el directorio:
/root/.googleearth


Acepto y me aparece esto otro:


No se ha creado el directorio:
/root/.googleearth/Cache


Acepto y me aparece este aviso:

Google Earth no ha podido escribir en la caché actual o en la ubicación del archivo de Mis lugares. Los valores se definirán de la siguiente forma:
 Ruta a Mis lugares: "/home/lukyvis/.googleearth"
Ruta a la caché: "/home/lukyvis/.googleearth/Cache"

Cuando acepto finalmente se abre el programa, pero va lentísimo. ¿Alguien sabe cómo solucionar estos errores?


Gracias

---

### Post by jjgomera on 2009-09-06
Los errores que te da no son tales, simplemente que no lo estás ejecutando como administrador.
Que te vaya lento es normal si no tienes una buena tarjeta gráfica, ya que necesita aceleración 3D, ¿que tarjeta gráfica tienes? ¿¿tienes instalados los controladores propietarios?

abre una terminal y ejecuta glxgears, maximiza la ventana con engranajes que se abre y comprueba que valor te da, si es menor de 50 es norma que googleearth te vaya lento

Si usas compiz, prueba a desahilitarlo cuando vayas a ejecutar google earth

---

### Post by ivisdrek on 2009-09-14
Pues la verdad es que todavía no sé cómo instalar los drivers propietarios, voy a controladores de hardware pero no sé qué hacer. Tengo una ATI XPress 1200, creo que para ver Google Earth debería bastar.
En cuanto a ejecutar el programa como propietario, ¿a qué te refieres?

Gracias

---

### Post by Maciett on 2009-09-15
Hola

Lo que jjgomera te quiso decir es que lo ejecutes como administrador

$sudo googleearth

Y googleando encontré que tu tarjeta si tiene aceleración gráfica.

Así que tranquilo y prueba que tal va.

Saludos

---

### Post by jjgomera on 2009-09-16
> **Maciett said:**
> Hola

Lo que jjgomera te quiso decir es que lo ejecutes como administrador

$sudo googleearth

Para nada recomiendo que hagas eso, simplemenete digo que el programa intenta guardar los archivos de configuración en la cuenta del administrador y como no lo eres da ese aviso y los guarda en tu cuenta de usuario normal, no es un error, es un aviso, y desde luego yo lo olvidaría y no trataría de ejecutar googleearth (ni ningún otro programa) como root

---

### Post by ivisdrek on 2009-09-18
Bien, gracias, pero sí, entro en Googleearth como administrador. Creo que la cosa va a ser instalar los drivers propietarios. A ver si lo consigo.

Gracias. Un saludo.

---

### Post by unsalmd on 2009-10-07
this is [COLOR="Red"]english forum[/COLOR] of ubuntu not spanish!!!!!!

---

### Post by themasterdark on 2009-10-07
Si Unsalmd, pero estas en el apartado de Chile Team, asi que sin reclamos jaja, lo de la tarjeta ati, por que no pruebas con:

Sistema -> administracion -> controladores de hardware

deberia mostrarte que necesitas el driver de tu tarjeta, o que ya esta instalado.

Saludos.

---

### Post by ivisdrek on 2009-10-07
Hola Themasterdark, cuando voy a controladores de hardware no me aparece ninguna lista,me dice que no se están usando controladores privativos. ¿Cómo hago para activar los controladores privativos?

---

### Post by themasterdark on 2009-10-07
Estas seguro que tu tarjeta es una ati... jaja 
deberia aparecer en la lista...

mira escriba en una consola

> lspci |grep VGA

y escribe que es lo que te da.. para ver tu modelo de tarjeta de video.

---

### Post by ivisdrek on 2009-10-08
Me sale ATI Radeon Xpress 1200. Es una tarjeta integrada en la placa.

---

### Post by Carlos C on 2009-10-08
Creo que la confusión sobre los controladores de hardware se debe a que ivisdrek no ha mencionado cuál versión de Ubuntu está usando, algo que debe hacer cada vez que pregunta en el foro. En caso de ser Jaunty es perfectamente normal que no salga nada, corre con los drivers por defecto.

---

### Post by ivisdrek on 2009-10-08
Así es, la verdad es que no lo había especificado. Mi versión es la 9.04.

---

