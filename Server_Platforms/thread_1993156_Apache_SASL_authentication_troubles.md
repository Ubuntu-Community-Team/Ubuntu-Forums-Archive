---
title: "Apache SASL authentication troubles"
date: 2012-06-01
forum: Server Platforms
---

### Post by stonebit on 2012-06-01
I'm trying to authenticate access to my website with SASL. I've got SASL installed and the module is enabled for apache. Here are the steps i've got so far:

# apt-get install libapache2-mod-authn-sasl
# a2enmod authn_sasl
# adduser www-data sasl
# testsaslauthd -u [user@domain] -p [password]
 ^- that returns OK: Success

default-ssl has this:
  <Location /private>
    AuthSaslPwcheckMethod saslauthd
    AuthSaslAppname httpd
    AuthSaslRealm [ADrealm]
    AuthType Basic
    AuthBasicProvider sasl
    AuthBasicAuthoritative On
    AuthName "enter as username@domain."
    require valid-user
  </Location>

When i goto [https://server/private](https://server/private), i am challenged, but authentication always fails. Apache does start without errors as well.

By the way, i'm authenticating into the box via ssh successfully using likewise-open.

---

