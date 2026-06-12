---
title: "Ares en Ubuntu 10.04"
date: 2011-06-26
forum: Software
---

### Post by chocheemedrano on 2011-06-26
Buenas,

He instalado* Ares* mediante *Wine*, pero al darle doble click al icono de *Ares*, se queda en la pestaña

*<Iniciando Ares>*

carga un poco, y luego se cierra esa pestaña y no abre el *Ares*..

Cuál es el problema?,

Gracias.

---

### Post by granjero on 2011-06-26
ejcutalo desde una terminal y posteá lo que salga....

salud!

---

### Post by chocheemedrano on 2011-06-26
Cuando lo estoy instalando;

```

err:ole:COMPOBJ_DllList_Add couldn't load in-process dll L"quartz.dll"
err:ole:CoGetClassObject no class object {cda42200-bd88-11d0-bd4e-00a0c911ce86} could be created for context 0x1
err:ole:COMPOBJ_DllList_Add couldn't load in-process dll L"quartz.dll"
err:ole:CoGetClassObject no class object {e436ebb2-524f-11ce-9f53-0020af0ba770} could be created for context 0x1
err:ole:COMPOBJ_DllList_Add couldn't load in-process dll L"quartz.dll"
err:ole:CoGetClassObject no class object {cda42200-bd88-11d0-bd4e-00a0c911ce86} could be created for context 0x1
err:ole:COMPOBJ_DllList_Add couldn't load in-process dll L"quartz.dll"
err:ole:CoGetClassObject no class object {e436ebb2-524f-11ce-9f53-0020af0ba770} could be created for context 0x1
chochemedrano@chochemedrano:~$ err:module:import_dll Library quartz.dll (which is needed by L"C:\\Archivos de programa\\Ares\\Ares.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Archivos de programa\\Ares\\Ares.exe" failed, status c0000135

```

Y cuando lo ejecuto mediante la terminal;

```

err:module:import_dll Library quartz.dll (which is needed by L"C:\\Archivos de programa\\Ares\\Ares.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Archivos de programa\\Ares\\Ares.exe" failed, status c0000135


```

---

### Post by guillermolisi on 2011-06-27
Que version de Wine estas usando ?

Tenes instalado Winetricks ?

---

### Post by mama21mama on 2011-06-27
Yo uso la red ares con una aplicación nativa para ubuntu.
Y me anda perfecto.

[http://mamalibre.xclan.ru/?q=content/instalar-ares-en-ubuntu-sin-wine](http://mamalibre.xclan.ru/?q=content/instalar-ares-en-ubuntu-sin-wine)

Te recomiendo la forma nativa.

---

### Post by chocheemedrano on 2011-06-27
> **guillermolisi said:**
> Que version de Wine estas usando ?

Tenes instalado Winetricks ?

1.2, creo que no tenía instalado el WInetricks.. veré si funciona, gracias ;)

El WineTricks para que sirve?

> **mama21mama said:**
> Yo uso la red ares con una aplicación nativa para ubuntu.
Y me anda perfecto.

[http://mamalibre.xclan.ru/?q=content/instalar-ares-en-ubuntu-sin-wine](http://mamalibre.xclan.ru/?q=content/instalar-ares-en-ubuntu-sin-wine)

Te recomiendo la forma nativa.

No entiendo de esa forma, pero gracias por tu aporte :p

---

### Post by guillermolisi on 2011-06-27
Agrega el repositorio de Wine-HQ e instala la version 1.3 junto con Winetricks.

Para ello podes usar Synaptic o la linea de comando en consola/terminal.
Mas informacion en detalle (en Ingles) en [http://www.winehq.org/download/ubuntu](http://www.winehq.org/download/ubuntu)

La version 1.3 es beta pero funciona muy bien y se actualiza bastante seguido.

Winetricks es una util herramienta para resolver algunas deficiencias funcionales en Wine respecto de ciertos programas para Windows.

---

### Post by chocheemedrano on 2011-06-27
Ya funcionó, pero ahora se queda en <Conectando>

---

### Post by guillermolisi on 2011-06-27
Posiblemente tengas que abrir algun puerto TCP en el firewall y/o router (dependiendo que tipo de conexion de red tengas para salir a Internet)

---

### Post by chocheemedrano on 2011-06-27
Wow, después de 5 minutos se conecto solo! muchas gracias carnal.

---

### Post by chocheemedrano on 2011-06-29
Solamente fue la primera vez, ya no se conecta :(

---

### Post by mama21mama on 2011-06-29
Proba con estos nodos....[http://mamalibre.no-ip.org/pub/update/ares/nodes](http://mamalibre.no-ip.org/pub/update/ares/nodes)
son los últimos a la fecha.

---

### Post by chocheemedrano on 2011-06-29
Gracias, funcionó ;)

---

### Post by chocheemedrano on 2011-06-30
Sigue siendo a la primera /:

---

