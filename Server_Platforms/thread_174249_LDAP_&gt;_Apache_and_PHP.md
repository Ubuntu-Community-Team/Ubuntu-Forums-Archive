---
title: "LDAP &gt; Apache and PHP"
date: 2006-05-11
forum: Server Platforms
---

### Post by Useless on 2006-05-11
Hello all

     I have an apache server running right now with a php site on it.  Its basically a forum here in our intranet.  It has been a great success so far so they want to fully integrate it in to our other apps, but in order to do so i need to add an ldap authentication log in screen for it.  I have the php log in screen set up ldap, BUT my version of php does not have ldap support.  It is not in the "info" screen.  I have added all the necessary ldap libraries on to the machine i just dont know how to get it to play nicely with the apache server and php.  

Any input would be appreciated.

---

### Post by DrSturgeon on 2006-05-14
If you have php5 working with apache2 all from ubuntu packages, all you should have to do is install the "php5-ldap" package.  This will enable the ldap functions in php.  Then from php, these two lines are all you need to authenticate users:

```

$ldap=ldap_connect("hostname_of_ldap_server");
if (@ldap_bind($ldap,"username@domain.com","password")) {
    echo("permission granted");
} else {
    echo("permission denied");
}

```

If you actually want to query the server for user data (at least with Microsoft's Active Directory, I'm not sure about OpenLDAP), you need to make the ldap connection through SSL.  I'm not 100% sure that's possible using the ubuntu packages, you may have to compile everything yourself.  If you do, the process goes like this:

1. Compile OpenSSL.
2. Get the signed security certificate from the CA.  (In Win2k, you "Export" it from the "Certification Authority" mmc snap-in.)
3. Compile OpenLDAP with OpenSSL support.
4. Compile PHP with OpenLDAP support.

I'm actually looking for some advice on this too:  does anyone know if it is possible to enable SSL support in the Ubuntu-packaged php ldap module?  I'm rebuilding a webserver, and I thought I'd try to see how Ubuntu-pure I could keep it.  This may be the straw that breaks the camel's back.

LDAP + SSL + PHP + Apache is a pain.  Good luck.

---

### Post by Useless on 2006-05-16
Awesome, thanks.  I ended up using the apt-get install php-ldap command it went through smooth.  The rest i had allready set up, thanks!

---

