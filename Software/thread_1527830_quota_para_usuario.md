---
title: "quota para usuario"
date: 2010-07-09
forum: Software
---

### Post by mama21mama on 2010-07-09
Hola,

ando viendo [esta guia]("http://doc.ubuntu-es.org/index.php?title=Gesti%C3%B3n_de_usuarios_y_grupos#Administrando_el_sistema_de_quotas") [2]("http://linux.tronk.net/archives/115")[ 3]("http://www.linuxtotal.com.mx/index.php?cont=info_admon_018") 4 para implementar quotas a usuarios pero me tira este error.

> mama@zeusa:~$ sudo quotacheck -avugf
[sudo] password for mama: 
quotacheck: Your kernel probably supports journaled quota but you are not using it. Consider switching to journaled quota to avoid running quotacheck after an unclean shutdown.
quotacheck: AVISO- El archivo Quota //aquota.user probablemente esté truncado. No se puede salvar la configuración de cuota...
quotacheck: AVISO- El archivo Quota //aquota.group probablemente esté truncado. No se puede salvar la configuración de cuota...
quotacheck: No se puede remontar el archivo del sistema montado como solo lectura en /  por lo tanto los valores del conteo puede no ser correctos.
Por favor detenga todos los programas que escriben en el archivo del sistema o use el flag -m para forzar una comprobación.
mama@zeusa:~$ 



:s

---

### Post by mama21mama on 2010-07-23
Una [excelente guiá]("http://mamalibre.eshost.com.ar/?q=content/quota-limitar-el-disco-duro-un-usuario") de como hacerlo.

---

