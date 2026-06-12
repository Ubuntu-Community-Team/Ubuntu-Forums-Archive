---
title: "Problemas generales en ubuntu Lucid"
date: 2010-06-16
forum: Software
---

### Post by Auringal on 2010-06-16
Hola gente, luego de una actualización comencé a notar cosas raras en mi sistema.
Por ejemplo Opera se me cerraba cuando quería descargar una imagen, cada vez que lo arrancaba me aparecía en ingles y al querer pasarlo de idioma se cerraba y así de modo que decidí usar firefox.

No obstante hay varias aplicaciones que dejaron de funcionarme o directamente no arrancan: Avidemux (GTK+). Vuze y otros

Incluso, al descargar un paquete .deb, veo que no se ejecutan y tengo que hacerlo mediante consola con dpkg -i

probe diferentes soluciones dadas en varios foros, instale paquetes sugeridos pero sigo con estos problemas

¿Alguna idea de lo que puede estar pasando?

cualquier otro dato que necesiten, me lo piden y s elos coloco

saludos y desde ya muchas gracias

---

### Post by emiliano_raso on 2010-06-16
Ah te pasaron todas!!! :P

Probaste reinstalar? Por ahi son fallos en la instalación.
A mi me pasó algo similar una vez que mientras instalaba cerré la tapa de la notebook, se suspendió y corto la instalación y despues retomó.
Ochomil errores tuve esa vez. Reinstalé de nuevo y andubo perfectamente.

Por ahi te falló en algo en el proceso de instalación:
- Mientras bajabas la .iso de Ubuntu alguna falla la dañó.
- Mientras grababas la .iso de Ubuntu en el CD alguna falla lo dañó.
- Mientras instalabas en disco, alguna falla te instalo las cosas mal.

O cualquiera de esas tres, o 2 juntas. O peor aun: Las tres. :P

Primero te recomiendo reinstalar. Si ya probaste reinstalar, te doy soluciones para algunos de los problemas:
- Para la instalación de paquetes .deb buscá en el Centro de Software de Ubuntu la aplicación gdebi e instalala. Esta aplicacion es la que ejecuta e instala automaticamente los .deb

Para las demas cosas no se. Te recomiendo actualizar el sistema:
```
sudo aptitude update && sudo aptitude full-upgrade
```

---

### Post by Auringal on 2010-06-16
Hola Emiliano, gracias por responder

No, aun no reinstale y quería ver si hay una solución ya que es molesto hacer backup de todo lo que tengo y partir de cero

el tema es que me andaba perfecto y en la ultima actualización me empezaron todos estos problemas

de última habrá que hacer tripas corazón,  formatear e instalar de cero

saludos

---

### Post by guillermon on 2010-06-19
> **Auringal said:**
> Hola Emiliano, gracias por responder

No, aun no reinstale y quería ver si hay una solución ya que es molesto hacer backup de todo lo que tengo y partir de cero

el tema es que me andaba perfecto y en la ultima actualización me empezaron todos estos problemas

de última habrá que hacer tripas corazón,  formatear e instalar de cero

saludos
Hola aurigal, si la solución sigue siendo hacer un backup y formaetar todo, te sugieros que esta vez consideres la posibilidad de hacer una partición para tu home, de forma que si te ocurre de nuevo, simplemente instales el sistema y conserves la configuración y los datos tuyos. Yo actualmente me lleva hacer una instalación limpia no más de una hora... solo hay que tener en cuenta un par de cosas antes de hacerlo. Si necesitas ayuda no dudes en pedirla. saludos
Guillermo

---

### Post by Auringal on 2010-06-19
> **guillermon said:**
> Hola aurigal, si la solución sigue siendo hacer un backup y formaetar todo, te sugieros que esta vez consideres la posibilidad de hacer una partición para tu home, de forma que si te ocurre de nuevo, simplemente instales el sistema y conserves la configuración y los datos tuyos. Yo actualmente me lleva hacer una instalación limpia no más de una hora... solo hay que tener en cuenta un par de cosas antes de hacerlo. Si necesitas ayuda no dudes en pedirla. saludos
Guillermo

hola Guillermon, gracias por responder

por lo que veo no me quedará otra que hacer instalación limpia. Lo de la partición  del home es una excelente idea, nunca la puse en práctica en mis inicios en Ubuntu por falta de experiencia en linux, y posteriormente no la utilicé porque tengo un disco esclavo de 500 gigas donde guardo prácticamente todo lo que descargo documentos y demás cosas. Utilizo pocas aplicaciones fuera de las que instala el sistema y y guardo las carpetas del home para cuando reinstalo nuevas versiones (por ej basket que utilizo mucho). Navegador uso Opera que me sicroniza prácticamente todo (chrome lo hace ahora también por suerte)y uso muschas cosas en la red (nube) pero me interesaba saber que cuernos había pasado, porque todo me andaba de maravilla hasta la actualización que me embarro todo.

Además debo decir que ubuntu me esta dejando de gustar. creo que le están metiendo demasiadas cosas y variando muchas que lo hacías particularmente atractivo. Yo me inicie con la 7.04 que me en-can-to. A partir de la 8.04 que fue la siguiente que use, siempre he tenido un problema aquí u otro allá. Ultimamente veo que cada vez exige mas recursos y la noticia que a partir de Maverik mi maquina no sera del todo apta...no se.

Tengo ganas de probar openSUSE porque veo que Ubuntu cada vez es mas pesado, con mas fallas y digamos que, sustancialmente, sigue siendo lo mismo, pero con mas dolores de cabeza

saludos

---

