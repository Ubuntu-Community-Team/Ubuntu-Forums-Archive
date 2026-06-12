---
title: "PDO OCI driver exception"
date: 2010-09-21
forum: Server Platforms
---

### Post by Andrewdps on 2010-09-21
Hi all,

I get the following error when installing PDO_OCI.[SIZE=3][FONT=Verdana]
[/FONT]Fatal error:  PDO: driver oci requires PDO API version 20060409; this is PDO version 20060511 in Unknown on line 0[/SIZE]

When I tried to check the php version,I got an error showing
[SIZE=3]# php --version
PHP Fatal error:  PDO: driver oci requires PDO API version 20060409; this is PDO version 20060511 in Unknown on line 0
PHP 5.2.6-1+lenny9 with Suhosin-Patch 0.9.6.2 (cli) (built: Aug  4 2010 06:06:53) 
Copyright (c) 1997-2008 The PHP Group
Zend Engine v2.2.0, Copyright (c) 1998-2008 Zend Technologies

[/SIZE]

[SIZE=3]And phpinfo().php doesn't show me PDO sections...it's like[/SIZE][SIZE=3]PDO[/SIZE]  [SIZE=3]PDO support[/SIZE][SIZE=3]enabled[/SIZE] [SIZE=3]PDO drivers [/SIZE][SIZE=3]*no value*[/SIZE]  [SIZE=3]
[/SIZE] **[SIZE=3]PDO_OCI[/SIZE]**

  [SIZE=3]PDO Driver for OCI 8 and later[/SIZE][SIZE=3]enabled[/SIZE] [SIZE=3]
Can anyone point me in the right direction.

Thanks.
[/SIZE]

---

