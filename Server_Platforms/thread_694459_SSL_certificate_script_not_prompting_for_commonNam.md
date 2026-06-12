---
title: "SSL certificate script not prompting for commonName"
date: 2008-02-12
forum: Server Platforms
---

### Post by stiev3 on 2008-02-12
I'm configuring a private svn repository via dav svn.  Everything has gone flawlessy up to generating my ssl ceritificate.

For some reason, I am not prompted for my commonName when I run the script "apache2-ssl-certificate". 

For browsing the repository, it's okay, but for making a checkout I get the error: 
```
svn: PROPFIND request failed on '/svn/test/trunk'
svn: PROPFIND of '/svn/test/trunk': Server certificate was missing
commonName attribute in subject name (https://localhost)
```


Any ideas on how to either ignore the common name error or get the script to prompt me for one?

Script looks like:
```
#!/bin/sh -e

if [ "$1" != "--force" -a -f /etc/apache2/ssl/apache.pem ]; then
  echo "/etc/apache2/ssl/apache.pem exists!  Use \"$0 --force.\""
  exit 0
fi

if [ "$1" = "--force" ]; then
  shift
fi     

echo
echo creating selfsigned certificate
echo "replace it with one signed by a certification authority (CA)"
echo
echo enter your ServerName at the Common Name prompt
echo
echo If you want your certificate to expire after x days call this programm 
echo with "-days x" 

# use special .cnf, because with normal one no valid selfsigned
# certificate is created

export RANDFILE=/dev/random
openssl req $@ -config /usr/share/apache2/ssleay.cnf \
  -new -x509 -nodes -out /etc/apache2/ssl/apache.pem \
  -keyout /etc/apache2/ssl/apache.pem
chmod 600 /etc/apache2/ssl/apache.pem
ln -sf /etc/apache2/ssl/apache.pem \
  /etc/apache2/ssl/`/usr/bin/openssl \
  x509 -noout -hash < /etc/apache2/ssl/apache.pem`.0
```

---

