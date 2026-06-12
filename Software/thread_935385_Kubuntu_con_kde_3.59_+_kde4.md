---
title: "Kubuntu con kde 3.59 + kde4"
date: 2008-10-01
forum: Software
---

### Post by luchardi on 2008-10-01
Gente,

Volví a mis fuentes y quería usar un poco kde 3.5.9 antes que la mayoría de las distros la discontinuen, y demás instalé kde4 de los repos de kubuntu 8.04.1 que es 4.0.3.

Ahora bien, funciona bien, bah bien, digamos "bien" ... igual que siempre.

Lo unico que me pasó que cuando inicio kde4 las ventanas quedan con la decoración de "keramik" que es la que uso en kde3 y si entro al Settings manager, dice que use la de kde4 pero sigue prevaleciendo la de kde3.

Esto se da porque uso el mismo usuario? 
Sabe alguien como solucionarlo?

Gracias!

---

### Post by guisheca on 2008-10-01
Usas compiz-fusion?? porque por alguna extraña razón cuando usas compiz-fusion en kde4 y no tenés emerald, es decir, que usas el decorador de ventanas de kde, te pone la decoración que usas en kde3.
Y cuando digo alguna extraña razón me refiero a que no se como ****** solucionarlo XD.
Saludos.

---

### Post by Hei Ku on 2008-10-01
No uses compiz fusion en kde4. :D

Y lo digo en serio. Los mismos efectos te los provee kwin, asi que chocan. El diseño de compiz y kwin es muy diferente, asi que es natural que tengan problemas.

---

### Post by pol666 on 2008-10-01
Podes usar Compiz pero desactiva Kwin.

depende que importancia le des a los efectos.... Kwin esta lindo, pero le falta mucho para parecerse a commpiz

---

### Post by guisheca on 2008-10-01
El problema que le veo a kwin en kde4 es que los mismos efectos que hay en compiz andan mas lento, es decir, necesitan de mas capacidad de proceso. Lo mismo pasaba con compiz-fusion me acuerdo, cuando estaba en etapa muy temprana de desarrollo lo probé con una compu algo viejita y me andaba lento, pero en cuanto estuvo mas desarrollado lo probé de vuelta, con la misma máquina, y me parecía incluso mas liviano que beryl.

---

### Post by luchardi on 2008-10-01
Actualizo, no uso Compiz, a nivel efectos esta OUT OF THE BOX la instalación.

Alguna idea?

---

### Post by leo_rockway on 2008-10-01
4.0.3 es vieeejo ya, quizás tu problema ya está solucionado.

¿No había nightlies para KDE4 en Kubuntu?

---

### Post by guisheca on 2008-10-02
Probá hacer alt+F2 y escribí kde4-window-decorator a ver que pasa, es obvio que entra con el decorador de kde3, capas eso lo resuelve.

---

### Post by luchardi on 2008-10-02
> **guisheca said:**
> Probá hacer alt+F2 y escribí kde4-window-decorator a ver que pasa, es obvio que entra con el decorador de kde3, capas eso lo resuelve.

Lo pruebo esta noche y te confirmo, gracias.


leo_rockway, kde 4.0.3 es el unico kde4 que esta en los repos de kubuntu 8.04.1, igualmente probé kde4.1 en la LiveKde de Fedora 10 Beta y no lo ví TAN cambiado. Para mí aún le falta muchísmo para llegar a la funcionalidad del 3.x.

---

### Post by guisheca on 2008-10-02
Los repos para la 4.1.1 están en la página de [kubuntu.org]("http://www.kubuntu.org/") y realmente hay direfencia entre kde4 y kde4.1.1.
O sea, hay diferencia en cuanto a estabilidad mas que nada, pero en novedades también.
Ojo, que el paquete gtk-qt-engine (o algo así) se va al ****** y si también tenés kde3 la aplicaciones gtk+ se van a ver mas feas que la cara de Stallman por la mañana después de una noche de parranda.

Para los que no quieren buscar les dejo los repos directamente:

```
http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu hardy main
```

Saludos.

---

### Post by luchardi on 2008-10-02
> **guisheca said:**
> Probá hacer alt+F2 y escribí kde4-window-decorator a ver que pasa, es obvio que entra con el decorador de kde3, capas eso lo resuelve.

No tengo ningun comando valido para kde4-w *, seguramente es por eso.
Voy a probar actualizando con el repo q pusiste debajo y te confirmo.

---
Edit
---

Mejoro bastante kde4.1.2 que es el que me instale desde los repos, pero igualmente kde4-window-decorator no existe como comando.

Sigo con Keramik aunque no me molesta, algo que si mejoro mucho es el scroll en las paginas web! barbaro!!!

---

