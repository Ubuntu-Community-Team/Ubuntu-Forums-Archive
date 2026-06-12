---
title: "Link system accounts to .htaccess"
date: 2011-05-07
forum: Server Platforms
---

### Post by DAcre on 2011-05-07
Hi
 
Is it possible to link system user accounts to .htaccess? Instead of having to add each user individually with htpasswd?
 
Thanks

---

### Post by volkswagner on 2011-05-07
I'm not sure how to do what you request.

Perhaps a different authentication mechanism will help.  Such as [authz_user ]("http://www.howtoforge.com/apache_mod_auth_shadow_debian_ubuntu")or [mod_auth_shadow]("http://httpd.apache.org/docs/2.2/mod/mod_authz_user.html").

One more [link]("http://davidlaing.com/2008/12/27/apache2-on-ubuntu-804lts-restrict-access-to-pam-authenticated-users/").

---

### Post by SeijiSensei on 2011-05-07
It's supposed to be possible to use [PAM]("http://en.wikipedia.org/wiki/Pluggable_Authentication_Modules") (the standard Linux authentication method) as an authenticator.  See [this description](http://code.google.com/p/mod-auth-external/) for an overview.  I've not tried this, so I can't vouch for this method.

---

### Post by Lars Noodén on 2011-05-07
Just a thought on encryption.  Be sure you are using HTTPS (HTTP+SSL/TLS) and disallow authentication authentication over HTTP.  Otherwise, the valuable system passwords get sent unencrypted over the net.

---

