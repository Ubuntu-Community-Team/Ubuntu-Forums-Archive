---
title: "SCP over SSH using keys instead of password - cannot get it to work"
date: 2017-10-19
forum: Server Platforms
---

### Post by Icarusbop on 2017-10-19
I have an Ubuntu 16.04 server with SSH, I have configured a keypair so I can SSH on to a remote system with no password, this works fine.

I am trying to SCP from Local (system1) to ther remote (system2), the SCP works fine but asks for a password. I want to use the keypair for non-autheticated copying.

I have followed numerous guides from the web on how to do this, but it basically seems to boils down to the following:

```
scp -i <path the PRIVATE key file>  filetocopy  user@remote.co.uk:~destinationfile
```
Everything I can find on the internet says this should work - but it keeps asking for the password for the remote (2nd) system, even though I know the keypair works OK because I can use it for SSH.

Annoyingly - the same command as above will work perfectly with no password request if run as root - either by way of 'sudo' or from an elevated terminal...

so:
```

sudo scp -i <path the PRIVATE key file>  filetocopy  user@remote.co.uk:~destinationfile
```
Works fine, but:
```
scp -i <path the PRIVATE key file>  filetocopy  user@remote.co.uk:~destinationfile
```
does not. (i.e. it still asks for a password - if I put it in the copy works fine)

There are no files in the roots' .ssh folder except for the known_hosts files (i.e. no key files)
Can anyone help with this please?
IcarusBop

---

### Post by howefield on 2017-10-19
Thread moved to the "*Server Platforms*" forum.

---

### Post by darkod on 2017-10-19
You do have permissions to copy the file you want to copy using the standard user, right?

If you try to copy it locally, with cp instead of scp, can you?

---

### Post by Icarusbop on 2017-10-19
Hello:

I got this sorted - I removed all my keys and keyfiles from both systems and worked through the process of setting up new keyfiles and using ssh-copy-id to copy the files over.
It now works great.

There must have been some obscure corruption in the authorizes_keys file maybe messing it up.
Thanks again.

---

### Post by darkod on 2017-10-19
OK, great. Please mark the thread as solved, you can do that in Thread Tools above the first post.

---

