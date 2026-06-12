---
title: "[SOLUCIONADO] Problema para ver Video en Firefox"
date: 2009-06-07
forum: Software
---

### Post by RafaelG on 2009-06-07
Hola bueno navegando en internet con firefox tengo problemas para ver Videos, puedo ver video de Youtube pero en otras paginas no puedo ver los videos y como por ejemplo en emol.com los videos corren pero no tienen sonido,  si alguien tiene algun antecedente de lo que me pueda estar ocurriendo.

Sistema operativo: ubuntu 9.04
Notebook Dell 1510

eligonzalez@ergg:~$ lspci |grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
eligonzalez@ergg:~$ lsmod |grep drm
drm                    96296  3 i915
agpgart                42696  3 drm,intel_agp
eligonzalez@ergg:~$ lsmod |grep agp
intel_agp              34108  1 
agpgart                42696  3 drm,intel_agp

---

### Post by nopersona on 2009-06-07
Ya instalaste los extras restrictivos? si no es así, te dejo la lectura, y asegurate de instalar y activar el plugin de Flash. 

[http://ubuntulife.wordpress.com/2009/05/02/cosas-a-hacer-despues-de-instalar-ubuntu-904-jaunty-jackalope/](http://ubuntulife.wordpress.com/2009/05/02/cosas-a-hacer-despues-de-instalar-ubuntu-904-jaunty-jackalope/)

Sobre Flash

[http://www.tuxapuntes.com/drupal/node/1372](http://www.tuxapuntes.com/drupal/node/1372)

;)

---

### Post by RafaelG on 2009-06-07
Gracias Nopersona, el sugundo Link fue justo lo que necesita (Sobre Flash), tenia un conflicto  entre Flash y swfdec, desintale y instale desde consola y justo como la segunda opcion del tutorial sobre Flash, todo Perfect... gracias hasta la proxima

---

