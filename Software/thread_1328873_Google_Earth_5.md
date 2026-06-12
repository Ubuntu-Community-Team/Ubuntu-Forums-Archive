---
title: "Google Earth 5"
date: 2009-11-16
forum: Software
---

### Post by drazhe on 2009-11-16
Hola, instale el Google Earth 5 en mi Ubuntu Karmic como dice esta pagina

[http://eltoloza.wordpress.com/2009/11/04/instalar-google-earth-en-ubuntu-9-10-karmic-koala/](http://eltoloza.wordpress.com/2009/11/04/instalar-google-earth-en-ubuntu-9-10-karmic-koala/)

todo funciona perfecto, solo que el iniciador de APLICACIONES>INTERNET>GOOGLE EARTH no anda, y el programa solo arranca si le doy 

sudo googleearth

en la terminal... 

hay alguna manera de hacer que el iniciador funcione? y no tener que recurrir a la consola?

---

### Post by guillermolisi on 2009-11-17
Podrias indicar que directorios elegiste para su instalacion ?

Lo que mencionas tiene pinta de que hay problemas de permisos para tu usuario.

Siendo una aplicacion que interactua con el exterior/Internet, no recomiendo usarla con privilegios de root.

---

### Post by drazhe on 2009-11-18
yo deje todo como venia... como se donde instalo el programa?

---

### Post by josecuervo86 on 2009-11-18
Si es la instalación estadar seguramente se instalo en tu /home

---

### Post by Mauro22 on 2009-11-18
No importa donde se instala, el asistente genera un link simbolico entre 'googleearth' y la carpeta de instalacion.


los pasos son:

1) Bajar el .bin
2) chmod +x Googleearth.bin
3) ./Googleearth.bin
4) Siguiente, Siguiente, Siguiente, ;)
5) Se crea la entrada en el menu y se accede con 'googleearth'


NOTA: Si en algun paso se uso 'sudo' por ejemplo en el paso 2 o 3. GE se instala como root y no como el usuario.

---

### Post by drazhe on 2009-11-18
es lo que hice, y el iniciador de aplicaciones no anda, solo arranca el programa desde el terminal y con el commando sudo... sino no arranca... 


Copio parte del terminal
nicolas@nicolas-laptop:~$ googleearth
Warning: Unable to create symlink for lock '/home/nicolas/.googleearth/instance-running-lock'.  Permiso denegado.
nicolas@nicolas-laptop:~$ 

ahora, si pongo sudo googleearth ahi arranca el programa...

---

### Post by Mauro22 on 2009-11-18
Borra la carpeta .googleearth y volvelo a instalar

---

### Post by guillermolisi on 2009-11-18
> **drazhe said:**
> yo deje todo como venia... como se donde instalo el programa?
En donde vos le indiques en la ventana que te ofrece dos campos para configurar la instalacion (parece que este detalle paso desapercibido :D )

---

### Post by drazhe on 2009-11-19
> **Mauro22 said:**
> No importa donde se instala, el asistente genera un link simbolico entre 'googleearth' y la carpeta de instalacion.


los pasos son:

1) Bajar el .bin
2) chmod +x Googleearth.bin
3) ./Googleearth.bin
4) Siguiente, Siguiente, Siguiente, ;)
5) Se crea la entrada en el menu y se accede con 'googleearth'


NOTA: Si en algun paso se uso 'sudo' por ejemplo en el paso 2 o 3. GE se instala como root y no como el usuario.

Bueno, borreo la carpeta .googleearth de mi home y segui los pasos mencionados arriba, el programa se instala y arranca desde APLICACIONES>INTERNET>GOOGLE EARTH, pero no se conecta con el servidor... y la pagina de ayuda que me muestra, me recomienda desabilitar el contrafuegos...

---

