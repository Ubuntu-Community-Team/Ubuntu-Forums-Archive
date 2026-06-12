---
title: "Kerberized SSH Fails: &quot;Unknown Key table type&quot;"
date: 2015-03-08
forum: Security
---

### Post by peridian on 2015-03-08
Hi,

I've got something weird going on.  Two Ubuntu server 14.04.2 installs, both configured to use LDAP-Kerberos-GSSAPI for authentication.  That works fine through PAM, so using the users from LDAP, I can log in with the Kerberos passwords.

I then updated the sshd_config files on both servers to enable use of GSSAPI, so that Kerberos tickets on the client would remove the need to enter a password.

This works on one server, but not on the other.  As far as I can see, the /etc/ssh/* and /etc/pam.d/* files are all identical.

When adding -vvv on the client, I can see that it repeatedly sends the gssapi-with-mic packets and then gives up and drops through to regular password attempt.

Raising the sshd LogLevel to DEBUG, I can see on the first GSSAPI call, a generic GSSAPI failure error with the minor error code "Unknown Key table type"  What does this mean?

I've tried regenerating the /etc/krb5.keytab file with the host/fqdn entry.  I've also run "klist -e -k /etc/krb5.keytab" on both servers, they both have the correct host/fqdn entry and the exact same encryption types.  They both have the file as owned by root:root and with 640 permissions.

On the client side, I do still see a successfully obtained host/fqdn ticket for the server, so it's as if ssh can actually access the file and issue a ticket, but something is then going wrong.

Any help would be appreciated.

Regards,
Rob.

---

### Post by peridian on 2015-03-08
There was a difference, turns out I was looking in the wrong place.

From other articles, it appears there is a bug in kerberos when the 'default_keytab_name' option is specified in the /etc/krb5.conf file.  This is apparently the usual problem with any kerberos error with "Unknown Key table type" in.

Removing this line from my conf file allowed the tickets to work as expected.  Not sure why I specified it on that one machine, wondering if something else will break now...

Regards,
Rob.

---

