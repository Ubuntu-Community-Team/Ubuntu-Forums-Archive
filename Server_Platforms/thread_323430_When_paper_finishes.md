---
title: "When paper finishes"
date: 2006-12-22
forum: Server Platforms
---

### Post by salvo1 on 2006-12-22
Hi all,
I have hylafax server on Ubuntu 6.06 that print incoming faxes on a HP Laserjet 1300 (driver: lj4dith).

If paper finishes, often during the night, i find the printer blocked with a lot of "print jobs stopped".

How can i let the printer retry to print all jobs for ever? In this way, when in the morning some1 put new paper, faxes are automaticaly printed.

Bye,
Salvo

---

### Post by darrenm on 2006-12-22
> **salvo1 said:**
> Hi all,
I have hylafax server on Ubuntu 6.06 that print incoming faxes on a HP Laserjet 1300 (driver: lj4dith).

If paper finishes, often during the night, i find the printer blocked with a lot of "print jobs stopped".

How can i let the printer retry to print all jobs for ever? In this way, when in the morning some1 put new paper, faxes are automaticaly printed.

Bye,
Salvo

You could just re-enable all disabled printers every 10 mins?

```

echo "for printer in \`lpstat -t | grep disabled | awk '{print \$2}'\` ; do /usr/bin/enable \$printer ; done" > /bin/cups_enable.sh
chmod 755 /bin/cups_enable.sh
crontab -e
0/10 * * * * /bin/cups_enable.sh >/dev/null
```

---

### Post by salvo1 on 2006-12-22
Solved by editing cups.conf
```

...
ErrorPolicy retry-job
...
```

(it was ```
ErrorPolicy stop-printer
```)

---

