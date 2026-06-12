---
title: "why SSL 128 bit = RSA 1024 bit?"
date: 2008-06-22
forum: Server Platforms
---

### Post by crixtiano on 2008-06-22
My SSL certificate was generated using RSA 1024 bit. My certificate is know as "128 bit".

Why SSL certificate 128 bit are made using RSA 1024 bit?

:confused: Why 124 = 1024 ? :confused:

Thank you.

Cristiano

---

### Post by HalPomeranz on 2008-06-22
The certificate is only used for the initial authentication piece of the SSL transaction.  The encrypted session itself is a separate animal and uses a 128-bit stream cipher.

---

