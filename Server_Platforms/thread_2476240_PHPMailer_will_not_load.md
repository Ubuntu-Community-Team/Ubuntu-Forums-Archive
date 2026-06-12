---
title: "PHPMailer will not load"
date: 2022-06-20
forum: Server Platforms
---

### Post by unicav on 2022-06-20
I have a new installation of Ubuntu Server 22.04, apache2, and php 8.1  - all installed from apt 
Got my site online and working with my SSL certificate. Pages load fine.
Then I added libphp-phpmailer from apt. It installed into /usr/share/php
phpinfo shows the include directory as /usr/share/php but phpmailer is not anywhere in the loaded modules.
I also just found the instructions for enabling a module using phpenmod, but there's no corresponding phpmailer.ini file in mods-available.
Can anyone tell me what I'm doing wrong?

EDIT - It was a path error in php.ini. By default it's set to ./ which is the document root. After setting it to /usr/share/php it works.
Then calling it with the apt installation of libphp-phpmailer the usage is

```

use PHPMailer\PHPMailer\PHPMailer;
use PHPMailer\PHPmailer\Exception;
use PHPMailer\PHPMailer\SMTP;
require_once "libphp-phpmailer/autoload.php";

```

---

