---
title: "Instalar PDT en Eclipse"
date: 2009-11-04
forum: Software
---

### Post by _miGue on 2009-11-04
Hola
Acabo de instalar Eclipse 3.5 y deseo instalar PDT para poder programar en PHP. Resulta que estoy siguiendo esta [guia]("http://wiki.eclipse.org/PDT/Installation") pero cuando voy ah instalar el PDT me sale lo siguiente:

```
Cannot complete the install because one or more required items could not be found.
  Software being installed: PHP Development Tools (PDT) Runtime Feature 2.2.0.v200910240541-7L7J-F8NcJKhTJcwK4wT (org.eclipse.php.feature.group 2.2.0.v200910240541-7L7J-F8NcJKhTJcwK4wT)

```Ojala me puedan ayudar

Gracias!

---

### Post by maxmoraga on 2009-11-06
Revisa si l aversion de eclipse que estas usando corresponde a la que el plugin requiere. en este caso es eclipse 3.5.

si eso esta bien,
Intenta isntalarlo manualmente.

1.- cierra eclipse.
2.- si no has modificado nada en ubuntu los plugins debieran estar en /home/user/.eclipse
3.- dentro de esa carpeta debiera haber otra similar a "org.eclipse.platform_3.5.0_1562511446", entra a esta carpeta y dentro encontraras varias carpetas, las importantes son features y plugins.
4.- ir a la url del plugin [http://download.eclipse.org/tools/pdt/updates/2.2/interim/]("http://download.eclipse.org/tools/pdt/updates/2.2/interim/") y descarga todo lo que este en features y plugins y copialo a las respectivas carpetas en la ruta mencionada previamente.
5.- inicia eclipse desde consola con eclipse -clean y revisa que los plugins esten funcioanando



Saludos y espero te sirva.

---

