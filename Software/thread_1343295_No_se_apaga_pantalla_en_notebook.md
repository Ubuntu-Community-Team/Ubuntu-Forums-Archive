---
title: "No se apaga pantalla en notebook"
date: 2009-12-01
forum: Software
---

### Post by luks911 on 2009-12-01
Siempre configuré el Gestor de Energía para que apagara la pantalla después de determinado tiempo. Siempre funcionó sin problemas, hasta Karmic.
Ahora tengo Karmic, instalado de cero y configuro el Gestor de Energía para que apague la pantalla después de 5 minutos de inactividad cuando está conectada a la electricidad y después de 1 minuto cuando está sólo con la batería (es en una notebook Dell Inspiron 1545), pero el sistema no hace caso. En lugar de apagarse la pantalla aparece un ícono del escritorio al lado del control de volumen y si dejo ahí el cursor aparece una advertencia (ver imagen adjunta) que dice "Sesión activa, sin inhibir, pantalla inactiva. Si puede ver este texto su servidor de pantalla está roto y debería notificárselo a su distribuidor. Para obtener más información consulte [http://blogs.gnome.org/hughsie/2009/08/17/gnome-power-manager-and-blanking-removal-of-bodges/](http://blogs.gnome.org/hughsie/2009/08/17/gnome-power-manager-and-blanking-removal-of-bodges/). Lo curioso es que a veces sí se apaga, aunque esto ocurre muy poco.
Estuve buscando y revisando el link del cartel, pero no llegué a nada: reportes de bugs con problemas parecidos aunque no iguales y no mucho más.
Si alguien tiene alguna idea o sugerencia, será bienvenida. Y pregunten si necesitan algún otro dato.

---

### Post by juancarlospaco on 2009-12-02
**xset dpms force off**

---

### Post by luks911 on 2009-12-02
Muchas gracias. Con ese comando la pantalla se apaga. Así que cree una combinación de teclas para llamarlo. Es un avance.
De todos modos, tengo que hacerlo en forma manual y el Gestor de Energía, bien, gracias :-P

---

### Post by juancarlospaco on 2009-12-02
Fijate que hay un lugar donde se ponen .sh que se ejecutan para apagar el sistema, 
podes poner ese comando ahi y problema resuelto, no recuerdo donde era puntualmente.
:)

---

