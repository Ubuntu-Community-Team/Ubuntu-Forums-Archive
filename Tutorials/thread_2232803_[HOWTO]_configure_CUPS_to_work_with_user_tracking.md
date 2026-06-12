---
title: "[HOWTO] configure CUPS to work with user tracking"
date: 2014-07-04
forum: Tutorials
---

### Post by art2003 on 2014-07-04
Some printers like the Konica Minolta bizhub C220 have a feature that allows to track how many pages users print.

This is done by specifying your PIN with each printing job submited.

However there is a more elegant way so this is done automatically and transparently for the user

1) Configure the printer normally as LPD - write down the name you choose ej. CASACRISTO
**IMPORTANT:** Choose the driver Generic Postcript/Foomatic

2) Open a terminal and stop CUPS
```
 sudo service cups stop

```

3) Edit /etc/cups/ppd/CASACRISTO.ppd
Adding these 3 lines just before the last line:

```
*cupsFilter: "application/vnd.cups-raw 0 minolta"
*cupsFilter: "application/vnd.cups-command 0 commandtops"
*cupsFilter: "application/vnd.cups-postscript 0 minolta"
```

So it will look like this:
```
*cupsFilter: "application/vnd.cups-raw 0 minolta"
*cupsFilter: "application/vnd.cups-command 0 commandtops"
*cupsFilter: "application/vnd.cups-postscript 0 minolta"
*% End of generic.ppd, 07884 bytes.

```

4) Create /etc/cups/ppd/CASACRISTO.km (enter your own tracking number instead of 1234)
```
ACCOUNT_NAME="casacristo"
ACCOUNT_PASSWORD="1234"
ACCOUNT_COETYPE="0"
```

5) Create /usr/lib/cups/filter/minolta with this content:
```

#!/bin/bash
source /etc/cups/ppd/${PRINTER}.km

echo -en "\033%-12345X"
echo -en "@PJL JOB\015\012"
echo -en "@PJL SET KMSECTIONNAME = \"${ACCOUNT_NAME}\"\015\012"
echo -en "@PJL SET KMSECTIONKEY2 = \"${ACCOUNT_PASSWORD}\"\015\012"
echo -en "@PJL SET KMCOETYPE = ${ACCOUNT_COETYPE}\015\012"
echo -en "@PJL ENTER LANGUAGE = POSTSCRIPT\015\012"

cat -

echo -en "\004\033%-12345X\015\012@PJL EOJ\015\012"
echo -en "\033%-12345X"
```

6) Make it executable:
 ```
sudo chmod +x /usr/lib/cups/filter/minolta
```

7) Restart CUPS:
```
 sudo service cups start 
```

---

