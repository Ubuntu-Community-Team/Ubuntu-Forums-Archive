---
title: "Log in &quot;locally&quot; after joining Kerberos domain?"
date: 2010-07-07
forum: Server Platforms
---

### Post by Lucky. on 2010-07-07
I recently got a Kerberos domain working on my server by [following this guide](https://help.ubuntu.com/10.04/serverguide/C/kerberos.html), and I authenticate to the server upon login on my desktop computer (or any other client machines that are joined).

However one day my server went down, and bam!  I was unable to log in to my client computers because they couldn't contact the Kerberos server.

(Note:  This is straight Kerberos.  No NFSv4, no other services integrated with Kerberos - just Kerberos in a test environment).

In the Windows world, if your domain server(s) go down you can always log in to the a local machine user account rather than the domain account.

In this case I only have a single account on my client computer (no account on the server, just a principal)...but my local one still tries to authenticate against the Kerberos server upon login.  Is there a way to ditch this Kerberos authentication in a tough situation and simply log in without it?

---

