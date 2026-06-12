---
title: "Apache no longer starting unattended after reboot"
date: 2010-11-18
forum: Server Platforms
---

### Post by NDLunchbox on 2010-11-18
I have an Ubuntu 10.04.1 AMD64 server running Apache with SSL.  In the past, even though I have a passphrase on my key file, I have only needed it if I manually restarted Apache2, never after reboot.

I recently switched from a self-signed cert to one from a CA.  I'm not sure if this is what caused it, I also installed a few packages (AWStats, PHPSysInfo and Munin) that all interact with the webserver.

Anyway, I just noticed that now after a reboot Apache starts but doesn't work.  I need to kill that process and start a new one with the passphrase (maybe on the console it is prompting me, I mainly use SSH access since the server is headless).

Why did Ubuntu used to 'remember' the passphrase on the self-signed cert but now I need to provide it?

Is there somewhere I can update it?

My sever auto-updates so it would be annoying to have this thing go down regularly after a patch that requires a reboot.

Thanks!

---

### Post by NathanBC on 2010-11-19
Have you verified in the logs that it is the missing pass-phrase that is stopping Apache from loading properly?

---

### Post by NDLunchbox on 2010-11-19
> **NathanBC said:**
> Have you verified in the logs that it is the missing pass-phrase that is stopping Apache from loading properly?

If I try to restart Apache after reboot, here is the error I get:
```
$ sudo /etc/init.d/apache2 restart
[sudo] password for xxxxxxx:
 * Restarting web server apache2                                                                                              (98)Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs

```

So I kill and restart with password.

Here are the apache2 error logs:
```
[Fri Nov 19 16:14:01 2010] [notice] caught SIGTERM, shutting down

[Fri Nov 19 16:18:34 2010] [error] Init: Private key not found
[Fri Nov 19 16:18:34 2010] [error] SSL Library Error: 218710120 error:0D094068:asn1 encoding routines:d2i_ASN1_SET:bad tag
[Fri Nov 19 16:18:34 2010] [error] SSL Library Error: 218529960 error:0D0680A8:asn1 encoding routines:ASN1_CHECK_TLEN:wrong tag
[Fri Nov 19 16:18:34 2010] [error] SSL Library Error: 218595386 error:0D07803A:asn1 encoding routines:ASN1_ITEM_EX_D2I:nested asn1 error
[Fri Nov 19 16:18:34 2010] [error] SSL Library Error: 218734605 error:0D09A00D:asn1 encoding routines:d2i_PrivateKey:ASN1 lib
[Fri Nov 19 16:18:59 2010] [warn] RSA server certificate CommonName (CN) `www.xxxxxxx.net' does NOT match server name!?
[Fri Nov 19 16:18:59 2010] [notice] Digest: generating secret for digest authentication ...
[Fri Nov 19 16:18:59 2010] [notice] Digest: done
[Fri Nov 19 16:18:59 2010] [warn] RSA server certificate CommonName (CN) `www.xxxxxxx.net' does NOT match server name!?
[Fri Nov 19 16:18:59 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.5 with Suhosin-Patch mod_ssl/2.2.14 OpenSSL/0.9.8k configured -- resuming normal operations

```

---

### Post by SeijiSensei on 2010-11-19
Look at the first error; Apache cannot find your private key.

Now I haven't requested a certificate for a while, but as I recall, you have to generate a Certificate Signing Request and sign it with your server's private key.  Apache needs to know where the key is in order to decrypt the certificate you received.  Your certificate provider's website should have the instructions you need.

It also appears as though the certificate is for a server with a name other than the one it's on.  That could be a consequence of not being able to decrypt the certificate, or the names may actually not match.

---

### Post by NDLunchbox on 2010-11-20
> **SeijiSensei said:**
> Look at the first error; Apache cannot find your private key.

Now I haven't requested a certificate for a while, but as I recall, you have to generate a Certificate Signing Request and sign it with your server's private key.  Apache needs to know where the key is in order to decrypt the certificate you received.  Your certificate provider's website should have the instructions you need.

It also appears as though the certificate is for a server with a name other than the one it's on.  That could be a consequence of not being able to decrypt the certificate, or the names may actually not match.

I think that message just means it can't decrypt the private key.  It finds it ok (it starts once I put in the past phrase).

To test, I moved the key to a file and gave it www-data read rights to it (in the etc/ssl/private folder, only root has access) - same error.

This time I checked the console, sure enough I was getting prompted for the passphrase (only the input was stuck, this seems to be a different problem based on prior searches).

```
* Starting web server apache2
Apache/2.2.14 mod_ssl/2.2.14 (Pass Phrase Dialog)
Some of your private key files are encrypted for security reasons.
In order to read them you have to provide the pass phrases.

```

Correct that the name on the cert ([www.domain.com](www.domain.com)) and the server name (hostname.domain.com) don't match... should that really matter?

Basically, without taking off the passphrase, is there a secure way to have the server pass it automatically at boot time?

If not, I will have to write a script that emails me when the server reboots so I can remember to go in and enter the password I guess...

---

### Post by SeijiSensei on 2010-11-20
You can decrypt the key to avoid needing to enter it when rebooting.  See [this](http://www.linuxsecurity.com/content/view/117549/49/) or one of the other many articles on this subject. I've done this myself to avoid exactly the problem you describe.  I've been running servers for a long time now and worrying about whether someone will break in, get root, and then use my unencrypted key for some unspecified nefarious purpose falls *very* far down my list of concerns.

Yes, it matters a lot that the names don't match.  Site users will be told there's a problem with your certificate and be required to accept it manually.  Your certificate is for that server with the hostname you used when sending the request.  Unless you have a "wildcard" certificate, a mismatch between the server names will cause problems.

---

### Post by NDLunchbox on 2010-11-20
> **SeijiSensei said:**
> You can decrypt the key to avoid needing to enter it when rebooting.  See [this](http://www.linuxsecurity.com/content/view/117549/49/) or one of the other many articles on this subject. I've done this myself to avoid exactly the problem you describe.  I've been running servers for a long time now and worrying about whether someone will break in, get root, and then use my unencrypted key for some unspecified nefarious purpose falls *very* far down my list of concerns.

Yes, it matters a lot that the names don't match.  Site users will be told there's a problem with your certificate and be required to accept it manually.  Your certificate is for that server with the hostname you used when sending the request.  Unless you have a "wildcard" certificate, a mismatch between the server names will cause problems.

When I sent the request I used the public (not private) hostname.  No browser errors when hitting the SSL site - it's just the cert hostname (www) doesn't match the internal (somename) hostname of the server...

I may decrypt the key - you're right, it seem slim that it will be compromised since you need root access to read it.
Thanks!

---

### Post by SeijiSensei on 2010-11-20
> **NDLunchbox said:**
> When I sent the request I used the public (not private) hostname.  No browser errors when hitting the SSL site - it's just the cert hostname (www) doesn't match the internal (somename) hostname of the server...

I may decrypt the key - you're right, it seem slim that it will be compromised since you need root access to read it.
Thanks!

I'd still give it 0440 permissions after decrypting with root:www-data as the owner and group, or 0400 permissions with www-data as the owner.

---

### Post by NDLunchbox on 2010-11-30
Thank you, I took your advice and decrypted the key.  If I have it correct, the security implecation is that if:
1) Someone gained access to your server
2) Gained root permissions
3) Copied your keys
then they could sniff and decrypt your SSL traffic.  Given this I hardly see this as an insecure setup and think the Ubuntu documentation needs to tone down the warnings.

---

