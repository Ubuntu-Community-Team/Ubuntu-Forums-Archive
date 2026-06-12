---
title: "No puedo montar disco NTFS por que no soy root ¿?"
date: 2008-12-25
forum: Software
---

### Post by nemodot on 2008-12-25
Me salió esto hoy al tratar de abrir cualquiera de los dos discos NTFS que tengo. Adjunto la imagen de lo que me salió.

---

### Post by Hei Ku on 2008-12-25
Tenés que ir a la configuración de discos y cambiar la configuración de esos discos para poder montarlos como usuario.
O en la terminal, poner:

```

sudo mount /media/sda1

```

---

