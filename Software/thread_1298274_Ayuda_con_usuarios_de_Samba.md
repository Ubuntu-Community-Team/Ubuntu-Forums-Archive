---
title: "Ayuda con usuarios de Samba"
date: 2009-10-22
forum: Software
---

### Post by panchoarq on 2009-10-22
Hola,
necesito ayuda con SAMBA.Tengo un servidor Dell Poewer EdgeT-100 con samba instalado tratando de que sea servidor de archivos para otros equipod con vista. El tema es que mepermite que solo algunos equipos accedan y puedan escribir sobre lacarpeta compartida en Ubuntu y otros no.Todoslos usuarios estan configurados iguales y no se porque solo algunos "pescan" la configuracion y otrosni siquiera pueden accedera la carpeta.Elcomportamiento es erratico.Algunos puedes hacer todo,otros solo leer y otros ni siquiera entrar.
Por favor ayuda ya que llevo dias parado en este tema.

---

### Post by Carlos C on 2009-10-22
Sería bueno que nos dijeras cómo estás compartiendo tus archivos, si acaso editaste tu archivo /etc/samba/smb.conf, si creaste los usuarios samba, qué permisos les diste etc. Mientras más datos nos des más fácil será ayudarte.

Saludos.

---

### Post by moreback on 2009-10-23
Yo tuve varios problemas con los usuarios y al final resultó que la contraseña que tenían no estaba agregada al Samba con el **smbpasswd**.

¿Conclusión? Asignarles la contraseña con **smbpasswd** para que queden sincronizada con la del usuario del sistema.

Saludos.

---

