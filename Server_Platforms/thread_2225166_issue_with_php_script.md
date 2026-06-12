---
title: "issue with php script"
date: 2014-05-20
forum: Server Platforms
---

### Post by sebastiaopburnay on 2014-05-20
Hi!

I have an ubuntu server 12.0.4 LTS, and I guess my issue has to do with permissions.

I have a php script to send html eMail notifications, something like this:
```

#!/usr/bin/php -c /etc/php.ini

<?php
function data_uri($file, $mime) {
    $contents = file_get_contents($file);
    $base64 = base64_encode($contents);
    return "data:$mime;base64,$base64";
}
?>


<?php
 $subject = "someSubject";
 
 $from  ="someEmailAddress";
 $body = "someBody";

 $headers = "From: $from\r\n";
 $headers = $headers."Content-type: text/html; charset=ISO-8859-1\r\n";
  
 mail($f_to, $subject, $body, $headers); 
?>

```

I can run this script as **root **and as **someUser**.

But the eMail is only sent when I'm using root.

As this script is to be run by **someUser**'s process, I really need **someUser **to be able to run this script and send this notiifcation eMail.

Any ideas?

Thank you in advance,
sebastiaopburnay

---

### Post by SeijiSensei on 2014-05-20
The variable "$f_to" is undefined.

---

### Post by sebastiaopburnay on 2014-05-20
> **SeijiSensei said:**
> The variable "$f_to" is undefined.

It is, otherwise, root user wouldn't be able to send mails, I've ommited the code below in favour of simplicity:
```

 array_shift($argv); 
 $f_notify_type =array_shift($argv);
 $f_host_name =array_shift($argv);
 $f_host_alias =array_shift($argv);
 $f_host_state =array_shift($argv);
 $f_host_address =array_shift($argv);
 $f_serv_output =array_shift($argv);
 $f_long_date =array_shift($argv);
 $f_serv_desc  =array_shift($argv);
 $f_serv_state  =array_shift($argv);
 $f_to  =array_shift($argv);
 $f_duration = round((array_shift($argv))/60,2);
 $f_downtime =array_shift($argv);
 $f_totwarnings =array_shift($argv);
 $f_totcritical =array_shift($argv);
 $f_totunknowns =array_shift($argv);
 $f_add_hour = array_shift($argv); 

```

---

### Post by sebastiaopburnay on 2014-05-20
Well,this had to do with the **from:** parameter in the SMTP message.

Apparently:
 - my **root** user was properly mapped to the *noreply@myCompany.pt* address
 - and the **someUser** was just geting out as *someUser@myCompany.pt*.

The only valid address (from our SMTP relay's perspective) is the [email]noreply@myCompany.pt[/email].

Ignorant as I am, I don't really know how postfix is mapping these values,

So, when I've forced the mail command in the php script as:
```
 mail($f_to, $subject, $body, $headers,"-f noreply@myCompany.pt");
```

Adding the ***"-f [email]noreply@myCompany.pt[/email]"*** parameter did the trick.

Thank you for your knowlege-sharing.

Best regards,
sebastiaopburnay

---

