---
title: "odbcinst: symbol lookup error: odbcinst: undefined symbol: iniOpen error installing m"
date: 2023-06-17
forum: Server Platforms
---

### Post by vagamente-gmail on 2023-06-17
Ubuntu server 20.04.
After updating all packets, msodbcsql17 stopped working.


I've purged it and then tried to reinstall and i get an error in post-install process.


The error is 


```
    odbcinst: symbol lookup error: odbcinst: undefined symbol: iniOpen

```

The unixodbc package is installed and it seems ok


    ```
root@zerfasv005:/home/utente1# odbcinst
    
    **********************************************
    * unixODBC - odbcinst                        *
    **********************************************
    *                                            *
    * Purpose:                                   *
    *                                            *
    *      An ODBC Installer and Uninstaller.    *
    *      Updates system files, and             *
    *      increases/decreases usage counts but  *
    *      does not actually copy or remove any  *
    *      files.                                *
    *                                            *
    * Syntax:                                    *
    *                                            *
    *      odbcinst Action Object Options        *
    *                                            *
    * Action:                                    *
    *                                            *
    *      -i         install                    *
    *      -u         uninstall                  *
    *      -q         query                      *
    *      -j         print config info          *
    *      -c         call SQLCreateDataSource   *
    *      -m         call SQLManageDataSources  *
    *      --version  version                    *
    *                                            *
    * Object:                                    *
    *                                            *
    *      -d driver                             *
    *      -s data source                        *
    *                                            *
    * Options:                                   *
    *                                            *
    *      -f file name of template.ini follows  *
    *         this (valid for -i)                *
    *      -r get template.ini from stdin, not   *
    *         a template file                    *
    *      -n Driver or Data Source Name follows *
    *      -v turn verbose off (no info, warning *
    *         or error msgs)                     *
    *      -l system dsn                         *
    *      -h user dsn                           *
    *                                            *
    * Returns:                                   *
    *                                            *
    *      0   Success                           *
    *     !0   Failed                            *
    *                                            *
    * Please visit;                              *
    *                                            *
    *      http://www.unixodbc.org               *
    *      pharvey@codebydesign.com              *
    **********************************************

```

I've tried even to reinstall unixodbc but still get the same error.

How can I solve it?

---

### Post by MAFoElffen on 2023-06-19
I believe this is the order of things to do a reinstall of 'odbcinst'
```

sudo mv /usr/bin/odbcinst /usr/bin/odbcinst.old
sudo mv /etc/odbcinst.ini /etc/odbcinst.ini.old 
sudo mv /usr/share/man/man1/odbcinst.1.gz /usr/share/man/man1/odbcinst.1.gz.old
sudo apt install --reinstall odbcinst libsqliteodbc odbc-postgresql tdsodbc

```

---

### Post by erpo on 2023-10-11
I ran into the same error on one of our servers. The issue turned out to be that /usr/bin/odbcinst (provided by the odbcinst package) was loading incompatible shared libraries from /usr/local/lib/, which had not been installed by a package. Removing them caused /usr/bin/odbcinst to load /usr/lib/x86_64-linux-gnu/libodbcinst.so.2, the correct shared library, which allowed installation of msodbcsql17 without errors.

> 
sudo rm /usr/local/lib/libodbccr.la
sudo rm /usr/local/lib/libodbccr.so
sudo rm /usr/local/lib/libodbccr.so.2
sudo rm /usr/local/lib/libodbccr.so.2.0.0
sudo rm /usr/local/lib/libodbcinst.la
sudo rm /usr/local/lib/libodbcinst.so
sudo rm /usr/local/lib/libodbcinst.so.2
sudo rm /usr/local/lib/libodbcinst.so.2.0.0
sudo rm /usr/local/lib/libodbc.la
sudo rm /usr/local/lib/libodbc.so
sudo rm /usr/local/lib/libodbc.so.2
sudo rm /usr/local/lib/libodbc.so.2.0.0


---

