---
title: "private ssl certificates : security warnings to windows clients"
date: 2013-08-13
forum: Server Platforms
---

### Post by sophie_horner on 2013-08-13
Hi,
When I'm using webmin (1.630) to access server through LAN, even if I install the certificate and key given by webmin, I still can't get rid of the rude message of my browser warning me about security...
I wonder if either I haven't installed the certification properly on the windows client either it's just impossible to convince windows system that webmin is safe because the key is private not Verisign.
I'm very much unfamiliar to SSL policies...

Any comment will help...
Thanks.

---

### Post by Cheesemill on 2013-08-13
Does the URL that you use to access your server match the Common Name of the certificate?

Even with the correct certificate on the client machines you will still get an error if the names don't match.

---

### Post by nerdtron on 2013-08-13
Private SSL? You created it yourself or did you bought the certificate?
If it is a self generated certificate you'll never get rid of the security warning.

---

### Post by Cheesemill on 2013-08-13
> **nerdtron said:**
> If it is a self generated certificate you'll never get rid of the security warning.

Unless you install your signing certificate on your clients browsers before connecting, exactly as the OP is trying to do.

I use self signed certificates at work all the time and none of the users ever get a warning as the company's signing certificate is installed on all of the workstations.

---

### Post by sophie_horner on 2013-08-13
Thanks very much for the quick response. 
I'll try and get the common name to match although I'm not sure how to go about it yet...
I'll look around the webmin config for the right certificate settings. 
Reassuring to know that I just haven't done it right yet. *noob blush*
Ok, I'll come back and post the proper way to generate the certificate if I manage it.
Thanks again.

---

