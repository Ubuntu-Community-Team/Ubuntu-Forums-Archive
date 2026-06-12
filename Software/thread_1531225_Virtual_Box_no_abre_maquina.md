---
title: "Virtual Box no abre maquina"
date: 2010-07-14
forum: Software
---

### Post by rogel on 2010-07-14
No se cual puede ser el problema, el VirtualBox (Ver. 3.2.6) no me abra una Maquina Virtual con WXP, me dice inaccesible y me da el siguiente mensaje:

 p, li { white-space: pre-wrap; }  Hard disk '/home/rodolfo/.VirtualBox/HardDisks/WXP.vdi' with UUID *{ecbbe793-94d5-4bae-921d-ca39e9c9d6c5}* cannot be directly attached to the virtual machine 'WXP' ('/home/rodolfo/.VirtualBox/Machines/WXP/WXP.xml') because it has 1 differencing child hard disks.
    Código Resultado: 
  [FONT= ]NS_ERROR_FAILURE (0x80004005)[/FONT]
   Componente: 
  Machine
   Interfaz: 
  IMachine {6d9212cb-a5c0-48b7-bbc1-3fa2ba2ee6d2}

Alguna idea de como resolverlo facilmente, soy muy novato.

Gracias!!!!
Rodolfo

---

### Post by alfplayer on 2010-07-14
Parece un problema que se puede resolver buscando en la web, en la salida está incluido un código de error.

---

### Post by juancarlospaco on 2010-07-15
Le tomaste un Snapshot?

Si es asi, es probable que se halla corrompido, 
podes borrar los Snapshots y iniciarla.

---

