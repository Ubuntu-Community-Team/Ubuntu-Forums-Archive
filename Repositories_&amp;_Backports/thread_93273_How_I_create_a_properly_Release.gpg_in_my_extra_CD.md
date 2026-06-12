---
title: "How I create a properly Release.gpg in my extra CDs?"
date: 2005-11-21
forum: Repositories &amp; Backports
---

### Post by nhereveri on 2005-11-21
I copy my signature in a dists/breezy/Release.gpg file, but (i think) gpgv don't know this signature.

If someone know the working system and how create this file, plz tell me.

Error say:

[FONT="Courier New"]$ apt-cdrom add
Usando el punto de montaje del CD-ROM /cdrom/
Desmontando el CD-ROM
Esperando el disco...
Please insert a Disc in the drive and press enter
Montando el CD-ROM...
Identificando.. [6b305f5ab59f8b8aa8d0c30e16e5c55b-2]
Buscando en el disco archivos de índices...
Se encontraron 4 índices de paquetes, 0 de fuentes y 1 firmas
Found label 'Ubuntu 5.10 _Breezy Badger_ EXTRA CD - Release i386 (20051121)'
Este disco se llama:
'Ubuntu 5.10 _Breezy Badger_ EXTRA CD - Release i386 (20051121)'
Copiando las listas de paquetes...gpgv: Signature made lun 21 nov 2005 14:19:16 CLST using DSA key ID 769CBDCE
gpgv: Can't check signature: public key not found
E: El subproceso gpgv devolvió un código de error (2)
W: Signature verification failed for: /cdrom/dists/breezy/Release.gpg[/FONT]

---

### Post by az on 2005-11-24
Offhand, I think the key you need to sign it beliongs to the release manager.  I do not thinik you would be able to sign your custom cd as an official one. I may be wrong.  If so, would you add the solution here:

[https://wiki.ubuntu.com/AptMoveHowto](https://wiki.ubuntu.com/AptMoveHowto)

I think by naming your cd something else, you avoid the authentification problem that is preventing your cd from being added to the repository list.

But then the packcages you install still require you to consent to their installation without authentification.  I cannot tell by the error you posted if the repo is being added or not.

---

