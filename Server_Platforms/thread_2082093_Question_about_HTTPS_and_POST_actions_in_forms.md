---
title: "Question about HTTPS and POST actions in forms"
date: 2012-11-08
forum: Server Platforms
---

### Post by jwright8 on 2012-11-08
I'm not sure if this is the right section, but I've had a lot of luck getting support here so I figured I might as well try.  

If I have apache with mod_ssl enabled and a plugin for Wordpress that forces HTTPS on all pages, how would form submission work?  If I used a POST action on the forum, would the data still be encrypted upon/during transmission?  

I was looking to create a sort of application form that might require sensitive data (like a social security number).  I was going to enabled mod_ssl for apache, use the Wordpress HTTPS plugin, have an SSL certificate, and make the entire site HTTPS just to be sure, then have it e-mail over TLS to a RackSpace e-mail account.  

There are some services, like LuxSci ( [http://luxsci.com/extranet/secure-form.html](http://luxsci.com/extranet/secure-form.html) ), that offer a secure POST action url that they charge monthly for.  I was wondering if this was necessary, or if the settings above would do essentially the same thing.

Thank you guys in advance for any help/advice.  Any links where I could read up on this specific process would also be very appreciated;  most stuff I've read about SSL/TLS are just general conceptual articles and don't necessarily relate to POST form actions or anything.

---

### Post by thnewguy on 2012-11-08
I think if you're using HTTPS then that should be enough for protecting the data you're submitting using the form. Just make sure your connection to the server is handled over HTTPS.

Regarding the second part of your plan, I don't think you should e-mail sensitive data. Even if the server-to-server connection is encrypted, the data as it sits on the server will be in plain text.

What I have done to deal with this is have a generic e-mail sent out which notifies me of a new order/record added to the database with a link to an admin console. The admin page is accessed over HTTPS and the sensitive information doesn't leave the server. This prevents SSN or credit card information from being transmitted over the net to other servers.

---

### Post by Lars Noodén on 2012-11-08
I agree with thnewguy that HTTPS should be enough but that you should avoid using e-mail for sensitive data. 

Also, it might not even be a good idea to keep sensitive data on the servers.  Your country probably has written guidelines on data privacy that you can use in making your plans.

---

### Post by SeijiSensei on 2012-11-08
> **thnewguy said:**
> Regarding the second part of your plan, I don't think you should e-mail sensitive data. Even if the server-to-server connection is encrypted, the data as it sits on the server will be in plain text.

Unless you have encrypted the sensitive information before storing it on the server, you're asking for a heap of trouble.  

I would recommend putting the SQL server for WordPress on an entirely different machine, one preferably behind a firewall, and using OpenVPN to create an encrypted connection between the web server and the database server.  Then the server can write securely to the database, and the data never reside on a publicly-visible machine.  Depending on what this application is used for, you may still need to encrypt the data you are storing before writing it to the SQL server.  I use the mcrypt functions in PHP to encrypt the data with AES256, then use PHP's base64_encode() function to convert the encrypted binary representation to a text string that I write to the database.  

Here are the functions I wrote for this task, if you'd like to do a little home cooking:

```

    function b64_encrypt($string,$key) {

        # encrypt a string with AES256 and $key
        # return the base64 encoding of the encrypted result

        # from the PHP manual
        $td = mcrypt_module_open('rijndael-256', '', 'ecb', '');
        $iv = mcrypt_create_iv (mcrypt_enc_get_iv_size($td), MCRYPT_RAND);
        mcrypt_generic_init($td, $key, $iv);

        # convert the result to base64 encoding here
        $encrypted_data = base64_encode(mcrypt_generic($td, trim($string)));

        mcrypt_generic_deinit($td);
        mcrypt_module_close($td);

        return $encrypted_data;

    }

   function b64_decrypt($string,$key) {

        # convert a base-64 encoded string into a Rijndael-256
        # cipher then decrypt using $key

        $td = mcrypt_module_open('rijndael-256', '', 'ecb', '');
        $iv = mcrypt_create_iv (mcrypt_enc_get_iv_size($td), MCRYPT_RAND);
        mcrypt_generic_init($td, $key, $iv);

        $decrypted_data = mdecrypt_generic($td, base64_decode($string));

        mcrypt_generic_deinit($td);
        mcrypt_module_close($td);

        # trim any padding
        return trim($decrypted_data);

    }


```

For the key I just use a random md5 string hidden in the bowels of the file system.  The command-line command "ps -aux | md5sum" produces a pretty decent key.

I used [AES256]("http://en.wikipedia.org/wiki/Advanced_Encryption_Standard") to comply with Federal regulations on encryption standards.  The client was a medical provider so HIPAA compliance was essential.

---

### Post by jwright8 on 2012-11-08
Thank you all for your responses.  I kind of figured something like that would be the case.

Seiji, as always your responses are as thorough as they are helpful.  Given that I have an OpenVPN server already for private use, that approach will work perfectly. 

Is it plausible to write the file to a DB other than what Wordpress uses, or are you restricted to it?  Meaning to have both a WP db and an auxiliary DB on the same server that the form on a WP page can write to.

As for what it is used for, it will likely just be read (printed out) and removed/deleted from the database shortly thereafter.

---

### Post by SeijiSensei on 2012-11-09
> **jwright8 said:**
> Is it plausible to write the file to a DB other than what Wordpress uses, or are you restricted to it?  Meaning to have both a WP db and an auxiliary DB on the same server that the form on a WP page can write to.

Yes, you could do this by having the form POST to a different handler.  You'd have to write a custom script to do this.  Suppose the handler is called "postdata.php".  Then you'd just have the form POST to that handler like this:

```

<form action="/postdata.php" method="POST">
stuff
</form>

```

---

