---
title: "fetchmail AHHHH!!!!!"
date: 2008-08-12
forum: Server Platforms
---

### Post by FiniteRed on 2008-08-12
Hi everyone

This problem is driving me nuts as it seems so simple, but I cant fix it!

I have a mail server running, this mail server uses fetchmail to pick up e-mails running from my ISP, I cannot get fetchmail to run on start-up with the following options:

fetchmail –d 60

I have written a script, placed it in the init.d directory, set it to executable with chmod and run rc-update - but still it does not work! :cry:

Every time the server restarts I have to log in and manually type this command in, can someone please tell me how to get fetchmail to do this upon start-up?

Thank you so much :)

FR

---

### Post by dperfors on 2008-08-12
can you run that script by hand? (/etc/init.d/<scriptname>)

how does the script looks like?

---

### Post by FiniteRed on 2008-08-13
Yes indeed I can run it manually and it works, the script looks like this:

```
fetchmail -d 60
```

That's it, am I missing something / everything? 

FR

---

### Post by moonpup on 2008-08-13
You may have the script in the /etc/init.d, but is the script actually linked to the runlevel you boot into?

---

### Post by windependence on 2008-08-13
You can use update-rc.d for start-only or stop-only scripts

    Start my script on startup :
    ```
# update-rc.d -f my_script start 99 2 3 4 5 .
```

    where
    - start is the argument given to the script (start, stop).
    - 99 is the start order of the script (1 = first one, 99= last one)
    - 2 3 4 5 are the runlevels to start

    Dont forget the dot at the end
    More info in /etc/rcS.d/README

    Start my_script on shutdown and reboot :
    ```
# update-rc.d -f my_script start 90 0 6 .
```

    Stop my_script on halt and reboot :
    ```
# update-rc.d -f my_script reboot 90 0 6 .
```

    If you want to make your own demon, you can use the skeleton file provided at
    /etc/init.d/skeleton

    about runlevels :

    To know which runlevel you are running, simply type
    ```
$ runlevel
```

    more info about runlevels here : [http://oldfield.wattle.id.au/luv/boot.html#init](http://oldfield.wattle.id.au/luv/boot.html#init)

    happy scripting

---

### Post by HermanAB on 2008-08-13
Try using the full path to the executable.

Cheers,

Herman

---

