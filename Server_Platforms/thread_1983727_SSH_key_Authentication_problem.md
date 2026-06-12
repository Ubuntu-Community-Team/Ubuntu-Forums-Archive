---
title: "SSH key Authentication problem"
date: 2012-05-20
forum: Server Platforms
---

### Post by LinuxTester on 2012-05-20
Hello, I am setting up an ssh tunnel for myself and a client of mine to access one of my machines. I have setup key authentication. My keys are configured correctly with 

ssh-keygen 
ssh-copy-id
Then i removed password authentication. I am able to access the server and tunnels fine. 

I am having a problem with my client and or friend though. his ssh-copy-id refused to copy over claiming that there was no identifcation. 

I decided to have him SCP the public key over and cat it into the authorized_users file.

I did the same with another machine and discovered a permissions issue on my end. i fixed the ssh permissions on the ubuntui server 

[http://www.noah.org/wiki/SSH_public_keys#Permission_problems_with_SSH](http://www.noah.org/wiki/SSH_public_keys#Permission_problems_with_SSH)

And on my test machine and then had my client run the same fix. worked for me not for him. He can authenticate correctly if i set password  authentication. Does anyone have an idea of where the problem lays?

P.S  my client is an advanced computer user but the issue could lay anywhere.

---

### Post by koenn on 2012-05-20
> I am having a problem with my client and or friend though. his ssh-copy-id refused to copy over claiming that there was no identifcation.
this resembles the error you typically get when you run ssh-copy-id pointing to an invalid or a non-existing file.


> I decided to have him SCP the public key over and cat it into the authorized_users file.
shouldn't that be the authorized_keys file ? 

> He can authenticate correctly if i set password authentication. Does anyone have an idea of where the problem lays?
see above.
once that is fixed, read the errors ssh shows, on screen or in the logs. 

> P.S my client is an advanced computer user but the issue could lay anywhere.
lol

---

### Post by CharlesA on 2012-05-20
> **koenn said:**
> 
shouldn't that be the authorized_keys file ? 


Yep.

If you want to use ssh-copy-id, you need password authentication enabled, so it can authenticate and add your key.

---

