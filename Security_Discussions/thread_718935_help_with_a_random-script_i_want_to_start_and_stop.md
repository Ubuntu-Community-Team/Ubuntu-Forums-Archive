---
title: "help with a random-script i want to start and stop"
date: 2008-03-08
forum: Security Discussions
---

### Post by loko on 2008-03-08
hello,

this is security related.

i have a encrypted swap. but /dev/random does not deliver the needed information to create a key until the mouse is moved or touchpad is used.

in other words, the system is hang on start-up until a user-action is made.

so on the random-manpage i found a script which will carry the entrophie pool information across shut-down to start-up.

at this point i need some help.

where do i have to put these scripts that they are working in ubuntu?

here is the manpage-site:
[http://linux.die.net/man/4/random]("http://linux.die.net/man/4/random")

and this is the script:

 ```
add the following lines to an appropriate script which is run during the Linux system start-up sequence:
  
    echo "Initializing random number generator..."
    random_seed=/var/run/random-seed
    # Carry a random seed from start-up to start-up
    # Load and then save the whole entropy pool
    if [ -f $random_seed ]; then
        cat $random_seed >/dev/urandom
    else
        touch $random_seed
    fi
    chmod 600 $random_seed
    poolfile=/proc/sys/kernel/random/poolsize
    [ -r $poolfile ] && bytes='cat $poolfile' || bytes=512
    dd if=/dev/urandom of=$random_seed count=1 bs=$bytes

Also, add the following lines in an appropriate script which is run during the Linux system shutdown:

    # Carry a random seed from shut-down to start-up
    # Save the whole entropy pool
    echo "Saving random seed..."
    random_seed=/var/run/random-seed
    touch $random_seed
    chmod 600 $random_seed
    poolfile=/proc/sys/kernel/random/poolsize
    [ -r $poolfile ] && bytes='cat $poolfile' || bytes=512
    dd if=/dev/urandom of=$random_seed count=1 bs=$bytes
```


can somebody help me with this?

---

