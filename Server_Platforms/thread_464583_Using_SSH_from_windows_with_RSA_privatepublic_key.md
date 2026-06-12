---
title: "Using SSH from windows with RSA private/public key"
date: 2007-06-04
forum: Server Platforms
---

### Post by dfreer on 2007-06-04
Hi everyone,

    So I need to do some work on my server with openssh installed from a windows client. I happen to really prefer the SSH client from here: [http://www.ssh.com/support/downloads/secureshellwks/non-commercial.html](http://www.ssh.com/support/downloads/secureshellwks/non-commercial.html) 

as it supports graphical file transferring between my windows and ubuntu boxen. PuTTy doesn't cut it for me.
    Anyways, I've used this SSH client in the past but never with RSA private/public key authentication, and I'm having a hard time trying to connect. It says it cannot open my file for reading, I thought this was a windows permission issue but I can open the file myself. I tried just copy+pasting the contents of id_rsa and id_rsa.pub into new files with the same names, and it still gives me that error. 

   I then tried PuTTy out, and I *think* I got putty to see my private key. However, when logging in just after it asked for my username putty just quits itself, no errors.

   I just need this to work temporarily so I can work from windows for a little bit... any ideas on programs to try? any way to validate that the private public key have the correct syntax?

There is so far no relevent information on /var/log/auth.log on the SSH server.

---

### Post by dfreer on 2007-06-22
here's one solution I found: use puttygen.exe to create a .pki (putty private/public keypair file) from the imported id_rsa private key. but I'm still working on figuring how to do it with SSH client ;) so any help would be appreciated.

---

### Post by dmizer on 2007-06-22
your client of choice supports private/public keys.

just looked it up on the site you linked to under "documentation": [http://www.ssh.com/support/documentation/online/ssh/quickstart/52/ch04s03.html](http://www.ssh.com/support/documentation/online/ssh/quickstart/52/ch04s03.html)

---

### Post by dfreer on 2007-06-22
hmmm, but importing the id_rsa key generates an error stating the file cannot be read. I'll try fiddling with it some more, I'm thinking it has to be some sort of syntax error.
The reason I think it has to do with syntax is that when I try generating a new keypair with the SSH client, the file is in a different format.

---

### Post by dmizer on 2007-06-23
are you using the tectia app on both your client and your server?

it wouldn't surprise me if openssh-server doesn't agree with your choice of interface.

what error are you getting?  you might try searching the knowledge base for the error text: [https://support.ssh.com/rqcustomer/servlet/login](https://support.ssh.com/rqcustomer/servlet/login)

---

### Post by dfreer on 2007-06-23
openssh on my server, the SSH tectia client on my windows client box. thanks for the link, I'll check it out and see if it can help resolve this issue.

EDIT: SSH tectia works great with openssh when using the default username/password auth. it just really doesn't like to import my id_rsa key right now :(

---

### Post by netlogic on 2007-06-23
try this. it has a step by step instruction with graphics.

[http://www.aota.net/Telnet/puttykeyauth.php4](http://www.aota.net/Telnet/puttykeyauth.php4)

---

### Post by dfreer on 2007-06-23
> **netlogic said:**
> try this. it has a step by step instruction with graphics.

[http://www.aota.net/Telnet/puttykeyauth.php4](http://www.aota.net/Telnet/puttykeyauth.php4)

Thanks for the advice, but if you had read the thread you would've noticed I've solved the problem with putty using puttygen already, I'm now troubleshooting the SSH tectia client :p

AFAIK, tectia can't use the .pki files putty makes, although I have yet to put that to the test.

---

### Post by dmizer on 2007-06-24
you should generate your public and private keys with the tectia client according to these instructions: [http://www.ssh.com/support/documentation/online/ssh/quickstart/52/userauth-pk-gui.html](http://www.ssh.com/support/documentation/online/ssh/quickstart/52/userauth-pk-gui.html)

leave both the private key and a copy of the public key on your client, and load a copy of the public key on your server.
[COLOR="Red"]private[/COLOR] key > windows
[COLOR="Blue"]public[/COLOR] key > ubuntu server

for more information read this link carefully: [http://www.ssh.com/support/documentation/online/ssh/quickstart/52/ch04s03.html](http://www.ssh.com/support/documentation/online/ssh/quickstart/52/ch04s03.html)

i posted it earlier, there are links to how to make your keypair work.

---

### Post by dfreer on 2007-06-24
Yes, thanks for the links dmizer! I already read them, and I am considering just making a new keypair with the tectia client. And I know it says the client can import the keys, however in actual practice it is giving me an error. It probably is going to be something simple, like the permissions are wrong (not quite sure why they would be wrong on an XP machine), or perhaps it is of the wrong MIME type (should just be a plain text file). Anyways, I have been really busy and haven't had a chance to test my theories, so give me a couple days and I'll report back to you guys on what I got working :) Thanks again!

---

