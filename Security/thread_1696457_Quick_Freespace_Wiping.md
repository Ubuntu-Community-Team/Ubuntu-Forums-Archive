---
title: "Quick Freespace Wiping?"
date: 2011-02-27
forum: Security
---

### Post by theyain on 2011-02-27
Is there any way to securely wipe the freespace on a drive with random ones and zeros?

I was thinking of using something like
```

sudo -i
//Bash script
for i in 1 2 3 4 5 6 7 8 9
do
    cat /dev/urandom > /tmp/wipe.conf
    rm /tmp/wipe.conf
done

```

But I'm not sure if this is as quick as possible or not. 

I'd rather use urandom then zero because I personally think using random 1's and 0's far more secure then just using zeros.

Any suggestions?

---

### Post by rookcifer on 2011-02-28
Using zeros will be much faster than /dev/urandom.  Do this:

```
dd if=/dev/zero of=/tmp/wipe.conf
```

Both zeros and random data will be as "secure" as the other.  The only reason to use random data is if you plan on encrypting the drive.

---

### Post by emiller12345 on 2011-02-28
Take a look at this package, its in the universe repo.

```
sudo apt-get install secure-delete
```

---

