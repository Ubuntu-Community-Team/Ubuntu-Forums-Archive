---
title: "Question on apache SSL config"
date: 2008-09-25
forum: Server Platforms
---

### Post by rkleemann on 2008-09-25
Hi,

I've installed Ubuntu Server 8.0.4. I wanted to have a test SSL configuration (not with a real commercial certificate).

Is there a test certificate that I can use?

How would I configure /etc/apache2/mods-enabled/ssl.conf in order to make https work? Right now if I try to access [https://myserver](https://myserver) it returns an error

SSL received a record that exceeded the maximum permissible length.

(Error code: ssl_error_rx_record_too_long)

And the error.log just has:
Invalid method in request \x16\x03\x01

Thanks for any help
Ricardo

---

### Post by windependence on 2008-09-25
Here is how to create a self-signed certificate and install it.

[https://help.ubuntu.com/8.04/serverguide/C/certificates-and-security.html](https://help.ubuntu.com/8.04/serverguide/C/certificates-and-security.html)

-Tim

---

