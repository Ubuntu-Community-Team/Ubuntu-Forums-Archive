---
title: "[SOLVED] gnome-panel se reinicia"
date: 2009-08-17
forum: Software
---

### Post by josecuervo86 on 2009-08-17
Hola gente del foro. Tengo elsiguiente problemita, bastante raro por cierto. Sucede que gnome-panel se "reinicia" (se cierra y vuelve a abrirse) cada vez que quiero abrir un programa mediante el menú, pero me pasa especificamente con los de la categoria **Internet**. Tambien sucede lo mismo cuando quiero abrir el programa apretanto **Alt + F2**.
Espero ideas!

---

### Post by pablo.s on 2009-08-17
Pareciera que el menú tiene un
problema para mostrar un link y
aborta. Fijate que instalaste hace
poco que te haya cambiado el
menú.
Otra cosa que podes hacer es en
la configuración de menú, deshabilita 
el rubro "Internet" y fijate si sigue dando
problemas.

---

### Post by josecuervo86 on 2009-08-17
Mira Pablo, seguramente el problema viene porque ayer actualize a jaunty (la notebook es de mi vieja, si no ya lo tendria hace rato :P) asi que calculo que debe estar por ese lado. Cuando voy a aplicaciones y paso el mouse sobre cada una de las categorias no pasa nada, pero al llegar a internet crashea.

---

### Post by pablo.s on 2009-08-17
Otra cosa que podés hacer
es abrir una terminal, matar
gnome-panel, ejecutarlo y ver
que mensaje te devuelve.

Pensandolo bien, ese mismo 
consejo te lo podrias haber
dado vos mismo...

---

### Post by Mauro22 on 2009-08-17
Abrilo con la consola a ver que tira...

---

### Post by josecuervo86 on 2009-08-17
Ya lo intente, pero te dice que ya hay una funcionando. Probe matandola desde la terminal pero la levanta nuevamente.

---

### Post by pablo.s on 2009-08-17
Y si reinstalás gnome-panel?
No se regenera el menú
(teoricamente)?

---

### Post by josecuervo86 on 2009-08-17
Es lo proximo que voy a hacer. Estaba Googleando un poco y encontre reportes similares al mio, pero de hace 3 años y en Gentoo que misteriosamente se solucionaron. Veremos que pasa

---

### Post by pablo.s on 2009-08-17
Si no funciona con el
reinstall, probá con este
comando:

```
xdg-desktop-menu forceupdate
```

---

### Post by josecuervo86 on 2009-08-17
Ninguno de los dos funciono. Voy a seguir googleando a ver que encuentro. Igual sigo escuchando ideas!

---

### Post by josecuervo86 on 2009-08-17
Busque un poco, y encontre dos reportes en launchpad. Son viejos y **supuestamente** el problema esta resuelto. Ni idea por donde viene..

---

### Post by pablo.s on 2009-08-17
Que bueno que tuviste ese
problema porque estoy 
aprendiendo bastante sobre
la estructura de los menús
en GNOME.

---

### Post by guillermolisi on 2009-08-17
No lei nada al respecto pero sera que en el submenu Internet hay algun caracter que no interpreta bien y por eso se cae, algo que no sabe resolver bien y tira todo abajo ?

---

### Post by pablo.s on 2009-08-17
> **guillermolisi said:**
> No lei nada al respecto pero sera que en el submenu Internet hay algun caracter que no interpreta bien y por eso se cae, algo que no sabe resolver bien y tira todo abajo ?

Es lo que me parece a mi,
también. Por lo que estoy
averiguando el meú lo genera
XDG porque GNOME utiliza
la especificación de FreeDesktop.

---

### Post by josecuervo86 on 2009-08-17
Bueno, la parte del error causada por la sección internet se soluciono a partir de la sugerencia de Guillermo. Desmarque zimbra (que lo desinstale hace mucho, pero el lanzador seguia marcado) y dejo de crashear. Pero la debida a **Alt + F2** sigue dando problemas.

---

### Post by guillermolisi on 2009-08-17
> **josecuervo86 said:**
> Bueno, la parte del error causada por la sección internet se soluciono a partir de la sugerencia de Guillermo. Desmarque zimbra (que lo desinstale hace mucho, pero el lanzador seguia marcado) y dejo de crashear. Pero la debida a **Alt + F2** sigue dando problemas.
Alt+F2 no genera un cache con los ultimos comandos usados ? Si es asi, es altamente posible que haya heradado el problema tambien ahi.

---

### Post by pablo.s on 2009-08-17
Vas a tener que purgar Zimbra
de Synaptic, porque ha dejado
entradas del menú. Con Alt+F2
sale una lista de programas para
ejecutar y está causando el mismo
problema.

---

### Post by josecuervo86 on 2009-08-17
Muchachos, les debo una!=D>

Purgue zimbra y se termino el problema. La verdad es que estaba perdido.
Ya lo marco como [SOLVED]

Muchisimas gracias!

PD: Marcalo vos guille, porque yo no puedo :)

---

### Post by pablo.s on 2009-08-17
> **josecuervo86 said:**
> Muchachos, les debo una!=D>

Sanguche+Coca

---

### Post by josecuervo86 on 2009-08-17
> **pablo.s said:**
> Sanguche+Coca

Cuando vengas de visita a La Plata ;)

---

