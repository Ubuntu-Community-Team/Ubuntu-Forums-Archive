---
title: "Error al instalar wine"
date: 2010-10-06
forum: Software
---

### Post by emiliano_raso on 2010-10-06
Resumo lo que me pasó:
- Estaba instalando Wine por medio del centro de software.
- Mi hermana me baja la tapa de la notebook.
- La notebook se suspende.
- La instalación se interrumpe.
- Vuelvo a querer instalar Wine por el centro de software y no me lo permite.
- Abro una consola, tiro "aptitude install wine" y me dice lo siguiente.


```
root@emiliano-laptop:/home/emiliano# aptitude install wine
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Leyendo la información de estado extendido      
Inicializando el estado de los paquetes... Hecho
Se configurarán los siguientes paquetes que están ahora parcialmente instalados:
  libmpg123-0 libopenal1 wine wine1.2 
0 paquetes actualizados, 0 nuevos instalados, 0 para eliminar y 0 sin actualizar.
Necesito descargar 0B de archivos. Después de desempaquetar se usarán 0B.
Escribiendo información de estado extendido... Hecho
Configurando libmpg123-0 (1.12.1-0ubuntu1) ...
dpkg (subproceso): no se puede ejecutar script post-installation instalado: Error de formato ejecutable
dpkg: error al procesar libmpg123-0 (--configure):
 el subproceso script post-installation instalado devolvió el código de salida de error 2
Configurando libopenal1 (1:1.12.854-0ubuntu1~lucid1) ...
dpkg (subproceso): no se puede ejecutar script post-installation instalado: Error de formato ejecutable
dpkg: error al procesar libopenal1 (--configure):
 el subproceso script post-installation instalado devolvió el código de salida de error 2
dpkg: problemas de dependencias impiden la configuración de wine1.2:
 wine1.2 depende de libmpg123-0 (>= 1.6.2); sin embargo:
 El paquete `libmpg123-0' no está configurado todavía.
 wine1.2 depende de libopenal1; sin embargo:
 El paquete `libopenal1' no está configurado todavía.
dpkg: error al procesar wine1.2 (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de wine:
 wine depende de wine1.2; sin embargo:
 El paquete `wine1.2' no está configurado todavía.
dpkg: error al procesar wine (--configure):
 problemas de dependencias - se deja sin configurar
No se ha escrito ningún informe de Apport porque el mensaje de error indica que es un error proveniente de un fallo anterior.
                                                                                                                             No se ha escrito ningún informe de Apport porque ya se alcanzado el nivel MaxReports
                                                    Se encontraron errores al procesar:
 libmpg123-0
 libopenal1
 wine1.2
 wine
E: Sub-process /usr/bin/dpkg returned an error code (1)
Un paquete no se pudo instalar. Intentado recuperarse:
Configurando libopenal1 (1:1.12.854-0ubuntu1~lucid1) ...
dpkg (subproceso): no se puede ejecutar script post-installation instalado: Error de formato ejecutable
dpkg: error al procesar libopenal1 (--configure):
 el subproceso script post-installation instalado devolvió el código de salida de error 2
Configurando libmpg123-0 (1.12.1-0ubuntu1) ...
dpkg (subproceso): no se puede ejecutar script post-installation instalado: Error de formato ejecutable
dpkg: error al procesar libmpg123-0 (--configure):
 el subproceso script post-installation instalado devolvió el código de salida de error 2
dpkg: problemas de dependencias impiden la configuración de wine1.2:
 wine1.2 depende de libmpg123-0 (>= 1.6.2); sin embargo:
 El paquete `libmpg123-0' no está configurado todavía.
 wine1.2 depende de libopenal1; sin embargo:
 El paquete `libopenal1' no está configurado todavía.
dpkg: error al procesar wine1.2 (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de wine:
 wine depende de wine1.2; sin embargo:
 El paquete `wine1.2' no está configurado todavía.
dpkg: error al procesar wine (--configure):
 problemas de dependencias - se deja sin configurar
Se encontraron errores al procesar:
 libopenal1
 libmpg123-0
 wine1.2
 wine
Leyendo lista de paquetes... Hecho                   
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Leyendo la información de estado extendido       
Inicializando el estado de los paquetes... Hecho

root@emiliano-laptop:/home/emiliano#
```


Como lo resuelvo?

Saludos gente!

EDIT: Traté de hacer "aptitude remove wine" pero tampoco funciona.

---

### Post by emiliano_raso on 2010-10-06
Otra cosa que hice y no funcionó:
- Abrí Synaptic
- Busqué "wine"
- Seleccioné todos lo paquetes que tenian el cuadradito en verde (instalados o algo asi)
- Elegí "Seleccionar para eliminar completamente".
- Terminó de hacer eso, y en una consola mandé "aptitude install wine"
- Descargó algunos archivos, pero de nuevo me devolvió el mismo texto de error que antes puse en el CODE.

---

### Post by emiliano_raso on 2010-10-07
Ya lo solucioné.

Pasos para solucionarlo:
- Ejecutar Synaptic
- Filtrar por WINE
- Marcar para desinstalar completamente todos lo que estén instalados (que tengan el recuadrito en verde)
- Despues de eso, mandé en consola "apt-get upgrade" y me marcó con que dos librerias tenia problemas, y estas eran "libmpg123-0" y "libopenal1"
- Las instalé de nuevo (porque removerlas no funciona tampoco) haciendo "aptitude install libmpg123-0" y "aptitude install libopenal1"
- Despues mandé un "apt-get upgrade" y no me marcó ningun drama, a lo cual le seguí con un
- aptitude install wine

Listo. Todo solucionado.

MORALEJA: Si están instalando aplicaciones, procuren no cortarle la corriente/suspender/hibernar/apagar/reiniciar/nada que se le asemeje a su computadora porque pueden mandarse macanas semejantes.
MORALEJA 2: Alejen a sus hermanas de las notebooks.

---

