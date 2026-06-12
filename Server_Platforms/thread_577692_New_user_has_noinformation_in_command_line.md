---
title: "New user has noinformation in command line"
date: 2007-10-16
forum: Server Platforms
---

### Post by RB@UNH on 2007-10-16
Please bear with me as I am new to Ubuntu and a novice with Linux in general.

I had a Red Hat Linux server running and two drives crashed in my array.  I decided to install a Server release of Ubuntu in its place and therefore I had to create the users again.  I had no problem adding a particular user but when she logs into the server via an SSH client (putty) she does not get her user or server information in the command line like this example.

user_name@servername:/path/in/prompt#

Instead she only gets the $ as the prompt.

How do I get this information into her command prompt.

Also, the vi editor that I used in the Red Hat distro worked different than the one that is in the Ubuntu release. When I am in edit mode and want to navigate with the arrow keys, I get unwanted text.  This didn't happen in the Red Hat version and the user mentioned previously will have trouble adjusting to it.  Is there a way to get the vi version that was  in my Red Hat distro?  Are they different or is there a way to "customize" vi so it behaved my prefered way?

Thanks for any assistance!

---

### Post by cdenley on 2007-10-16
I think this should do it. If you want to change the configuration for other users, adjust destination and permissions as necessary.
```

cp /etc/skel/.bashrc ~

```

---

### Post by codmate on 2007-10-17
Maybe the user has been given an obscure shell?

Try:
```
sudo chsh -s /bin/bash username
```
...which will make sure the user's shell is bash.

---

