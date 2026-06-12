---
title: "Compartir archivos Ubuntu/XP"
date: 2009-01-01
forum: Software
---

### Post by benjamin_linux on 2009-01-01
Hola a todos

(y feliz año nuevo!! :D)

Acabo de cambiar mi ex router Noganet por un Linksys WRT54G2 y quiero, de una vez por todas, compartir carpetas/archivos entre mi laptop y mi pc de escritorio (de mi familia, con XP). El estado de la conexión es:

internet > router > pc (cable)
                    laptop (wifi)

Disculpen si ya se posteó o es muy fácil de hacer, he encontrado como compartir una conexión pero no archivos/carpetas...

Gracias y de nuevo, feliz año :)

---

### Post by Hei Ku on 2009-01-01
Está en los tutoriales de ubuntu-ar, además de varios threads en este y otros foros.

[http://ubuntu-ar.org/tutoriales/samba](http://ubuntu-ar.org/tutoriales/samba)

Feliz Año!

PD: Movido a Software

---

### Post by benjamin_linux on 2009-01-01
Sabía que tenía que estar en todos lados, 

muchíiiiisimas gracias Hei Ku

---

### Post by benjamin_linux on 2009-03-25
Refloto este post de la nada...

Finalmente (estoy sin mucho tiempo) me puse a ver si podía poner las máquinas en red. Estuve un buen rato hasta que logré que Windows si quiera me reconociera el grupo de trabajo. Y desde Ubuntu, Red > Red de Windows veo la PC de escritorio en la que tengo Win, pero cuando quiero acceder me tira el error "Failed to retrieve share list from server"

El único caso que encontré googleando se solucionó instalando samba, pero ya lo tengo instalado...

Mi /etc/samba/smb.conf es
```

[global]
workgroup = CASA
security = SHARE
[compartido]
path = /home/publico
public = yes
read only = no
guest ok = yes
```

Como siempre, GGRRAACCIIAASSS

---

