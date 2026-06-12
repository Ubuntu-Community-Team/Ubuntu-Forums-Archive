---
title: "Conflicto entre Madwifi y driver ATI"
date: 2008-08-09
forum: Software
---

### Post by cutOff on 2008-08-09
Buenas tardes desde España.

Estoy en Hardy, uso el driver madwifi 0.10.5.6-r3698 ([http://snapshots.madwifi.org/special/]("http://snapshots.madwifi.org/special/")) en mi placa **Atheros Communications, Inc. AR5006EG 802.11**. Sin embargo, parece no llevarse bién con mi placa de video, ya que si compilo los madwifi, la placa Atheros funciona excelente, pero la gráfica ATI no lo admite. He buscado info por el foro, pero todo es muy confuso. Espero puedan echarme una mano.

Pongo la salida del comando lspci:

```
02:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)

```

```
01:05.0 VGA compatible controller: ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]

```

El kernel que uso:

```
Linux this 2.6.24-19-generic #1 SMP Fri Jul 11 23:41:49 UTC 2008 i686 GNU/Linux

```

Gracias por anticipado.

---

### Post by Hei Ku on 2008-08-09
que drivers usas para la ATI?

---

### Post by cutOff on 2008-08-09
> **Hei Ku said:**
> que drivers usas para la ATI?

> ati-driver-installer-8-7-x86.x86_64.run

Kernel: linux-image-2.6.24-18-generic
Headers: linux-headers-2.6.24-18-generic
linux-restricted-modules: linux-restricted-modules-2.6.24-19-generic

Veo que hay una pequeña diferencia de versión entre las **restricted** y mi kernel, pero no creo que este sea el problema.

A ver si alguien me ilumina.

Gracias.

---

