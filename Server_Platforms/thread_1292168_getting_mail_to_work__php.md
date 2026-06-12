---
title: "getting mail to work / php"
date: 2009-10-15
forum: Server Platforms
---

### Post by ALnot on 2009-10-15
I have LAMP setup on 8.10
here is a simple php mail script:

if($_POST['email'])
{
    $to      = $_POST['email'];
    $subject = "bla";
    $message = "Read Now";
    $headers = 'From: Bla.com' . "\r\n" .
        'Reply-To: [EMAIL="Al@bla.com"]Al@bla.com[/EMAIL]' . "\r\n" .
        'X-Mailer: PHP/' . phpversion();

    mail($to, $subject, $message, $headers);
    echo "An alert has been sent.";
}

No errors are returned, nor is any email sent.
I ran this function:

if (function_exists('mail'))
{
    echo "Looks like php mail() is installed/enabled so its something else..";
}
else
{
    echo "The problem is php mail() is not installed or enabled";
}  

 php mail() is installed/enabled, so is there some other setting or package
I need to install???

ALnot.

---

### Post by Bachstelze on 2009-10-15
We'll need more details abnout your environment. Is the server on a home connection? Does said connection have a static or dynamic IP? etc..

---

### Post by yknivag on 2009-10-15
Do you have a mailserver installed?  If so which one and is it configured correctly?

Can you send email from the CLI on the box without using PHP?

```

sendmail your.email@address.com <press enter>
Testing<press enter>
<press enter>
<press Ctrl+D>

```

Is the script sending email externally from your network? If so does your ISP allow this? (many don't to prevent open relays being used for spam)

It's unlikely to be PHP to be honest, and much more likely to be your mailserver setup.

---

### Post by ALnot on 2009-10-15
the server is behind my cowcast modem hooked up to a linksus router.
I am using a static address. sounds like an obvious answer but there is no
mail server installed. I used synaptic and installed some pear packages as a 
blind hope, no luck.

ALnot

---

### Post by Girya on 2009-10-15
> **ALnot said:**
> the server is behind my cowcast modem hooked up to a linksus router.
I am using a static address. sounds like an obvious answer but there is no
mail server installed. I used synaptic and installed some pear packages as a 
blind hope, no luck.

ALnot

install sendmail from an xterm (acessories>terminal): 

> sudo apt-get install postfix

configure postfix: [//https://help.ubuntu.com/9.04/serverguide/C/postfix.html]("https://help.ubuntu.com/9.04/serverguide/C/postfix.html")

note: on my system the default php install sends mail to /usr/bin/sendmail you'll have to change your config file to postfix.

---

### Post by JK3mp on 2009-10-15
+1 to above. You need a mailserver. :P

---

