---
title: "Totem reproduce sin audio."
date: 2009-07-24
forum: Software
---

### Post by bloodytanga on 2009-07-24
Mi problema es el siguiente: introduzco un DVD a la lectora que contiene varios episodios de una serie con menu y todo. Cuando lo pongo me aprecen las opciones de reproducir o grabar y elijo reproducir con el Totem. Cuando me lo abre el menú se inicia y puedo elegir los capítulos pero todo sin audio. es decir que puedo ver lo que hay en el dvd ero no puedo escucharlo. El DVD está en buen estado y antes de instalar ubuntu lo reproduje siempre sin problema.
Espero puedan ayudarme y mil gracias por estar ayudandome a iniciarme en ubuntu.

---

### Post by guillermolisi on 2009-07-24
Al margen de la cuestion especifica con Totem, te animas a probar el mismo DVD pero con VLC ?

Lo bajas e instalas desde los repos.

Por que la sugerencia ? Porque VLC (y posiblemente otros mas) actualmente son mejores reproductores que Totem.

---

### Post by luks911 on 2009-07-24
¿Es posible que te falten codecs? Probá instalando el paquete w32codecs. Pra eso, en una terminal:

```
sudo apt-get install w32codecs
```

Avisá por cualquier cosa.

---

### Post by bloodytanga on 2009-07-24
El paquete w32codecs no está disponible, pero algún otro paquete hace referencia
a él. Esto puede significar que el paquete falta, está obsoleto o sólo se
encuentra disponible desde alguna otra fuente

Eso me salta si pongo eso en la consola. Ahora pruebo bajando el vlc.

Actualizo: instalé el VLC y me andubo perfecto. Gracias de nuevo Guille. A vos luks también.

---

### Post by luks911 on 2009-07-24
> **bloodytanga said:**
> El paquete w32codecs no está disponible, pero algún otro paquete hace referencia
a él. Esto puede significar que el paquete falta, está obsoleto o sólo se
encuentra disponible desde alguna otra fuente

Eso me salta si pongo eso en la consola. Ahora pruebo bajando el vlc.

Proba con VLC. Y si querés, para instalar el paquete w32codecs agregá los repositorios de Medibuntu. Acá[0] cómo hacerlo. Si no entendés algo, preguntá. Con esos repos agregados, los actualizás (sudo aptitude update) y ahí sí instalás el paquete.

[0]https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories

---

### Post by aledruetta on 2009-07-24
> **luks911 said:**
> Proba con VLC. Y si querés, para instalar el paquete w32codecs agregá los repositorios de Medibuntu. Acá[0] cómo hacerlo. Si no entendés algo, preguntá. Con esos repos agregados, los actualizás (sudo aptitude update) y ahí sí instalás el paquete.

[0]https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories

Lo que te aconseja luks911 es muy conveniente si vas a trabajar con distintos formatos de video y multimedia en general. En google hay mucha información sobre "post-instalación de Ubuntu Jaunty". Te convendría seguir alguna de esas guías para dejar tu sistema más funcional.

---

### Post by bloodytanga on 2009-07-24
Instalé el medibuntu pero a la hora de instalar el win32 me da siempre el mismo error.

---

### Post by aledruetta on 2009-07-24
> **bloodytanga said:**
> Instalé el medibuntu pero a la hora de instalar el win32 me da siempre el mismo error.
¿te referís al paquete w32codecs, verdad?

Contanos qué versión de Ubuntu estás usando, qué procedimiento usaste para instalar los repositorios de Medibuntu y qué error te da la consola o Synaptic cuando querés instalar el paquete.

---

### Post by bloodytanga on 2009-07-24
Perdón me había olvidado de actualizar los paquetes antes de instalar el win32. Ya lo solucioné poniendo 
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

---

