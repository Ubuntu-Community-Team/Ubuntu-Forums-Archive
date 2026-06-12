---
title: "SSLError when trying to download using u1_downloader"
date: 2014-06-18
forum: Ubuntu One (CLOSED)
---

### Post by finger51 on 2014-06-18
I get the prompt for email and password but then:
```

Traceback (most recent call last):
  File "<string>", line 336, in <module>
  File "<string>", line 308, in main
  File "<string>", line 150, in get_session
  File "<string>", line 129, in _get_token
  File "/home/matiasb/canonical/u1-downloader/build/u1_downloader/out00-PYZ.pyz/requests.api", line 88, in post
  File "/home/matiasb/canonical/u1-downloader/build/u1_downloader/out00-PYZ.pyz/requests.api", line 44, in request
  File "/home/matiasb/canonical/u1-downloader/build/u1_downloader/out00-PYZ.pyz/requests.sessions", line 383, in request
  File "/home/matiasb/canonical/u1-downloader/build/u1_downloader/out00-PYZ.pyz/requests.sessions", line 486, in send
  File "/home/matiasb/canonical/u1-downloader/build/u1_downloader/out00-PYZ.pyz/requests.adapters", line 385, in send
requests.exceptions.**SSLError: [Errno 185090050**] _ssl.c:344: error:0B084002:x509 certificate routines:X509_load_cert_crl_file:system lib

```

I've got hundreds of pics from my camera on this thing... would be a bummer to have to DL them one by one.

---

### Post by dcharbonnel on 2014-06-19
> **finger51 said:**
> I get the prompt for email and password but then:
```

Traceback (most recent call last):
  File "<string>", line 336, in <module>
  File "<string>", line 308, in main
  File "<string>", line 150, in get_session
  File "<string>", line 129, in _get_token
  File "/home/matiasb/canonical/u1-downloader/build/u1_downloader/out00-PYZ.pyz/requests.api", line 88, in post
  File "/home/matiasb/canonical/u1-downloader/build/u1_downloader/out00-PYZ.pyz/requests.api", line 44, in request
  File "/home/matiasb/canonical/u1-downloader/build/u1_downloader/out00-PYZ.pyz/requests.sessions", line 383, in request
  File "/home/matiasb/canonical/u1-downloader/build/u1_downloader/out00-PYZ.pyz/requests.sessions", line 486, in send
  File "/home/matiasb/canonical/u1-downloader/build/u1_downloader/out00-PYZ.pyz/requests.adapters", line 385, in send
requests.exceptions.**SSLError: [Errno 185090050**] _ssl.c:344: error:0B084002:x509 certificate routines:X509_load_cert_crl_file:system lib

```

I've got hundreds of pics from my camera on this thing... would be a bummer to have to DL them one by one.

I've the same error, somebody can help us ?

---

### Post by finger51 on 2014-06-19
I sent in the output above to ubuntu support. This is the response

[INDENT][I]It might be some issue with problems on your certificate.
can you please either try to run the command as root or to make sure
the cert has the right permissions by writing in the terminal (before
you try to run the command) "chmod 644 cacert.pem" and hitting enter?

Please let me know if this works[/I][/INDENT]

It didn't work (same error) so no luck there. I did respond to let them know that it didn't work but haven't heard back yet.

---

### Post by nealmcb on 2014-06-20
I got the same error.  It was because I only extracted the u1_downloader executable from the tar.gz file they provided.   It went away when I also extracted the cacert.pem file from the same archive.

But now I get __main__.AuthenticationError: Authentication failed  even though I think I'm entering the right credentials.

I finally got past that - probably confused by what I thought were unrelated changes due to the many services that use the openid credentials.
Now it is downloading stuff, and noting "E: /content/~/Ubuntu One/......file: File download failed." from time to time.  But those errors are lost in the overall flow of status messages for each file.

Also: no man page, no hint beforehand of where it plans to put the files, ....

Not very impressive UX here, I'm afraid.....

**Update**:

There is a lot of helpful info online.  I wish they would reference the documentation for u1_downloader from their web page, and when it is run.....

  [https://help.ubuntu.com/community/U1/Downloader](https://help.ubuntu.com/community/U1/Downloader)

---

