---
title: "CUPS pagelog missing page-number"
date: 2011-06-21
forum: System76 Support
---

### Post by healperci on 2011-06-21
Hi there, I setup the cups server and is working ok with all the networks clients, is printing fine. But I need to register how many pages did a user print, and the page_log only shows 1 1 for all the works.


kmnorte 234 sistemas [21/Jun/2011:13:52:04 -0500] 1 1 - 192.168.2.222 smbprn.00000001 Microsoft Word - Documento1 - - kmnorte 235 sistemas [21/Jun/2011:13:58:14 -0500] 1 1 - 192.168.2.222 smbprn.00000002 Microsoft Word - Documento1 - - kmnorte 236 auxiliar.cartera [21/Jun/2011:14:18:35 -0500] 1 1 - 192.168.2.84 ActiveReports Document - - kmnorte 237 coordinadora.calidad [21/Jun/2011:14:36:22 -0500] 1 1 - 192.168.2.109 CRUZ ROJA.xlsx - - kmsur 238 almacen.administrativo [21/Jun/2011:14:36:26 -0500] 1 1 - 192.168.2.77 COTIZACION  MESA DE MAYO  JUNIO 21.xls - - kmnorte 239 analista.auditoria [21/Jun/2011:14:37:59 -0500] 1 1 - 192.168.2.78 ARCHIVO CONTRATOS 2011.xls - -

for example 
kmsur 238 was a job with four pages.
I don't know what to do... thanks in advance.

---

### Post by healperci on 2011-06-23
Hi there again.

I found what was the problem, is not easy to resolv the problem, but if you don't use the correct printing filter (driver via ppd) and the correct driver in windows the CUPS system doesn't register properly the number of pages that a client sent to the printer.

that's all folks...

---

