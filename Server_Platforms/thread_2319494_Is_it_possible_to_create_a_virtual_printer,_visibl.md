---
title: "Is it possible to create a virtual printer, visible on the network?"
date: 2016-04-04
forum: Server Platforms
---

### Post by Dave_Harris on 2016-04-04
I need to create a virtual printer on an Ubuntu server, preferably one that appears to be an HP4 Laserjet. In other words: I want the server to present a network printer to the local net, that looks like an HP 4. When anything is printed to this "printer", the best result would be if it was forwarded to a real printer which is *not* a PS printer. However, saving the output to a PDF file, which can then be picked up by a CON job & printed on a real printer, would do. Any ideas anyone?

This is required to support a legacy application and before anyone asks, we *have* to use this application and they will *not* change anything for us. Don't ask :/

---

### Post by SeijiSensei on 2016-04-05
I'd start here: [https://wiki.linuxfoundation.org/en/OpenPrinting/Database/CupsFAQ#How_do_I_print_to_a_file.3F](https://wiki.linuxfoundation.org/en/OpenPrinting/Database/CupsFAQ#How_do_I_print_to_a_file.3F)

---

