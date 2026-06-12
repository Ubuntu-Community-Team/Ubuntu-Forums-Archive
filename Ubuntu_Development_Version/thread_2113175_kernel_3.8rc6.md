---
title: "kernel 3.8rc6"
date: 2013-02-06
forum: Ubuntu Development Version
---

### Post by rmarquez on 2013-02-06
How can I tell what options were compiled with the kernel?

Where can I get the source and some documentation on compiling it?

Basically I want to see if the SMB 2 protocol kernel support is turned on and if not compile a new kernel with it turned on.

Thanks!

---

### Post by pressureman on 2013-02-06
You can see the kernel config with:

```

less /boot/config-`uname -r`

```

And to answer your question about SMB2, it looks like it's been enabled:

```

...
CONFIG_CIFS_SMB2=y
...

```

---

### Post by rmarquez on 2013-02-06
> **pressureman said:**
> You can see the kernel config with:

```

less /boot/config-`uname -r`

```

And to answer your question about SMB2, it looks like it's been enabled:

```

...
CONFIG_CIFS_SMB2=y
...

```


Thank you pressureman!

Now my next question is how can I force a linux client to connect to a linux samba share to negotiate at SMB2?
I have tried with the smb.conf entry "max protocol = SMB2" and am using samba 4 along with the latest kernel = 3.8rc6.

If i connect to my share using windows 7, it negotiates at SMB2.1.

When i try to connect from a linux client, it says that option is not available. 
When I remove that statement from my smb.conf, I can connect with the linux client but only at SMB v. 1.


Thanks!

---

### Post by rrnbtter on 2013-02-09
Greetings,
RC7 Released today

---

### Post by pqwoerituytrueiwoq on 2013-02-09
> **rrnbtter said:**
> Greetings,
RC7 Released today
which version do you have in synaptic? i have 3.8.0.5.18 which according to [ubuntupackages](http://packages.ubuntu.com/raring/kernel/linux) is the latest
i installed it yesterday

---

### Post by rrnbtter on 2013-02-09
Greetings,
I am running the Mainline version 3.8 RC7. I don't use the repos version.  Since this thread is titled "Re: kernel 3.8rc6" I thought that this would be the proper place to let the RC users know that the RC7 update was present.  If discussing the RC versions isn't permissible I pretty sure that I will get a PM from the Admin. I' m sure there are other threads related to the repos versions.

---

