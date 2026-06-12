---
title: "Problema de compiz y terminal gnome"
date: 2011-02-08
forum: Software
---

### Post by absalon.valdes on 2011-02-08
hola:

hace unos dias instale netbeans 6.9 en ubuntu 10.10. lo hice con el centro de software y no hubo ningun problema. pero luego, cada vez que inicio la consola (gnome-terminal) se desactivan los efectos de compiz. intente varias de las soluciones que encontre en google pero ninguna funciono. desinstalé temporalmente netbeans y deshice los cambios hechos en un archivo .conf de la instalacion de netbeans (cero aporte, se borro al desinstalar). pero aun asi sigue el problema. puedo ejecutar cualquier aplicacion, pero si inicio la consola se desactivan todos los efectos. alguien conoce alguna solucion a esto? o alguien sabe si aun puede quedar por ahi algun parametro de configuracion que no haya vuelto a su lugar? de antemano muchas gracias.

---

### Post by asterix77 on 2011-02-09
¿Como desintalastes netbeans también por el centro de software?

En particular cuando desinstalo un paquete prefiero hacerlo por la terminal,  específicamente si quiero borrar todo rastro de sus archivos de configuración ejecuto por la terminal, esto no se logra si es que lo haces desde el centro de software, tengo entendido que no, corriganme si no es así, al menos en synaptic no lo es.

$sudo apt-get purge nombredelpaquete.deb


Otra cosa, por lo general cuando instalas algo, se crea una carpeta oculta en tu /home/usuario

Tal vez sería bueno que busques si es que tienes una carpeta oculta que debiera llamarse mas o menos .netbeans  y borrarla (hacele un respaldo por si acaso).

Para el tema de compiz, y saber que error te arroja en forma más específica, al menos se me ocurre.

1) Matar compiz por la terminal o mas fácil con el monitor del sistema (Sistema--->Administración--->Monitor del sistema---->Procesos----->finalizar proceso)

2) Abrir una terminal y llamar a compiz

3) Aqui si no se puede ejecutar compiz, debiera arrojar algún tipo de error, y comenzar a buscar soluciones más especificas.


Saludos

---

