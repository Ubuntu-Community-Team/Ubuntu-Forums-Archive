---
title: "php passtrhu and utf-8"
date: 2011-02-17
forum: Server Platforms
---

### Post by JeanCr on 2011-02-17
Hello,

I am installing a machine with ubuntu to replace my windows based server and I am having a little problem with utf-8.
Normally everyting is Ok, special characters are displayed as they should.

Now I have this little home made c program that outputs the character ° among other things.

```
int main(int argc, char *argv[])
{ 
cout << "hello world °°°  ";
return 0;
}
```

If I call this program with bash it outputs the ° correctly.
However if I call it from php with passthru it outputs Â° in stead.

```
<? passthru("/var/www/bin/prog"); ?>
```

In windows I have in httpd.conf: AddDefaultCharset ISO-8859-1, I added that to ubuntu's /etc/apache2/sites-available/default but it does not help.

Just to be sure, in index.php I also have: <meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1">

How do I get rid of the extra Â?

Thanks.

Edit: solved by adding 'AddDefaultCharset UTF-8' to '/etc/apache2/sites-available/default'.

---

