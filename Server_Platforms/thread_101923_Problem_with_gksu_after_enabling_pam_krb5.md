---
title: "Problem with gksu after enabling pam_krb5"
date: 2005-12-10
forum: Server Platforms
---

### Post by Fault Bucket on 2005-12-10
Sorry for the cross-post, but I got no answers in the main 5.10 forum...

After setting up everything to use Kerberos auth, I now cannot launch apps through gksu. Everything else with krb5 works great - initial login, xscreensaver, forwarding TGTs to other kerberized hosts, etc.

I've straced gksu and it looks like it's trying to request credentials for 'root@MY.KERBEROS.DOMAIN'. The graphical password request box never appears on-screen.

I can still launch items like synaptic using normal sudo from a command line.

Any ideas?

-chris

---

