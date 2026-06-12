---
title: "error en la actualización de repositorios"
date: 2008-10-24
forum: Server Platforms
---

### Post by nauix on 2008-10-24
Hace unos días que quando entro en el synaptics i hago un "actualizar" para ver todos los repositorios disponibles me dice:

No se ha podido obtenir [http://cairo-dock.vef.fr/ubuntu/dists/gutsy/cairo-dock/binary-i386/Packages.gz](http://cairo-dock.vef.fr/ubuntu/dists/gutsy/cairo-dock/binary-i386/Packages.gz)  302 Found
No se ha podido obtenir [http://soulmachine.net/breezy/unstable/Packages.gz](http://soulmachine.net/breezy/unstable/Packages.gz)  404 Not Found
No se pueden descaregar algunos fitxeros índices, se han ignorado o en su lugar se han usado los antiguos.


No sé que pasa, desde hace ya un mes que me tira este mensaje, alguien ha tenido el mismo problema? Alguien sabe como resolverlo?


gracias amigos!



arnau

---

### Post by koenn on 2008-10-24
you appear to be using old and unofficial repositories.
The source of your problem may be that these servers are no longer maintained or that the release you're trying to download (breezy) has been removed from them.

You should probably (and preferably) install a recent Ubuntu version
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

If you insist on using breezy, you're going to have to find repository servers that still have breezy repos, and add those to your software sources, replacing the ones that are not working. Can't help you with that.

---

