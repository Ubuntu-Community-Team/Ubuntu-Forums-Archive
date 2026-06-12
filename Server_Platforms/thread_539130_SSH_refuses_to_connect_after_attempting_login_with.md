---
title: "SSH refuses to connect after attempting login with putty"
date: 2007-08-30
forum: Server Platforms
---

### Post by FANTAchrist on 2007-08-30
I've installed openssh and I'm trying to use it for remote administration and either SCP or SFTP with a putty key I've generated. I've tested logging in from  linux  with the openssh key and it was successful, but as soon as I go over to a windows machine with the putty key I get a connection refused message in putty, I then go back over to the linux box to attempt to login and it gives me connection refused at the port I have it set to BUT that's not all it's stopped using the sshd_config and started using the ssh_config. 

 Any ideas?

---

### Post by uuesley on 2007-08-30
are you using the openssh key to generate a key for putty with puttygen?

has the key been added to your authorized_keys file?

isnt ssh_config the default for the linux client, while sshd_config is for the service?...dont think that the service just started using the wrong config file...

might want to double-check your sshd_config (AllowUses, AuthorizedKeysFile), restart the service, and try again...dont forget to check the logs for hints to the problem...

---

### Post by HermanAB on 2007-08-30
Debug with:
ssh -vvv user@server

Cheers,

Herman

---

### Post by FANTAchrist on 2007-08-31
Thanks for your help I figured it out. I didn't have  ListenAddress set right.

---

