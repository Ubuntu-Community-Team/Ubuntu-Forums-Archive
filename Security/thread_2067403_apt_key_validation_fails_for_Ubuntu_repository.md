---
title: "apt key validation fails for Ubuntu repository"
date: 2012-10-06
forum: Security
---

### Post by nicolasdiogo on 2012-10-06
hello 

i am receiving this error

```

W: GPG error: http://gb.archive.ubuntu.com precise Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

```


and i wonder if this is something that is 'correct'

i wonder if the repo is not being has not being compromised.

i tried solving this by:

```

gpg --recv-keys 40976EAF437D05B5
gpg --export --armor 40976EAF437D05B5 | sudo apt-key add -

```

but it does not solve the problem - so are these packages signed by someone other then Ubuntu?

thanks,

---

### Post by rookcifer on 2012-10-06
Are you trying to download a specific package?  If so, which one?

---

### Post by nicolasdiogo on 2012-10-06
thanks

no a package in particular.

just running:

```

apt-get update

```

which refreshes the whole thing but at the end fails with the message mentioned earlier

---

### Post by oldos2er on 2012-10-06
[http://maketecheasier.com/solve-badsig-error-in-ubuntu/2012/01/13](http://maketecheasier.com/solve-badsig-error-in-ubuntu/2012/01/13)

---

### Post by nicolasdiogo on 2012-10-06
thanks

the following commands cleared this problem, as suggested:

```

sudo apt-get clean 
cd /var/lib/apt 
sudo mv lists lists.old 
sudo mkdir -p lists/partial 
sudo apt-get clean 
sudo apt-get update
```

but why does it arise in the first place - is there a theory?

thanks,

---

