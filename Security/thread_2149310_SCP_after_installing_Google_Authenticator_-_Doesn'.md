---
title: "SCP after installing Google Authenticator - Doesn't work!"
date: 2013-05-28
forum: Security
---

### Post by talz13 on 2013-05-28
I set up the Google Authenticator for 2 factor authentication on my server about a month ago.  It's working great for protecting my login, but it is also blocking my methods of remote file transfers.  I can no longer use SCP to copy files off of my server when using the password / 2 factor login (it MIGHT work with a public / private key, but I don't want to put that on my publicly accessible PC), either from the terminal or from Gnome's file manager net connection.

Is there any way I can keep using Google Authenticator, but get my SCP access back?  I think the SCP programs don't support the 2 factor authentication...

---

### Post by MadsRC on 2013-06-02
Which SCP programs doesn't work?  

Back when I used GA, I'm positive that WinSCP worked (Had to use Windows sometimes...) and can't recall having problems with the build in SCP program on Ubuntu.... However, something tells me that Filezilla doesn't workshop with GA...

---

### Post by talz13 on 2013-06-02
After my post, I did try WinSCP which worked ok (though I had to run it from my windows VM).  I'll have to check if the standard SCP command on centos can connect to my Ubuntu server with GA active...

---

### Post by talz13 on 2013-07-15
Looks like it works with FileZilla as well... but I think it re-prompts for authentication for each file transfer.  I'll see if it happens after this file transfer completes.

Edit: Yep, I started a second transfer while the first was still going, and it re-prompts for password / authentication code.  Oh well, it's better than CLI!

---

### Post by k3n on 2013-08-30
I prefer to scp on the command line most of the time. I had trouble getting it to work until I included my ssh key in the request like this: scp -i ~/id_rsa.pub user@server:filename .

---

### Post by talz13 on 2013-08-30
> **k3n said:**
> I prefer to scp on the command line most of the time. I had trouble getting it to work until I included my ssh key in the request like this: scp -i ~/id_rsa.pub user@server:filename .

I did eventually start using a public key auth with this connection, and it is working well... but it now bypasses the google authenticator (as I have it configured)

---

