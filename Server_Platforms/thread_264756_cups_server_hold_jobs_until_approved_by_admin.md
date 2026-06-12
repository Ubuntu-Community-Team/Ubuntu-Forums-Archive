---
title: "cups server hold jobs until approved by admin"
date: 2006-09-25
forum: Server Platforms
---

### Post by jsaints on 2006-09-25
I am trying to set up a cups print server for our network.  we would like the default behavior of the printer to be to hold all jobs until they are approved by an administrator.  

I have tried:
```
sudo lpadmin -p PRINTER_NAME_HERE -o job-hold-until-default=indefinite
```
but this doesn't seem to affect the printer's behavior. It is still printing all jobs on demand.  

Is there something in printers.conf that i need to change as well?

---

### Post by Stevko on 2007-12-17
> **jsaints said:**
> I am trying to set up a cups print server for our network.  we would like the default behavior of the printer to be to hold all jobs until they are approved by an administrator.  

I have tried:
```
sudo lpadmin -p PRINTER_NAME_HERE -o job-hold-until-default=indefinite
```
but this doesn't seem to affect the printer's behavior. It is still printing all jobs on demand.  

Is there something in printers.conf that i need to change as well?
Add
```

Option job-hold-until indefinite

```
to /etc/cups/printers.conf in section of the printer you need to limit.
(I know it is too late, but maybe someone else will use it)

---

