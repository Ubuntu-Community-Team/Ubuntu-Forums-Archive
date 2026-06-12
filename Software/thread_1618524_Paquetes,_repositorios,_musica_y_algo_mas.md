---
title: "Paquetes, repositorios, musica y algo mas"
date: 2010-11-10
forum: Software
---

### Post by Caikaku on 2010-11-10
Hola, soy usuario de Ubuntu hace bastante tiempo y tengo una pregunta respecto a los paquetes. Resulta que trabajo con sonido en edicion/grabacion. He probado Ardour y algunas apps mas y me parecen extraordinarias. He decidido mudar todos mis proyectos de Windows a Ubuntu y tener solo ese sistema. Ahora la pregunta es: ¿Como funcionan los repositorios y los paquetes? Veo casi imposible poder instalar Ardour, sino fuera por ellos. En Windows se descarga el .exe, se guarda y listo, queda disponible para otras instalaciones posibles. Salvo incompatibilidad al cambiar de version de Windows no hay problemas mayores.
Pero... en GNU/Linux? He visto que Ubuntu, saca una distro' cada 6 meses y ¿quien se encarga de que ardour este ahi disponible? Tambien utilizo plugins de ladspa para la edicion.
Bien, no quiero extenderme tanto, la cuestion en si es que me da "miedo" la migracion total de un sistema a otro por ese motivo de no saber hasta cuando aparecera el paquete que necesito en los repositorios. Ya que buscarlo por la web me parece una odisea.

---

### Post by Wiredfixer on 2010-11-11
Pues es algo que a muchos les pone a pensar, pero bien puedes hacer varias cosas:

- En la pagina oficial, te viene como instalarlo "from source" esto es, descargar los archivos que lo componen, cumplir con las dependencias e instalarlo con los pasos magicos en consola (configure, make, make install)

- La otra, es que al momento de descargar e instalar el paquete en tu PC, regularmente el archivo .deb queda en tu sistema, prueba a buscarlo y si mal no estoy se encuentra en /var/cache/apt/archives.

 Aun asi, mantenerte en base a Repositorios no es muy arriesgado, hay algunos repositorios independientes que manejan recopilaciones de software o software mejorado por ellos mismos en Launchpad.net, asi que es relativamente sencillo.

Por otro lado, puedes dedicar una PC para que sea un repositorio mirror, con APT-MIRROR puedes descargar (alrededor de 30gb) todo el repositorio de ubuntu al que acudes normalmente y tenerlo de manera local, actualizandose solo si lo requieres.

Saludos!!

---

### Post by biale on 2010-11-12
Ademas de lo que ya dijo Wiredfixer fijate que las versiones LTS duran 2 años.

Y en caso de emergencia hasta se podria pasar a otra distro.

De todas maneras, siempre existe el riesgo de que un proyecto de open source no siga y al momento no aparezca un reemplazo viable. 

En el peor de los casos hay tener en cuenta que una versión del sistema operativo que no se actualice tampoco necesariamente va a dejar de funcionar de un día para otro. Salvo que cambie el HW y etc. Pero para este tipo de casos tampoco el soft privativo garantiza nada.

---

