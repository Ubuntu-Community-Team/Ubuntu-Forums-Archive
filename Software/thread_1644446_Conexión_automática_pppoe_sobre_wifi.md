---
title: "Conexión automática pppoe sobre wifi"
date: 2010-12-13
forum: Software
---

### Post by asterix77 on 2010-12-13
Al encender mi notebook con lucid, este se conecta a mi AP, pero sin embargo es incapaz de acceder a internet, cada vez debo recurrir a la terminal y correr pppoeconf, indicar luego nombre de usuario y contraseña.
 
¿existe alguna forma de dejarlo automáticamente?. Debiera existir, ya que antes de reinstalar lucid, esta se hacía en forma automática al encender mi notebook.
 
 
Saludos

---

### Post by Lutho on 2010-12-13
crear un script con la sentencia de conexión para que se ejecute al inicio.

---

### Post by RafaelG on 2010-12-13
Asterix77,

El Encryption key te otorga esa cualidad tengo entendido.

Saludos cordiales,

---

### Post by asterix77 on 2010-12-13
Lo que no entiendo es porqué al reinstalar lucid me apareció el problema, ya que antes de hacerlo se conectaba en forma automática. La verdad es que reinstalé lucid porque quice reestructurar mi disco duro; lo particioné en dos, en una partición dejé mi home, y en el otro mi directorio raiz (antes lo tenía en uno solo, y cada vez que actualizaba tenía que respaldar mi home).
 
 
Voy a probar con algún sccript que se ejecute al inicio a ver si funciona.
 
Con respecto a la encription key ¿eso significa modificar la configuración de mi ap?.
 
Saludos

---

### Post by RafaelG on 2010-12-13
> **asterix77 said:**
> 
Con respecto a la encription key ¿eso significa modificar la configuración de mi ap?.

No necesariamente tienes que modificar tu AP. Consulta, el sistema te solicita contrasena para ingesar al anillo de seguridad?

Saludos,

---

### Post by asterix77 on 2010-12-14
Si Rafael, lo hace.
 
 
Saludos

---

### Post by moreback on 2010-12-16
Podrías probar borrando la conexión y creándola de nuevo. Creo que puede ser problema del Network-Manager con versiones de configuración viejas.

---

### Post by asterix77 on 2010-12-17
En realidad, el tema de redes en mi notebook, lo manejo con wicd porque uso bastante wifi; y no la pude hacer andar con en NM por lo que instalé wicd con lo que solucioné el problema en forma inmediata. El problema es que cuando hice eso usaba karmic, y al instalar wicd automáticamente me desinstalaba el NM por temas de compatibilidad.
 
Luego hice la actualización a lucid vía internet, conservando todos mis programas instalados en karmic (para ello usé dpkg --get-selections).
 
Ahora bien hice un apt-get install network-manager, y para mi sorpresa no me desintaló wicd (como me ocurría en karmic). Lo que hice fue crear una conexión con NM, y pedirle que me guarde la configuración y la conexión automática.
 
 
No es una manera muy elegante, pero al menos en las 3 pruebas que hice, se conectó a internet (vía wifi) automáticamente en cada reinicio (aunque se conectó usando wicd y no sé porqué).
 
 
Solo espero que se siga conectando en forma automática, voy a probar por un tiempo, y si no tengo problemas, posteo de nuevo para dar por solucionado el tema.
 
 
 
Saludos y gracias.

---

### Post by asterix77 on 2010-12-19
Bueno, no he vuelto a tener problemas con mi conexión, así es que lo doy por solucionado.


Saludos

---

