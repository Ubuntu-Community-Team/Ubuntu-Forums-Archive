---
title: "¿Como se remplazan los iconos manualmente en hardy?"
date: 2008-06-03
forum: Software
---

### Post by pol666 on 2008-06-03
Hola recien estaba retocando unos iconos y quise tocar uno manualmente me di cuneta que Hardy es distinto a Gusty en cuanto a la gestion de iconos.

Ahora los icon themes estan organizados en escala de pixeles y antes no era asi... Antes era muy facil editar iconos manualmente pero ahora no se como hacer en que medida de iconos me meto para modificiarlos :s

---

### Post by _kAz_ on 2008-06-03
Yo no comprender... Quizás porque no tuve Ubuntu Gutsy sino Kubuntu. Pero en Hardy (ubuntu) se usa más el .svg

Si te referis puntualmente a reemplazar un determinado icono de un icon-theme tenés que crear uno con el mismo nombre que tiene el original. No se si estoy siendo muy claro, o más aún si entendí bien a lo que te referías.

Te cito mi caso, quizás te sirva. Instalé un tema nuevo (en .icons del home), pero si bien no era nada escueto el theme había algunos iconos que seguían siendo los default. Lo que tuve que hacer fue ir al /usr/share/icons, fijarme que nombre tenían los iconos que quería reeplazar, volver al .icons y hacer/enlazar el icono que yo quería con el nombre antes obtenido.

Ojalá te sirva de algo mi experiencia.

---

### Post by pol666 on 2008-06-03
exacto eso hacia pero ahora entro en la carpeta .icons y adentro estan los respectivos temas por ejemplo Oxy-Gnome. Entro ahi y hay un monton de carpetas con las resoluciones de los iconos :s

 y no se en que carpeta entrar, Antes en Gutsy no estaban esas carpetas

---

### Post by _kAz_ on 2008-06-03
Ahhh yo las ignoro a esas carpetas y voy derecho al "scalable", de ahi he cambiado todos los iconos ;)

Eso sí, procurá conseguir .svgs en lo posible porque esa sería la idea...

---

### Post by pol666 on 2008-06-03
a ver.... para por que no se si yo no entiendo lo que me decis o vos a mi.

Mira

[IMG]http://img362.imageshack.us/img362/6697/pantallazooxygnomenavegcl6.jpg[/IMG]


vos decis que entre a CUALQUIERA de esas y cambie el icono? ...eso hice y no funciono. Probe en 24x24

---

### Post by _kAz_ on 2008-06-03
Claaaaarooo... Con razón!!! A vos te falta en ese theme la carpeta "scalable", seguramente será cosa de ese tema...

Bueno, me retrotraigo entonces a mi experiencia Kubuntu donde cambié un gran porcentaje de los iconos de las aplicaciones.

Para cambiar UN icono tenés que cambiarlo en todas las resoluciones utilizadas. En el caso de Kubuntu 7.10, si mal no recuerdo, eran 16x16, 24x24, 32x32, 48x48, 64x64 y 128x128.

Así que agarrá el icono que quieras de 128x128, lo copias 5 veces más y lo reducis a los tamaños indicados. Creo que debería andar. Es poco probable que Ubuntu use las otras resoluciones (20x20 por ejemplo). Si ves que no te aparece nada, reduci el icono a TODAS las resoluciones. Es un laburo de mono, pero que yo sepa era la única forma.

Salu3.

---

### Post by pol666 on 2008-06-04
> 
Así que agarrá el icono que quieras de 128x128, lo copias 5 veces más y lo reducis a los tamaños indicados. Creo que debería andar. Es poco probable que Ubuntu use las otras resoluciones (20x20 por ejemplo). Si ves que no te aparece nada, reduci el icono a TODAS las resoluciones. Es un laburo de mono, pero que yo sepa era la única forma.

Salu3.


Demasiado laburo para un vago como yo. Ahora que me pongo a pensar. no hay forma de modificar un determinado icono desde la carpeta raiz por ejemplo alguna carpeta de iconos que se encuentre en /usr/ Capas que lo puedo hacer desde ahí

---

### Post by _kAz_ on 2008-06-05
> **pol666 said:**
> Demasiado laburo para un vago como yo. Ahora que me pongo a pensar. no hay forma de modificar un determinado icono desde la carpeta raiz por ejemplo alguna carpeta de iconos que se encuentre en /usr/ Capas que lo puedo hacer desde ahí

Probá... Buscá en /usr/share/icons, pero te advierto que era ahí donde yo reemplazaba los iconos en todas sus resoluciones. En realidad el .icons viene a ser un "atajo" para no tener que entrar como root cada vez que quieras instalar o modificar un paquete de iconos, ya que este aspecto no debería representar un riesgo para la seguridad.

Yo en Kubuntu tuve un rato largo hasta que me di cuenta que si no modificaba todas las resoluciones de cada icono no cambiaba nada. Te estoy tirando abajo :lolflag:, pero asi era; quizás tengás suerte y en ubuntu no sea tan así.

---

### Post by MeduZa on 2008-06-05
como dice kaz trata de trabajar con los escalables!

---

### Post by pol666 on 2008-06-05
mmm baje otro Icon theme y no estaba scalable ..en cualquier momento me voy a poner hacer un icon theme propio

---

### Post by EnriqueK on 2008-06-05
Para Gutsy estaba la aplicación **assogiate** que te permite reasignar íconos para documentos de cada tipo de aplicación, ahora si bien assogiate figura en los repositorios de Hardy, no funciona, así que el asunto viene por la nueva versión de Gnome que se está usando, por lo que los procedimientos usados en versiones anteriores, no son válidas para hardy, inclusive probé con usar iconos svg y no pasa nada, supongo que habrá que esperar a que se actualice Assogiate o que aparezca otro programa similar , habrá que estar atentos a GetDeb.

---

### Post by pol666 on 2008-06-05
> **EnriqueK said:**
> Para Gutsy estaba la aplicación **assogiate** que te permite reasignar íconos para documentos de cada tipo de aplicación, ahora si bien assogiate figura en los repositorios de Hardy, no funciona, así que el asunto viene por la nueva versión de Gnome que se está usando, por lo que los procedimientos usados en versiones anteriores, no son válidas para hardy, inclusive probé con usar iconos svg y no pasa nada, supongo que habrá que esperar a que se actualice Assogiate o que aparezca otro programa similar , habrá que estar atentos a GetDeb.

ahá viene por que Gnome modifico su gestor de iconos.. Ahora me callo la ficha de los tantos problemas que tuvo la gente cuando actualizo a HH que no se veian los iconos

---

