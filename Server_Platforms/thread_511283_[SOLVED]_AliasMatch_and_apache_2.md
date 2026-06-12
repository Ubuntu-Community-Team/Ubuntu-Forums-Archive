---
title: "[SOLVED] AliasMatch and apache 2"
date: 2007-07-27
forum: Server Platforms
---

### Post by nkassi on 2007-07-27
I'm trying to use AliasMatch to map a bunch of folders from a mounted drive that all have a public_html folder to something like

example.com/share/departement/

which would redirect to 

/mnt/file_server/departement/public_html

Currently my AliasMatch looks like this:

AliasMatch ^/share(.*) /mnt/file_server$1public_html

It doesn't seem to understand since my error.log shows that the apache server is looking for /var/www/share and not matching it to the Alias

Please help

P.S. Why does SysAdmin day have to be so much worse than other days?

---

### Post by murraymca on 2007-07-27
Currently my AliasMatch looks like this:

AliasMatch ^/share(.*) /mnt/file_server$1public_html

It doesn't seem to understand since my error.log shows that the apache server is looking for /var/www/share and not matching it to the Alias

Hi,

Looking at [http://httpd.apache.org/docs/2.0/mod/mod_alias.html](http://httpd.apache.org/docs/2.0/mod/mod_alias.html) wouldn't the required syntax be:
AliasMatch ^/share(.*) /mnt/file_server/public_htm$1 ?

Hope that helps.

---

### Post by nkassi on 2007-07-29
Unless I'm mistaken, the $1 is replaced with what ever the (.*) matches. Agan if I'm not wrong this should make /mnt/file_server$1public_html become /mnt/files_server/department/public_html

But when I go to example.com/share/department it just give me a 404 error.

---

### Post by murraymca on 2007-07-30
[QUOTE=nkassi;3091497]I'm trying to use AliasMatch to map a bunch of folders from a mounted drive that all have a public_html folder to something like

example.com/share/departement/

which would redirect to 

/mnt/file_server/departement/public_html

Currently my AliasMatch looks like this:

AliasMatch ^/share(.*) /mnt/file_server$1public_html

It doesn't seem to understand since my error.log shows that the apache server is looking for /var/www/share and not matching it to the Alias

Reading from ([http://httpd.apache.org/docs/2.0/mod/mod_alias.html](http://httpd.apache.org/docs/2.0/mod/mod_alias.html)) "This directive is equivalent to Alias, but makes use of standard regular expressions, instead of simple prefix matching. The supplied regular expression is matched against the URL-path, and if it matches, the server will substitute any parenthesized matches into the given string and use it as a filename. For example, to activate the /icons directory, one might use:"

I set up a test.  I have two folders, /var/www/test and /var/www/test2.  Test 2 contains a html that displays "redirection success".  I pretended that test was your department, and test 2 the /mnt/file etc:

AliasMatch ^/test(.*) /var/www/test2$1

When I went to my_ip/test it directed me to test2.

I almost reckon you could simply do it with a normal Alias.  However when using this AliasMatch my_ip/test2 threw back a 404...but then again I haven't had much experience with AliasMatch so I don't know why that is...time to check the logs!

With regards to $1, if I didn't have that appended and tried to go to my_ip/test, logs showed:  /var/www/favicon.ico...

Cheers, All the best!

---

### Post by nkassi on 2007-07-30
The $1 does indeed work when the AliasMatch is within the correct virtual host ;0) 

I put it in the wrong place and it worked all along. 

Thanks for the help.

---

### Post by murraymca on 2007-07-30
:)

---

