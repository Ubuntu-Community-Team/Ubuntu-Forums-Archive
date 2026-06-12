---
title: "Freeradius debug message not to be seen"
date: 2012-10-30
forum: Security
---

### Post by sthyagar on 2012-10-30
To debug freeradius, I use the command freeradius -X &

However, I do not see any debug messages appearing on the screen. Can someone help please?

Ubuntu 12.04 LTS

---

### Post by lykeion on 2012-10-30
maybe so:
```
radiusd -X &
```

Read documentation here: [http://freeradius.org/doc/](http://freeradius.org/doc/)

---

### Post by HermanAB on 2012-11-01
Howdy,

Try these:

Run the server in debug mode in one console, so you can watch the error messages, then connect to it from another console, using the radtest utility:

# radiusd -X
# radtest johndoe johndoepassword localhost 1812 yoursharedsecret

It should respond with "rad_recv: Access Accept packet...". If not, check the error messages in the other console.

There is also a more powerful, but more obscure utility called radclient. The syntax for this one is quite arcane and the man page is wrong in some respects. Here is an example that I figured out by trial and terror:

# echo "User-Name=johndoe,User-Password=johndoepassword"|radclient -x localhost
auth yoursharedsecret

That should do the same as radtest example. Radclient can also exercise the accounting features, by using the 'acct' command, but I could not figure out how to make it work. However, replacing 'auth' with 'acct' in the above command will prove that the accounting module is at least trying to do something.

Hope that helps!

H.

---

