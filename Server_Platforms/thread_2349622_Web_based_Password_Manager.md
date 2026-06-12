---
title: "Web based Password Manager"
date: 2017-01-16
forum: Server Platforms
---

### Post by pepsifx357 on 2017-01-16
Hi there,

I stumbled upon RatticDB over at [http://rattic.org/]("http://rattic.org/").  Unfortunately, it doesn't look like it's maintained anymore.  I'm really looking for something like this for my company.  We have a lot of users with multiple passwords for multiple services.  I've been looking for a way to keep up with all of these services/passwords.  Currently I'm using a pass worded excel sheet that shows the URL and Password.  Are there any forks of RatticDB, or alternatives anywhere?  I really want something web based.  I gave TeamPass a shot, but honestly I didn't know what to do with it after I got it up and running.  It didn't seem like it did what I needed it to do.

Thanks

---

### Post by SeijiSensei on 2017-01-16
Anyone in your organization know how to write PHP scripts with a database backend?  This wouldn't be very hard for a reasonably experienced developer to write from scratch.  You'd need a database like MySQL or PostgreSQL to store the username/url/password triplets, and a set of relatively simple scripts so that each user could log in and retrieve, add, or delete her passwords.  If you want real security, I'd use the mcrypt functions to encrypt the passwords with a two-way cipher like Rijndael-256 before storing them in the database.  To give you a leg up, here are two functions I wrote to encrypt and decrypt strings with that cipher and return the results as a base64 string which can be stored in a text field in the database:

```

function b64_encrypt($string,$key) {

     # encrypt a string with Rijndael-256 and $key
     # return the base64 encoding of the encrypted result

     # from the PHP manual
     $td = mcrypt_module_open('rijndael-256', '', 'ecb', '');
     $iv = mcrypt_create_iv (mcrypt_enc_get_iv_size($td), MCRYPT_RAND);
     mcrypt_generic_init($td, $key, $iv);

     # convert to base64 encoding
     $encrypted_data = base64_encode(mcrypt_generic($td, $string));

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

---

### Post by pepsifx357 on 2017-01-16
I just tried another one.  "Syspass."  Apparently these don't actually show you the passwords.  I'm not entirely sure what these types of software are for, but I need one that shows me the users password when I need it.  I also need it to show me the URL that their password goes to.

---

### Post by pepsifx357 on 2017-01-16
Thanks for the reply.  I wish I knew PHP.  There are a lot of times I would like to use that and a database.

---

### Post by mastablasta on 2017-01-18
maybe you can find an alternative here: [SIZE=2][https://github.com/tildaslash/RatticWeb/issues/404](https://github.com/tildaslash/RatticWeb/issues/404)

edit: not sure why you are using this at all (what is the point). here we have all or majority of services connected via AD domain (i think there is a Linux alternative for that), so ther eis just one password that matters to users.
for out of Office work there is TLS/SSL connection (or whatever it is called) again via AD username and password.

all is very user friendly and the only thing i do not udnerstand is why laptos are unencrpyted. one could have it stolen, it would be easy to get to admin password using ehm tools and then work your way up the system. not to mention that laptops contain various business secrets and sensitive information. ](*,)
[/SIZE]

---

