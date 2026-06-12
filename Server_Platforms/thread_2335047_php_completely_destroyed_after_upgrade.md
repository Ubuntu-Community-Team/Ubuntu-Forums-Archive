---
title: "php completely destroyed after upgrade"
date: 2016-08-24
forum: Server Platforms
---

### Post by DigiAngel on 2016-08-24
Topic says it....luckily this is on a vm.  Php packages before upgrade:


```
ii  libapache2-mod-php5                 5.5.9+dfsg-1ubuntu4.19                  amd64        server-side, HTML-embedded scripting language (Apache 2 module)
ii  php-auth                            1.6.4-1                                 all          Creating an authentication system
ii  php-auth-sasl                       1.0.6-1                                 all          Abstraction of various SASL mechanism responses
ii  php-db                              1.7.14-2                                all          PHP PEAR Database Abstraction Layer
ii  php-http-request                    1.4.4-4                                 all          PEAR class to provide an easy way to perform HTTP requests
ii  php-log                             1.12.7-1                                all          Logging Framework
ii  php-mail                            1.2.0-6                                 all          Class that provides multiple interfaces for sending emails
ii  php-mail-mime                       1.8.8-1                                 all          PHP PEAR module for creating MIME messages
ii  php-mdb2                            2.5.0b5-1                               all          merge of the PEAR DB and Metabase php database abstraction layers
ii  php-net-dime                        1.0.2-2                                 all          class that implements DIME encoding
ii  php-net-smtp                        1.6.1-1                                 all          PHP PEAR module implementing SMTP protocol
ii  php-net-socket                      1.0.14-1                                all          PHP PEAR Network Socket Interface module
ii  php-net-url                         1.0.15-3                                all          easy parsing of Urls
ii  php-pear                            5.5.9+dfsg-1ubuntu4.19                  all          PEAR - PHP Extension and Application Repository
ii  php-soap                            0.13.0-1                                all          SOAP Client/Server class for PHP
ii  php5                                5.5.9+dfsg-1ubuntu4.19                  all          server-side, HTML-embedded scripting language (metapackage)
ii  php5-cli                            5.5.9+dfsg-1ubuntu4.19                  amd64        command-line interpreter for the php5 scripting language
ii  php5-common                         5.5.9+dfsg-1ubuntu4.19                  amd64        Common files for packages built from the php5 source
ii  php5-curl                           5.5.9+dfsg-1ubuntu4.19                  amd64        CURL module for php5
ii  php5-gd                             5.5.9+dfsg-1ubuntu4.19                  amd64        GD module for php5
ii  php5-imap                           5.4.6-0ubuntu5                          amd64        IMAP module for php5
ii  php5-intl                           5.5.9+dfsg-1ubuntu4.19                  amd64        internationalisation module for php5
ii  php5-json                           1.3.2-2build1                           amd64        JSON module for php5
ii  php5-mcrypt                         5.4.6-0ubuntu5                          amd64        MCrypt module for php5
ii  php5-mysql                          5.5.9+dfsg-1ubuntu4.19                  amd64        MySQL module for php5
ii  php5-pspell                         5.5.9+dfsg-1ubuntu4.19                  amd64        pspell module for php5
ii  php5-readline                       5.5.9+dfsg-1ubuntu4.19                  amd64        Readline module for php5
ii  php5-sqlite                         5.5.9+dfsg-1ubuntu4.19                  amd64        SQLite module for php5

```

and php packages after:
```

ii  php-auth                            1.6.4-1build1                       all          Creating an authentication system
ii  php-auth-sasl                       1.0.6-2build1                       all          Abstraction of various SASL mechanism responses
ii  php-cli                             1:7.0+35ubuntu6                     all          command-line interpreter for the PHP scripting language (default)
ii  php-common                          1:35ubuntu6                         all          Common files for PHP packages
ii  php-db                              1.7.14-3build1                      all          PHP PEAR Database Abstraction Layer
ii  php-imap                            1:7.0+35ubuntu6                     all          IMAP module for PHP [default]
ii  php-log                             1.12.9-1build1                      all          Logging Framework
ii  php-mail                            1.3.0-1                             all          Class that provides multiple interfaces for sending emails
ii  php-mdb2                            2.5.0b5-1build1                     all          merge of the PEAR DB and Metabase php database abstraction layers
ii  php-net-smtp                        1.7.1-1build1                       all          PHP PEAR module implementing SMTP protocol
ii  php-net-socket                      1.0.14-1build1                      all          PHP PEAR Network Socket Interface module
ii  php-pear                            1:1.10.1+submodules+notgz-6         all          PEAR Base System
ii  php-soap                            1:7.0+35ubuntu6                     all          SOAP module for PHP [default]
ii  php-xml                             1:7.0+35ubuntu6                     all          DOM, SimpleXML, WDDX, XML, and XSL module for PHP [default]
ii  php7.0-cli                          7.0.8-0ubuntu0.16.04.2              amd64        command-line interpreter for the PHP scripting language
ii  php7.0-common                       7.0.8-0ubuntu0.16.04.2              amd64        documentation, examples and common module for PHP
ii  php7.0-imap                         7.0.8-0ubuntu0.16.04.2              amd64        IMAP module for PHP
ii  php7.0-json                         7.0.8-0ubuntu0.16.04.2              amd64        JSON module for PHP
ii  php7.0-opcache                      7.0.8-0ubuntu0.16.04.2              amd64        Zend OpCache module for PHP
ii  php7.0-readline                     7.0.8-0ubuntu0.16.04.2              amd64        readline module for PHP
ii  php7.0-soap                         7.0.8-0ubuntu0.16.04.2              amd64        SOAP module for PHP
ii  php7.0-xml                          7.0.8-0ubuntu0.16.04.2              amd64        DOM, SimpleXML, WDDX, XML, and XSL module for PHP

```

a simple phpinfo(); with 14.04 gives a ton of info.  That same bit on the upgraded server gives a blank page.  Any assistance with trying to get to work would be great....again, glad I'm still testing.

---

### Post by darkod on 2016-08-25
As you probably noticed, ubuntu 16.04 comes with php7 compared to php5 in the previous versions. So even though ubuntu introduced this "change" I do not see this as a problem. As php moves along you have to modify your apps to work with the new php7. Which makes it more php "issue" than ubuntu.

---

### Post by DigiAngel on 2016-08-25
In this particular case, "application" is:

```
<?php

// Show all information, defaults to INFO_ALL
phpinfo();

?>

```

So yea....I do appreciate the change.  I'll dig in and post when I find the culprit.

---

### Post by darkod on 2016-08-25
Unfortunately I know almost nothing about php7 to know if that still works... But google or someone else should be able to help you.

Of course when I said application I meant all the sites that you might have in php5 and that might need adjustments to work in php7.

---

### Post by DigiAngel on 2016-08-25
Apparently the upgrade process completely misses package libapache2-mod-php which is required for php to even work.  So that was fun.

---

