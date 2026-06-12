---
title: "me aparecen en blanco algunas cosas"
date: 2008-11-12
forum: Software
---

### Post by tsueseres on 2008-11-12
hola, creo la regue desinstale emerald y creo que borre algo del xorg.conf y ahora no veo lo que escribo en una terminal, jdownloader tampoco lo veo y ha desaparecido la barra de la parte de arriba de las ventanas (las de maximizar, minimizar, cerrar), y el cairo dock tampoco lo veo.

alguien sabe como arreglar esto?

---

### Post by hictio on 2008-11-12
Abri el 'Run Application' box, tipea Alt + F2, y en el tipea:

```

metacity --replace (ENTER)

```

---

### Post by tsueseres on 2008-11-12
> **hictio said:**
> Abri el 'Run Application' box, tipea Alt + F2, y en el tipea:

```

metacity --replace (ENTER)

```

ok funciona pero loluego vuelve a como estaba

que puedo hacer

---

### Post by luks911 on 2008-11-14
¿Usás Compiz? Si es así, andá a: Sistema > Preferencias > Advanced Desktop Effects Settings (o el nombre que tenga las opciones de Compiz) > Decoración de ventanas
en la opción comando seguro que dice emerald, reemplazalo por metacity.

Cualquier cosa avisá porque estoy en una máquina con win :( en el trabajo.

Saludos

---

### Post by tsueseres on 2008-11-14
ok ya lo resolvi lo que hice fue reconfigurar el xorg.conf

---

