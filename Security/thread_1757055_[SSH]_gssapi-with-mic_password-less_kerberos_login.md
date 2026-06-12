---
title: "[SSH] gssapi-with-mic password-less kerberos login"
date: 2011-05-13
forum: Security
---

### Post by batrick on 2011-05-13
I'm trying to login to a server using gssapi-with-mic authentication against one of my school's machines that supports this mode of authentication. I have these kerberos packages installed:


batrick@menzoberranzan:~$ dpkg -l | grep krb
ii  krb5-config                          2.2                                               Configuration files for Kerberos Version 5
ii  krb5-multidev                        1.8.1+dfsg-5ubuntu0.7                             Development files for MIT Kerberos without Heimdal conflict
ii  krb5-user                            1.8.1+dfsg-5ubuntu0.7                             Basic programs to authenticate using MIT Kerberos
ii  libgssapi-krb5-2                     1.8.1+dfsg-5ubuntu0.7                             MIT Kerberos runtime libraries - krb5 GSS-API Mechanism
ii  libkrb5-3                            1.8.1+dfsg-5ubuntu0.7                             MIT Kerberos runtime libraries
ii  libkrb5-dev                          1.8.1+dfsg-5ubuntu0.7                             Headers and development libraries for MIT Kerberos
ii  libkrb5support0                      1.8.1+dfsg-5ubuntu0.7                             MIT Kerberos runtime libraries - Support library
ii  openafs-krb5                         1.4.12.1+dfsg-2                                   AFS distributed filesystem Kerberos 5 integration

Using this version of ssh:

batrick@menzoberranzan:~$ ssh -v
OpenSSH_5.5p1 Debian-4ubuntu5, OpenSSL 0.9.8o 01 Jun 2010


I'm running this command:

batrick@menzoberranzan:~$ ssh -vvv -o PreferredAuthentications=gssapi-with-mic host.nd.edu

I get the following output:

[...]
debug1: Authentications that can continue: publickey,gssapi-with-mic,password
debug3: start over, passed a different list publickey,gssapi-with-mic,password
debug3: preferred gssapi-with-mic
debug3: authmethod_lookup gssapi-with-mic
debug3: remaining preferred: 
debug3: authmethod_is_enabled gssapi-with-mic
debug1: Next authentication method: gssapi-with-mic
debug1: Unspecified GSS failure.  Minor code may provide more information
Server host/host.nd.edu@ND.EDU not found in Kerberos database

debug1: Unspecified GSS failure.  Minor code may provide more information
Server host/host.nd.edu@ND.EDU not found in Kerberos database

debug1: Unspecified GSS failure.  Minor code may provide more information


debug2: we did not send a packet, disable method
debug1: No more authentication methods to try.
Permission denied (publickey,gssapi-with-mic,password).




After googling around a lot I can't seem to find an appropriate solution to this.

---

### Post by batrick on 2011-05-13
Here's my krb5.conf attached.

---

