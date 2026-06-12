---
title: "ssh conn/auth/agent problem"
date: 2009-09-04
forum: Server Platforms
---

### Post by elitium on 2009-09-04
Hi
I'm trying to set up an ssh server or sftp. I've made some keys with ssh-keygen. configured sshd_conf with protocol 2, allow certain users. I've tried to copy the keys to a windows client, saved them through putty as (filename.ppk) but when i try to connect i can't.

From my ubuntu ssh-server i get:
"Could not open a connection to your authentication agent." when i run ssh-add
(I'm supposed to run this to se if the ssh is ok,right? I'm not so good at this)

What can I do to get my ssh up and running? I've googled and have only found this command: eval ssh-agent, and according to that site it will solve every problem I'm having... which it dosen't....

I've followed cromwells guide [http://cromwell-intl.com/unix/ssh.html](http://cromwell-intl.com/unix/ssh.html) and the ssh worked a couple of days ago (I didn't have problem with starting the ssh, but with connecting then...)

Regards

---

### Post by Bachstelze on 2009-09-04
> **elitium said:**
> I've tried to copy the keys to a windows client, saved them through putty as (filename.ppk) but when i try to connect i can't.

What happens, exactly? Anyway, I suggest you first try to connect to your SSH server using simple password-based authentication. If that works, you can proceed to setting up key-based authentication.

---

### Post by elitium on 2009-09-10
Hi again
Thanks for the reply.
I've done as you told me to, setup it only using username+passwd, and it works.
But now I'm trying to use key-based authentication and I can't get it to work.

I've made a key using ssh-keygen, saved it on the server /home/[user]/.ssh filename rsa_id rsa_id.pub, password set on the keys.

And now I want to copy it to the clients (which using Windows XP), so I setup samba, copying /home/[user]/.ssh > /etc/samba/share, chmod 777 on (samba share, .ssh, rsa_id, rsa_id.pub) Is this a good way to do it? or do I corupt the files by doing chmod 777?

ON WINDOWS
copy the two keys, in Putty saves it as [filename].ppk, when using WinSCP with the key I get "Server refused our key". Using Filezilla, Filezilla doesn't support password protected keys it says, automaticly converts it to a key that it can use, try to connect but can't authenticate.

sshd_config (brief)
```
RSAAuthentication yes
PubkeyAuthentication yes
AuthorizedKeysFile    /home/[user]/.ssh/
PasswordAuthentication no
ChallengeResponseAuthentication no
RhostsRSAAuthentication no
```

---

### Post by Bachstelze on 2009-09-10
> **elitium said:**
> 
copy the two keys, in Putty saves it as [filename].ppk

Do you just rename id_rsa to something like id_rsa.ppk? If that's what you're doing, that's your problem. You must:

1) Run puttygen
2) Click Conversions > Import key
3) Enter your passphrase
4) Click "Save private key"

It will save it as a PPK file, which is the one you must use in putty/winscp/filezilla.

---

### Post by elitium on 2009-09-11
No I have done as you discribed it, converting and saved it as private key.
But I still get "server refused our key" inWinSCP.
"No supported authentication method available" in FileZilla

And another thing I'm wondering about, I always get prompted to fill in user name when trying to connect. Is it the client program (WinSCP, FileZilla) that always ask or do I have to change something in my sshd_config file? or am I suppose to get the prompt with my ssh server settings? it doesn't matter what I type, it doesn't complain on being the wrong user even if I type in a none existing user...

I've followed this guide:
[http://sial.org/howto/openssh/publickey-auth/](http://sial.org/howto/openssh/publickey-auth/)
And it states that "OpenSSH may also refuse to support public key authentication if the file permissions are too open"
And when copying the keys to be able to share them to windows i used chmod 777.
Is this a right way to have them moved to the windows computer, are there some other way? I have the feeling I corrupt the keys by doing that.

One more thing that I had missunderstood and which I've changed now was that I had not cat id_rsa.pub into authorized_keys which I thought was a folder instead of a file.
So now I have the info in id_rsa.pub in my authorized_keys file, and changed the sshd_config to [FONT=monospace]AuthorizedKeysFile /home/[user]/.ssh/authorized_keys
[/FONT]

---

