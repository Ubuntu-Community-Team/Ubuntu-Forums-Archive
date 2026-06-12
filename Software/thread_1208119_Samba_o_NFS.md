---
title: "Samba o NFS?"
date: 2009-07-08
forum: Software
---

### Post by ado@linux on 2009-07-08
El título del post puede llevar un poco a la confusión, pero no ando muy creativo hoy. Más que una pregunta, necesito un poco de ayuda.

Tengo 3 compus en red, y la "grande", la que debería servir archivos y esas cosas no lo hace como debería.

Por algún motivo mis shares SAMBA no funcionan. No se puede acceder al listado de recursos compartidos desde la red. Reinstalar SAMBA sólo me permitió volver a tener un servidor funcional durante un día. Reinicio y chau.

Escenario:

3 equipos en red, 2 notebooks por aire y una desk cableada.
Desde la desk puedo acceder los shares en las notebooks, pero NO al revés.
MT-DAAPd está corriendo sin problemas en la desk. Los equipos se "ven" en la red.

Creo que podría reemplazar SAMBA por NFS, pero no tengo la más peregrina idea de como lo haría. Como no hay compus con Win, perder la compatibilidad con la ventana no es un problema.

Gracias!

---

### Post by guillermolisi on 2009-07-08
> **ado@linux said:**
> El título del post puede llevar un poco a la confusión, pero no ando muy creativo hoy. Más que una pregunta, necesito un poco de ayuda.

Tengo 3 compus en red, y la "grande", la que debería servir archivos y esas cosas no lo hace como debería.

Por algún motivo mis shares SAMBA no funcionan. No se puede acceder al listado de recursos compartidos desde la red. Reinstalar SAMBA sólo me permitió volver a tener un servidor funcional durante un día. Reinicio y chau.

Escenario:

3 equipos en red, 2 notebooks por aire y una desk cableada.
Desde la desk puedo acceder los shares en las notebooks, pero NO al revés.
MT-DAAPd está corriendo sin problemas en la desk. Los equipos se "ven" en la red.

Creo que podría reemplazar SAMBA por NFS, pero no tengo la más peregrina idea de como lo haría. Como no hay compus con Win, perder la compatibilidad con la ventana no es un problema.

Gracias!
Si no hay ni pensas tener compatibilidad con Windows en red, se impone NFS por mucho.

Esa maquina "grande" bien podria ser el servidor NFS que publicara sus recursos para que las otrs maquinas los usen, montandolos como si fueran particiones nativas/propias.

Pero si con esto no alcanza porque los recursos a compartir y usar estan en todas y cada una de las maquinas de esa red, cada una puede ser a la vez cliente y servidor NFS.

Para tener una introduccion y algo mas en el tema de como instalar y configurar en forma razonablemente sencilla, podes darle una leida a un tutorial publicado en el sitio web de Ubuntu-ar ubicado en [http://ubuntu-ar.org/node/208](http://ubuntu-ar.org/node/208)

Si bien habla de 8.04 y 8.10, en general es aplicable practicamente a cualquier version conocida a la fecha.

Luego y con la red en marcha, podras leer en mas detalle otros articulos, manuales, etc. para profundizar y mejorar lo que lograste.

---

