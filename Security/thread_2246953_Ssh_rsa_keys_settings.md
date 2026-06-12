---
title: "Ssh rsa keys settings"
date: 2014-10-04
forum: Security
---

### Post by drew26 on 2014-10-04
Hello, I am pretty new to ubuntu, I have to log in via ssh on a server with public/private RSA-keys. At the beginning, I did it with putty on windows, I created the two keys and so on...but now i'd want to do it on ubuntu, but I don't know where I have to put the private and the public key (which I've already communicated to the server). When I try to login I get the error: "Permission denied (publickey,gssapi-keyex,gssapi-with-mic)". What am I supposed to do?

---

### Post by Lars Noodén on 2014-10-04
The private key stays on your client, usually in the directory ~/.ssh/

The public key goes on the server you wish to connect to.  Specifically it goes in the file ~/.ssh/authorized_keys on a line by itself, the whole oublic key on a single line.  You can copy it to the server with the program ssh-copy-id.

---

### Post by drew26 on 2014-10-04
> **Lars Noodén said:**
> The private key stays on your client, usually in the directory ~/.ssh/

The public key goes on the server you wish to connect to.  Specifically it goes in the file ~/.ssh/authorized_keys on a line by itself, the whole oublic key on a single line.  You can copy it to the server with the program ssh-copy-id.

Thanks for your answer. The public key is already on the server I think, because with putty I am able to log in... About the private key, I just need to copy it in that folder?

---

### Post by Lars Noodén on 2014-10-04
> **drew26 said:**
> Thanks for your answer. The public key is already on the server I think, because with putty I am able to log in... About the private key, I just need to copy it in that folder?

Yes, or move it there.  The idea is that it should be somewhere you can find it easily but not where anyone else has a chance to read it.

---

### Post by drew26 on 2014-10-04
> **Lars Noodén said:**
> Yes, or move it there.  The idea is that it should be somewhere you can find it easily but not where anyone else has a chance to read it.

Ok, how can I locate the ***~/.ssh/*** folder? And after that, I just need to copy, without any subfolder?

---

### Post by Lars Noodén on 2014-10-04
The tilde is an abbreviation for your own home folder.  So ~/.ssh/ would be the same as /home/drew26/.ssh/, no further subfolder are needed.

---

### Post by drew26 on 2014-10-04
> **Lars Noodén said:**
> The tilde is an abbreviation for your own home folder.  So ~/.ssh/ would be the same as /home/drew26/.ssh/, no further subfolder are needed.

I did this: *drew26@mypc:~/Desktop$ mv id_rsa.ppk  ~/.ssh/  *and it worked, but as soon as I try to login I get the same error...

---

### Post by steeldriver on 2014-10-04
The .ppk format is specific to putty - if you want to use the keypair that you generated in puttygen from an openssh client, you will likely need to convert the .ppk file into OpenSSH format - either by importing it back into puttygen and re-exporting it (or possibly using ssh-keygen's import-export functionality)

---

### Post by drew26 on 2014-10-04
> **steeldriver said:**
> The .ppk format is specific to putty - if you want to use the keypair that you generated in puttygen from an openssh client, you will likely need to convert the .ppk file into OpenSSH format - either by importing it back into puttygen and re-exporting it (or possibly using ssh-keygen's import-export functionality)

Thank you for all the suggestions, but still it doesn't work, I did *puttygen mykey.ppk -O private-openssh -o the-new-keyfile *to convert the file, then I moved it the /.ssh/ folder, butI get the same error message.

---

### Post by tgalati4 on 2014-10-04
You might have to create new keys and start again:  [https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

I find it easier to delete the keys from both systems, regenerate them, copy the public key (using scp or some other secure method) to the remote system.  Delete any extraneous entries in ~/.ssh/known_hosts.  Of course, if you have many keys on different systems, you would not follow this advice, nor would you be asking this question.

---

### Post by drew26 on 2014-10-04
> **tgalati4 said:**
> You might have to create new keys and start again:  [https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

I find it easier to delete the keys from both systems, regenerate them, copy the public key (using scp or some other secure method) to the remote system.  Delete any extraneous entries in ~/.ssh/known_hosts.  Of course, if you have many keys on different systems, you would not follow this advice, nor would you be asking this question.

When I got my account on that remote system I had to generate the pair of keys, I just have the fear that, if I try to reset the keys, I might loose the access to the remote system, since I have no priviliges on it.

---

### Post by tgalati4 on 2014-10-04
Yes, this assumes you have access to the remote server (either an IT person who can do it for you or physical access to the server).  If you are currently locked out of the remote system, changing and sharing keys is non-trivial.

What you can do is remove all of the entries in your *known_hosts* (or copy them to another file) and force the creation of a new entry when you attempt to log into your remote server.  Just respond yes to the dialog asking for permission to add this host.

---

### Post by Lars Noodén on 2014-10-05
Or you can add the new keys while keeping the old ones, if you do decide to generate new keys.  I don't know the limit to the number of keys an account can have but it is high.  That would allow you to test the new keys while still having access via the old ones.  That's how I rotate keys myself.  Then once the new keys are verified to work, you can decide whether to remove the old ones.

---

