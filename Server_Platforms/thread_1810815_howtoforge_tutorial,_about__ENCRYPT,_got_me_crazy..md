---
title: "howtoforge tutorial, about  ENCRYPT, got me crazy..?"
date: 2011-07-23
forum: Server Platforms
---

### Post by vannia_p on 2011-07-23
Hi all, this wont to be easy one I guess, since I have not idea how explain it.

Here we go: I have been follow this great tutorial from  [Falkos at howtoforge]("http://www.howtoforge.com/virtual-users-and-domains-with-postfix-courier-mysql-and-squirrelmail-ubuntu-10.10"), everything works great, not a problem at all (thanks Falko).

They recomend to use (into terminal)

```

mysql -u root -p
####  password here
USE mail;
INSERT INTO `users` (`email`, `password`, `quota`) VALUES ('my@site.com', ENCRYPT('PassGoHere'), 10485760);
quit;

```

It works perfect, but... some one can explain to me (like a baby) ;) how do I implement a Register_Validator_Form.php, that allow me to use ENCRYPT way ?... I have been use to many ways (cost me re install Ubuntu Server more than 5 times), but no luck at all.

The Table of "users" acept that I introduce data in my Registration Validation Form like:

```
INSERT INTO users (email, password, quota) VALUES ('my@site.com', CRYPT('PassGoHere'), 10485760);
```

or

```
INSERT INTO users (email, password, quota) VALUES ('my@site.com', md5('PassGoHere'), 10485760);
```

But DOING THAT users can not login... ...The only way is using terminal, and insert the user by hand, like tutorial said..?.. So my worry is how, to make my "php" Registration Validation Form to match the whole Tutorial configuration for that [COLOR="Red"]ENCRYPT[/COLOR]('PassGoHere') .. somethis like:

INSERT INTO `users` (`email`, `password`, `quota`) VALUES ('my@site.com', [COLOR="Red"]WHAT_DO_I_PLACE_HERE[/COLOR]('PassGoHere'), 10485760);

This thing really drive me crazy allready... Thanks for your suport guys.

---

### Post by vannia_p on 2011-07-24
*bump*
:confused:

---

### Post by vannia_p on 2011-08-02
*bump*
Somebody please...?

---

### Post by vannia_p on 2011-08-13
[-o<

*bump*

Somebody please

---

### Post by vannia_p on 2011-08-16
**PHP authentication with mysql encrypt function**

The solution is in:

[http://www.howtoforge.com/forums/showthread.php?t=17804]("http://www.howtoforge.com/forums/showthread.php?t=17804") .. about page 2.

Thanks to @Falko and @Mark_NL from howtoforge forums.

:guitar:

---

### Post by PierreRobiquet on 2011-08-16
If I were you I would avoid using the MySQL encrypt function as it is based on the old and known vulnerable DES standard. Instead use a hashing algorithm such as SHA-256 with a individual user salt and multiple rounds. I've seen other people recommend bcrypt however I've never personally used it, I instead stick to SHA-256 with 10,000 rounds and a large per user salt.

---

### Post by vannia_p on 2011-08-16
> **ConcreteDonkey said:**
> If I were you I would avoid using the MySQL encrypt function as it is based on the old and known vulnerable DES standard. Instead use a hashing algorithm such as SHA-256 with a individual user salt and multiple rounds. I've seen other people recommend bcrypt however I've never personally used it, I instead stick to SHA-256 with 10,000 rounds and a large per user salt.


Good point... What about using a registration Form with ENCRYPT password, from a https encrypted connection .. using AES_256_CBC, with SHA1 for message authentication and DHE_RSA as the key exchange mechanism... ??

Still insecure ? ... Just wonder :confused:

---

### Post by PierreRobiquet on 2011-08-16
The main idea of hashing all of the passwords in your database is in case it is ever compromised as it will prevent the attackers gaining access to the users plain text passwords. You don't need to worry too much about HTTPS unless you already have a certificate or are handling payment information. You'll probably want something along the lines of this:

```

for ($i = 1; $i <= 1000; $i++) {
    $pass_h = hash("sha256",$password.$salt);
}

```

That will perform 1000 rounds of SHA256 on the password + salt, of course you will have to set a salt for each user and then grab it with a query. The hashed password will then be set as $pass_h. Although I'm not a cryptography expert and I'm sure someone with a lot better knowledge can suggest a better method. When generating the salt make sure it's long and unique, I would say around 20 characters should be fine the salt is there to prevent rainbow table attacks.

---

### Post by vannia_p on 2011-08-16
Thanks @ConcreteDonkey, good point .. .. as mentioned before, I use encrypted https connection .. using AES_256_CBC, With SHA1 for message authentication and key exchange DHE_RSA as the mechanism.

The registration of users is created from https, authenticated by a shell scrypt (server side) and then inserted into the database, using MySQL ENCRYPT password plus salt mechanism ... and the database is only available to the LAN, which does not actually have internet access (I refer to the MySQL server).

But the way you explain it, it would be more effective.
Any  specific link you want to share.

Regards.

---

### Post by PierreRobiquet on 2011-08-16
You have a very good system so far especially for HTTPS as far as I can tell and the seperation of the database is also a good step although I am the ultra paranoid type and I would consider what if your web server were accessed and the attacker can read your shell script? Then they could "pivot" and attack your MySQL database, the best explanation I can use is in Metasploit as I have done it before with a group of VM's.

[http://blog.metasploit.com/2010/02/automatically-routing-through-new.html](http://blog.metasploit.com/2010/02/automatically-routing-through-new.html)

Even though your database is separate from the internet an attacker could tunnel through the assumed exploited web server and gain access to your MySQL database. In regards to the best password hashing method I would browse StackOverflow it is filled with highly knowledgeable people but here's an article I picked out with some good advice:

[http://stackoverflow.com/questions/401656/secure-hash-and-salt-for-php-passwords](http://stackoverflow.com/questions/401656/secure-hash-and-salt-for-php-passwords)

---

