---
title: "ebox error"
date: 2010-05-14
forum: Server Platforms
---

### Post by blackcloud on 2010-05-14
help me iam try install ebox on lucid and i got error, this the error.
 * Stopping eBox module: apache                                                              [fail]
Creating the eboxlogs database
 * Stopping eBox module: apache                                          [fail]
root command /usr/share/ebox/ebox-apache2ctl stop failed.
Error output: apache2: Syntax error on line 56 of /var/lib/ebox/conf/apache2.con                    f: Could not open configuration file /etc/apache2/mods-available/perl.load: No s                    uch file or directory

Command output: .
Exit value: 1
 * Restarting eBox module: apache                                        [ OK ]

---

### Post by windependence on 2010-05-14
Try installing Perl first.

-Tim

---

### Post by blackcloud on 2010-05-14
i has install perl.

---

### Post by windependence on 2010-05-14
Does /etc/apache2/mods-available/perl.load exist on your machine? If so, what are the permissions on that file?

You may need to do:

 ```
# ln -s /etc/apache2/mods-available/perl.load  /etc/apache2/mods-enabled/perl.load  
    # ln -s /etc/apache2/mods-available/perl.conf  /etc/apache2/mods-enabled/perl.conf  

```

to enable Perl in Apache.

-Tim

---

### Post by blackcloud on 2010-05-14
im not found perl load on my apache2 mods, can you give me solution to install this perl mods.

---

