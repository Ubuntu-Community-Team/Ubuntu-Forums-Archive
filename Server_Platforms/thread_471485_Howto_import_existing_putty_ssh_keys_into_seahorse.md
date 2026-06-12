---
title: "Howto import existing putty ssh keys into seahorse?"
date: 2007-06-12
forum: Server Platforms
---

### Post by markymarknz on 2007-06-12
Hi everyone,

I have some servers setup and running fine and I access them remotely using ssh with public keys.
That is all working fine, however the keys I am using were generated using putty. When I try to import my existing private keys into seahorse it says they are of an "invalid file format". 
They are standard rsa 1024 bit keys.
Does anyone know how to import these keys as I thought it would be a straight forward thing to do but it obviously isn't.

Cheers

Mark

---

### Post by markymarknz on 2007-06-13
Bump :)
Anyone have any ideas ?

---

### Post by Roti on 2008-04-02
Hi!

 The import didn't worked for me either.
I had to copy my private key to .ssh/id_rsa and my public key to .ssh/id_rsa.pub, and it appeared in seahorse.


Roti

---

### Post by netlogic on 2008-04-02
Putty comes with software to convert it.  Check out puttygen. 

Load key and export.

---

### Post by randysparks on 2008-06-18
These kind of problems might be caused by incorrect clock settings on different computers. This can be a problem if you're using virtual machines. 

Ensure the time is set correctly on each computer. 

If the clock on the computer you're trying to import is set for a time before the key was generated, this means Seahorse will get confused and not import.

---

