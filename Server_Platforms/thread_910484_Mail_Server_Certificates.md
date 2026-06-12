---
title: "Mail Server Certificates"
date: 2008-09-04
forum: Server Platforms
---

### Post by PrinceArithon on 2008-09-04
OK here is the deal.  I am working on a mail server that the certificate has expired.  The certificate was a self written certificate as far as what I was told.  Anyway I tried to create a new one buy typing this in the terminal:

openssl x509 -req -days 999 -in server.csr -signkey server.key -out server.crt

After I input that into the terminal I got an error telling me that the server.csr directory doesn't exist.

So I'm kinda stuck, I can't seem to find anything that can help me to get past this.

If there is a better way of doing it than what I am trying, please let me know.

Oh, and I have no idea which version of ubuntu server that I'm working on.

Thanks!!

---

### Post by HermanAB on 2008-09-04
I think that you need to make a new CSR first, since the error says that it doesn't exist.

Cheers,

Herman

---

### Post by Dr Small on 2008-09-04
Hi, have you read this guide?
[https://help.ubuntu.com/community/OpenSSL](https://help.ubuntu.com/community/OpenSSL)

---

### Post by PrinceArithon on 2008-09-04
Dr. Small this is really good.  I didn't find this before, I had found something else as I mentioned above.  This seems more involved than what I had before, but it seems like it may work.  I will probably be trying this tomorrow or next week sometime.

---

### Post by Dr Small on 2008-09-04
> **PrinceArithon said:**
> Dr. Small this is really good.  I didn't find this before, I had found something else as I mentioned above.  This seems more involved than what I had before, but it seems like it may work.  I will probably be trying this tomorrow or next week sometime.
I've created many certificates for my server by following that guide, so I thought it might help you :)

---

### Post by PrinceArithon on 2008-09-04
My last question is, do I need to delete the first certificate first??  Or can I just make the new one and all will be fine??  Cuz to be honest I don't know where the original certificate is located in the server in the first place.

---

### Post by father time on 2008-09-04
Message Deleted.

---

### Post by PrinceArithon on 2008-09-05
Thanks so much, it helps.

---

