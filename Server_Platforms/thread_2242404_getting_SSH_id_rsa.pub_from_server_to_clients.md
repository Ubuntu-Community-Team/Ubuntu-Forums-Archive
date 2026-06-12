---
title: "getting SSH id_rsa.pub from server to clients?"
date: 2014-09-01
forum: Server Platforms
---

### Post by scojopa on 2014-09-01
I am a newbie linux installing my first linux server. 

I have configured SSH, using keys. I have generated the id_rsa.pub file 

I wanted to copy it to my client machine - how can I do this? I can copy to usb while on the server. But does not show via usb when on the client. 

the import option is grayed out when trying to install the id_rsa -= 

Can someone help me with this?
Thanks,

---

### Post by papibe on 2014-09-01
Hi scojopa.

The common procedure is to create the key pair on the client, and then transfer the public key to the server.

In your current situation, you can use sftp or scp to retrieve the private key from the server to the client. Don't disable ssh password login just yet. Do the transfer and once you've tested to key based login process, disable password login to tighten security.

Here a tutorial that can be helpful: [SSH/OpenSSH/Keys]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys").

Let us know how it goes.
Regards.

---

### Post by nerdtron on 2014-09-01
Copy the content of the id_rsa.pub of the server and paste it inside the **~/.ssh/authorized_keys** file on the client computers. If the authorized_keys file doesn't exists on that location you can create it.

---

### Post by scojopa on 2014-09-02
Thank for the responses. Can you clarify - I was under the impression I would generate the pub key on the server (machine to host the SSH connections) and then send the pub key to the client that was allowed to connect. 

My issue was I do not have connectivity to the server from the client - I wanted to send the key to the client and could not figure out how.

---

### Post by steeldriver on 2014-09-02
The **private **key stays with you (the client) - the **public **key goes on the server - typically, you would generate the key pair on the client side and then push the public key down to the server, however you should be able to use scp (with password authentication) to **pull **the private key from the server where you generated it - you should then probably delete the original from the server side

---

### Post by Hugo_Serrano on 2014-09-02
Hi!

You should understand how it works (the concepts), but to setup on between 2 ubuntu machines do the following on the client (not sure if this is what you want):

#ssh[hit double tab]
you can see the option ssh-* commands

So here you can generate a certificate for your client:
#ssh-keygen
You can use the default stuff... if you choose a password, you will need to type it every time...

Then, to copy the pub cert into the server:

#ssh-copy-id user@server
Password:
This will add your pub key on the file ~/.ssh/authorized_keys in the server.

After this you should be able to login into the server without password. If you want to connect from other clients, you need to run both commands on every client again, so you will have one line per client in authorized_keys on you server.

Cheers,
Hugo.

---

### Post by nerdtron on 2014-09-02
> **Hugo_Serrano said:**
> Hi!

You should understand how it works (the concepts), but to setup on between 2 ubuntu machines do the following on the client (not sure if this is what you want):

#ssh[hit double tab]
you can see the option ssh-* commands

So here you can generate a certificate for your client:
#ssh-keygen
You can use the default stuff... if you choose a password, you will need to type it every time...

Then, to copy the pub cert into the server:

#ssh-copy-id user@server
Password:
This will add your pub key on the file ~/.ssh/authorized_keys in the server.

After this you should be able to login into the server without password. If you want to connect from other clients, you need to run both commands on every client again, so you will have one line per client in authorized_keys on you server.

Cheers,
Hugo.

I think this one is what you need. I forgot that this is ubuntu. No need to copy keys manually. Just these commands will do the passwordless login.

---

### Post by scojopa on 2014-09-05
Thank folks  - got it working.

---

