---
title: "Try to install Zoom on 14.04 but the text of own icons software dont appear."
date: 2020-09-16
forum: Ubuntu/Debian BASED
---

### Post by Portaro on 2020-09-16
Hello friends I try to install zoom on Lubuntu 14.04 and the software install well.
But when I open the software aplication client on desktop he dont have some texts on icons.

[IMG]https://i.imgur.com/wHuj8U9.png[/IMG]

The command install return on moment of zoom install &#8594;

```
flavitu@flavitu-P4V88:~$ sudo dpkg -i /home/flavitu/zoom_i386.deb
[sudo] password for flavitu: 
A seleccionar pacote anteriormente não seleccionado zoom.
(A ler a base de dados ... 561389 ficheiros e directórios actualmente instalados.)
A preparar para desempacotar /home/flavitu/zoom_i386.deb ...
A descompactar zoom (5.2.458699.0906) ...
A instalar zoom (5.2.458699.0906) ...
run post install script, action is configure...
Warning in file "/usr/share/applications/gnumeric.desktop": usage of MIME type "zz-application/zz-winassoc-xls" is discouraged ("zz-application/zz-winassoc-xls" should be replaced with "application/vnd.ms-excel")
A processar 'triggers' para shared-mime-info (1.2-0ubuntu3) ...
Unknown media type in type 'chemical/x-alchemy'
Unknown media type in type 'chemical/x-cache'
Unknown media type in type 'chemical/x-cactvs-ascii'
Unknown media type in type 'chemical/x-cactvs-binary'
Unknown media type in type 'chemical/x-cactvs-table'
Unknown media type in type 'chemical/x-cdx'
Unknown media type in type 'chemical/x-cdxml'
Unknown media type in type 'chemical/x-chem3d'
Unknown media type in type 'chemical/x-cif'
Unknown media type in type 'chemical/x-cml'
Unknown media type in type 'chemical/x-daylight-smiles'
Unknown media type in type 'chemical/x-dmol'
Unknown media type in type 'chemical/x-gamess-input'
Unknown media type in type 'chemical/x-gamess-output'
Unknown media type in type 'chemical/x-gaussian-input'
Unknown media type in type 'chemical/x-gaussian-log'
Unknown media type in type 'chemical/x-genbank'
Unknown media type in type 'chemical/x-gulp'
Unknown media type in type 'chemical/x-hin'
Unknown media type in type 'chemical/x-inchi'
Unknown media type in type 'chemical/x-inchi-xml'
Unknown media type in type 'chemical/x-jcamp-dx'
Unknown media type in type 'chemical/x-macromodel-input'
Unknown media type in type 'chemical/x-mdl-molfile'
Unknown media type in type 'chemical/x-mdl-rdfile'
Unknown media type in type 'chemical/x-mdl-rxnfile'
Unknown media type in type 'chemical/x-mdl-sdfile'
Unknown media type in type 'chemical/x-mdl-tgf'
Unknown media type in type 'chemical/x-mmcif'
Unknown media type in type 'chemical/x-mol2'
Unknown media type in type 'chemical/x-mopac-graph'
Unknown media type in type 'chemical/x-mopac-input'
Unknown media type in type 'chemical/x-mopac-out'
Unknown media type in type 'chemical/x-msi-car'
Unknown media type in type 'chemical/x-msi-hessian'
Unknown media type in type 'chemical/x-msi-mdf'
Unknown media type in type 'chemical/x-msi-msi'
Unknown media type in type 'chemical/x-ncbi-asn1'
Unknown media type in type 'chemical/x-ncbi-asn1-binary'
Unknown media type in type 'chemical/x-ncbi-asn1-xml'
Unknown media type in type 'chemical/x-pdb'
Unknown media type in type 'chemical/x-shelx'
Unknown media type in type 'chemical/x-vmd'
Unknown media type in type 'chemical/x-xyz'
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
A processar 'triggers' para desktop-file-utils (0.22-1ubuntu1.1) ...
A processar 'triggers' para bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
A processar 'triggers' para mime-support (3.54ubuntu1.1) ...

```

What I can do to try to solve this ?

Thanks.

---

### Post by deadflowr on 2020-09-16
Why such an old release?
Lubuntu 14.04 has been more or less unsupported for years.

---

### Post by CelticWarrior on 2020-09-16
> **deadflowr said:**
> Why such an old release?
Lubuntu 14.04 has been more or less unsupported for years.

Because this person thinks it makes more sense to keep using 14.04 with a non-standard kernel on top (some liquorix or whatever) that does nothing more that newer standard kernels for support of their oldish AMD APU.
At least it has now ESM but not sure if that's even available for flavors. 

Or maybe it's because this person is reluctant in upgrading that curious project in the signature?

---

### Post by howefield on 2020-09-16
Moved to the "*Ubuntu/Debian BASED*" forum.

---

