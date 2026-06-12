---
title: "Problemas al actualizar Lucid"
date: 2011-07-10
forum: Software
---

### Post by maghoxfr on 2011-07-10
Hola,

Hacía tiempo que no actualizaba el equipo y la actualización fue bastante larga (arriba de 100Mb). Ahora tengo un problema, un paquete roto. Siempre lo resolvía con los filtros de synaptic, pero ahora no puedo porque al abrir symaptic me salta este error:


> E: El paquete git necesita ser reinstalado, pero no se encuentra un archivo para éste.
E: Error interno al abrir el caché (1). Por favor informe de este error.

Recurrí a la terminal e hice

sudo apt-get install
 Pero me devolvió:
> Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
E: El paquete git necesita ser reinstalado, pero no se encuentra un archivo para éste.

Lo mismo para sudo apt-get -f install, sudo apt-get remove git...

Alguien sabe cómo solucionar esto? Muchas gracias.

---

### Post by guillermolisi on 2011-07-11
Que mirrors estas utilizando ?

Cambialos por alguno de otro pais, por ej. Brasil o el central (archive) y volve a probar despues de correr en una terminal/consola ```
sudo dpkg --confgure -a
```

---

### Post by maghoxfr on 2011-07-11
> **guillermolisi said:**
> Que mirrors estas utilizando ?

Cambialos por alguno de otro pais, por ej. Brasil o el central (archive) y volve a probar despues de correr en una terminal/consola ```
sudo dpkg --confgure -a
```

El tema es que para cambiar los mirror yo lo hacía desde synaptic pero no me deja entrar, me salta el error que posteé y al cerrarlo se cierra synaptic...

---

### Post by guillermolisi on 2011-07-12
Ok. Entonces hay que echar mano de un editor de texto simple y de la consola.

Con Alt+F1-6 (podes elegir cualquiera entre 1 y 6) abris una consola e inicias sesion con tu usuario, el mismo que utilizas para la sesion grafica y con la misma password.

Luego ingresas ```
sudo nano /etc/apt/sources.list
```y recorres el contenido de ese archivo borrando el subdominio que denota el pais de origen del mirror.

Por ejemplo, si tenias ```
deb http://ar.archive.ubuntu.com/ubuntu/ natty main restricted
```tenes que borrar "ar." con lo cual deberian quedarte lineas que digan ```
deb http://archive.ubuntu.com/ubuntu/ natty main restricted
```Guardas los cambios, luego en la misma consola corres ```
sudo dpkg --configure -a
```y si no te da error luego actualizas con ```
sudo apt-get update
```Tene en cuenta que cuando ingreses tu password en consola el cursor no se movera pero los datos ingresan.
Si todo anduvo bien, proba nuevamente con Synaptic y comenta que tal te fue.

---

### Post by maghoxfr on 2011-07-13
Cambié el servidor al de uruguay mediante sistema>otro software. Actualizó y me tiró el mismo error. Synaptic me sigue tirando el mismo error. Veo el sources.list que cambió efectivamente, pero ```
sudo dpkg --configure -a
```
Me da el siguiente error:
> dpkg: problemas de dependencias impiden la configuración de git-core:
 git-core depende de git (>> 1:1.7.0.2); sin embargo:
  El paquete `git' no está instalado.
dpkg: error al procesar git-core (--configure):
 problemas de dependencias - se deja sin configurar
Se encontraron errores al procesar:
 git-core
No se que hacer, la verdad necesito usar synaptic, quiero instalar sweet home 3D para un proyecto urgente (y no quiero hacerlo en windows!!!). El paquete de eeror es el "git-core".

Muchas gracias

---

### Post by gmunioz on 2011-07-13
**Intento de solución drástica**
Como la información de los paquetes instalados se guardan en el archivo:
/var/lib/dpkg/status
Edita el mismo ejecutando en una terminal:
sudo su
gedit /var/lib/dpkg/status
Busca la línea que menciona al paquete

Package: git-core
Status: install ok installed

Y dejas su status como install ok installed

O borras todas las líneas hasta el siguiente

Package: xxxxxxx-xxxxxx

---

