---
title: "need help on encrypt password on ubuntu/mysql"
date: 2009-05-16
forum: Server Platforms
---

### Post by kustomjs on 2009-05-16
Hi Guys

I need to know what kind of encryption that ubuntu/mysql is using because I am trying to make a script for a database and I know that if I use regular md5 password like this:7b9f9e7f9eb41cbea2d1 and that password doesnt work but if I use this: tJhggTSs3Dotw  it works just fine.

because right now I got this code in there " $password = hash('md5', $_POST['password']);

but that code is giving me to long of password and I cant use it to login to my webmail that uses mysql.

now if I use this tool: [http://www.kxs.net/support/htaccess_pw.html](http://www.kxs.net/support/htaccess_pw.html)  then the password works.

---

